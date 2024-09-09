<!-- loioeac5771068bb4c25afc9ae63cd2b5ef8 -->

# Integrate with SAP Cloud Logging

Learn how to configure the Telemetry module to ingest application and access logs as well as distributed trace data and metrics in instances of SAP Cloud Logging.



<a name="loioeac5771068bb4c25afc9ae63cd2b5ef8__prereq_esy_hvv_xbc"/>

## Prerequisites

-   Kyma as the target deployment environment.

-   The Telemetry module is added. For details, see [Add and Delete a Kyma Module](../50-administration-and-ops/add-and-delete-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).

-   If you want to use Istio access logs, make sure that the Istio module is added.

-   An instance of [SAP Cloud Logging](https://help.sap.com/docs/cloud-logging?locale=en-US&version=Cloud) with OpenTelemetry enabled to ingest distributed traces.

    > ### Tip:  
    > Create the instance with the SAP BTP service operator \(see [Create an SAP Cloud Logging Instance through SAP BTP Service Operator](https://help.sap.com/docs/cloud-logging/cloud-logging/create-sap-cloud-logging-instance-through-sap-btp-service-operator?locale=en-US&version=Cloud)\), because it takes care of creation and rotation of the required Secret. However, you can choose any other method of creating the instance and the Secret, as long as the parameter for OTLP ingestion is enabled in the instance. For details, see [Configuration Parameters](https://help.sap.com/docs/cloud-logging/cloud-logging/configuration-parameters?locale=en-US&version=Cloud).

-   A Secret in the respective namespace in the Kyma cluster, holding the credentials and endpoints for the instance. In the following example, the Secret is named “sap-cloud-logging” and the namespace “sap-cloud-logging-integration”, as illustrated in the [secret-example.yaml](https://github.com/kyma-project/telemetry-manager/blob/main/docs/user/integration/sap-cloud-logging/secret-example.yaml).

-   Kubernetes CLI \(kubectl\) \(see [Install the Kubernetes Command Line Tool](https://developers.sap.com/tutorials/cp-kyma-download-cli.html)\).

-   UNIX shell or Windows Subsystem for Linux \(WSL\) to execute commands.




## Context

The Telemetry module supports shipping logs and ingesting distributed traces as well as metrics from applications and the Istio service mesh to SAP Cloud Logging. Furthermore, you can set up Kyma dashboard integration and use SAP Cloud Logging alerts and dashboards.

SAP Cloud Logging is an instance-based and environment-agnostic observability service to store, visualize, and analyze logs, metrics, and traces.

![](images/Kyma_SAP_Cloud_Logging_Integration_c99a164.svg)

<a name="task_th5_cxv_xbc"/>

<!-- task\_th5\_cxv\_xbc -->

## Ship Logs to SAP Cloud Logging

You can set up shipment of applications and access logs to SAP Cloud Logging. The following instructions distinguish application logs and access logs, which can be configured independently.



<a name="task_th5_cxv_xbc__steps_drj_4xv_xbc"/>

## Procedure

**Set Up Application Logs**

1.  Deploy the `LogPipeline` for application logs with the following script:

    ```
    kubectl apply -n sap-cloud-logging-integration -f - <<EOF
    apiVersion: telemetry.kyma-project.io/v1alpha1
    kind: LogPipeline
    metadata:
      name: sap-cloud-logging-application-logs
    spec:
      input:
        application:
          containers:
            exclude:
              - istio-proxy
      output:
        http:
          dedot: true
          host:
            valueFrom:
              secretKeyRef:
                name: sap-cloud-logging
                namespace: sap-cloud-logging-integration
                key: ingest-mtls-endpoint
          tls:
            cert:
              valueFrom:
                secretKeyRef:
                  name: sap-cloud-logging
                  namespace: sap-cloud-logging-integration
                  key: ingest-mtls-cert
            key:
              valueFrom:
                secretKeyRef:
                  name: sap-cloud-logging
                  namespace: sap-cloud-logging-integration
                  key: ingest-mtls-key
          uri: /customindex/kyma
    EOF
    ```

2.  Wait for the `LogPipeline` to be in the *Running* state. To check the state, run: `kubectl get logpipelines`.


**Set Up Access Logs**

By default, Istio sidecar injection and Istio access logs are disabled in Kyma. To analyze access logs of your workload in the default SAP Cloud Logging dashboards shipped for SAP BTP, Kyma runtime, you must enable them:

3.  Enable Istio sidecar injection for your workload. See [Enabling Istio Sidecar Injection](https://kyma-project.io/#/istio/user/operation-guides/02-20-enable-sidecar-injection).

4.  Enable Istio access logs for your workload. See [Enable Istio Access Logs](https://kyma-project.io/#/istio/user/operation-guides/02-30-enable-istio-access-logs).

5.  Deploy the `LogPipeline` for Istio access logs and enable access logs in Kyma with the following script:

    ```
    kubectl apply -n sap-cloud-logging-integration -f - <<EOF
    apiVersion: telemetry.kyma-project.io/v1alpha1
    kind: LogPipeline
    metadata:
      name: sap-cloud-logging-access-logs
    spec:
      input:
        application:
          containers:
            include:
              - istio-proxy
      output:
        http:
          dedot: true
          host:
            valueFrom:
              secretKeyRef:
                name: sap-cloud-logging
                namespace: sap-cloud-logging-integration
                key: ingest-mtls-endpoint
          tls:
            cert:
              valueFrom:
                secretKeyRef:
                  name: sap-cloud-logging
                  namespace: sap-cloud-logging-integration
                  key: ingest-mtls-cert
            key:
              valueFrom:
                secretKeyRef:
                  name: sap-cloud-logging
                  namespace: sap-cloud-logging-integration
                  key: ingest-mtls-key
          uri: /customindex/istio-envoy-kyma
    EOF
    ```

6.  Wait for the `LogPipeline` to be in the *Running* state. To check the state, run: `kubectl get logpipelines`.


<a name="task_ejt_bzv_xbc"/>

<!-- task\_ejt\_bzv\_xbc -->

## Ship Distributed Traces to SAP Cloud Logging

You can set up ingestion of distributed traces from applications and the Istio service mesh to the OTLP endpoint of the SAP Cloud Logging service instance.



<a name="task_ejt_bzv_xbc__steps_x1d_szv_xbc"/>

## Procedure

1.  Deploy the Istio Telemetry resource with the following script:

    ```
     kubectl apply -n istio-system -f - <<EOF
     apiVersion: telemetry.istio.io/v1alpha1
     kind: Telemetry
     metadata:
       name: tracing-default
     spec:
       tracing:
       - providers:
         - name: "kyma-traces"
         randomSamplingPercentage: 1.0
     EOF
    ```

    The default configuration has the `randomSamplingPercentage` property set to *1.0*, meaning it samples 1% of all requests. To change the sampling rate, adjust the property to the desired value, up to 100 percent.

2.  Deploy the `TracePipeline` with the following script:

    ```
     kubectl apply -n sap-cloud-logging-integration -f - <<EOF
     apiVersion: telemetry.kyma-project.io/v1alpha1
     kind: TracePipeline
     metadata:
       name: sap-cloud-logging
     spec:
       output:
         otlp:
           endpoint:
             valueFrom:
               secretKeyRef:
                 name: sap-cloud-logging
                 namespace: sap-cloud-logging-integration
                 key: ingest-otlp-endpoint
           tls:
             cert:
               valueFrom:
                 secretKeyRef:
                   name: sap-cloud-logging
                   namespace: sap-cloud-logging-integration
                   key: ingest-otlp-cert
             key:
               valueFrom:
                 secretKeyRef:
                   name: sap-cloud-logging
                   namespace: sap-cloud-logging-integration
                   key: ingest-otlp-key
     EOF
    ```

3.  Wait for the `TracePipeline` to be in the *Running* state. To check the state, run: `kubectl get tracepipelines`.


<a name="task_swp_g1w_xbc"/>

<!-- task\_swp\_g1w\_xbc -->

## Ship Metrics to SAP Cloud Logging

You can set up ingestion of metrics from applications and the Istio service mesh to the OTLP endpoint of the SAP Cloud Logging service instance.



<a name="task_swp_g1w_xbc__steps_ylh_m1w_xbc"/>

## Procedure

1.  Deploy the `MetricPipeline` with the following script:

    ```
     kubectl apply -n sap-cloud-logging-integration -f - <<EOF
     apiVersion: telemetry.kyma-project.io/v1alpha1
     kind: MetricPipeline
     metadata:
       name: sap-cloud-logging
     spec:
       input:
         prometheus:
           enabled: false
         istio:
           enabled: false
         runtime:
           enabled: false
       output:
         otlp:
           endpoint:
             valueFrom:
               secretKeyRef:
                 name: sap-cloud-logging
                 namespace: sap-cloud-logging-integration
                 key: ingest-otlp-endpoint
           tls:
             cert:
               valueFrom:
                 secretKeyRef:
                   name: sap-cloud-logging
                   namespace: sap-cloud-logging-integration
                   key: ingest-otlp-cert
             key:
               valueFrom:
                 secretKeyRef:
                   name: sap-cloud-logging
                   namespace: sap-cloud-logging-integration
                   key: ingest-otlp-key
     EOF
    ```

    By default, the `MetricPipeline` assures that a gateway is running in the cluster to push OTLP metrics.

2.  If you want to use additional metric collection, configure the presets under `input`.

    For the available options, see [Metrics](metrics-44ac6c5.md).

3.  Wait for the `MetricPipeline` to be in the *Running* state. To check the state, run: `kubectl get metricpipelines`.


<a name="task_pny_z1w_xbc"/>

<!-- task\_pny\_z1w\_xbc -->

## Set Up Kyma Dashboard Integration

For easier access from the Kyma dashboard, adjust the navigation under *Observability*, and add deep links to the *Pod*, *Deployment*, and *Namespace* views.



<a name="task_pny_z1w_xbc__steps_jw2_hbw_xbc"/>

## Procedure

1.  Read the SAP Cloud Logging dashboard URL from the Secret:

    ```
    export DASHBOARD_URL=$(kubectl -n sap-cloud-logging-integration get secret sap-cloud-logging --template='{{index .data "dashboards-endpoint" | base64decode}}')
    ```

2.  Download the following ConfigMaps containing the sample configuration:

    ```
    curl -o configmap-navigation.yaml https://raw.githubusercontent.com/kyma-project/telemetry-manager/main/docs/user/integration/sap-cloud-logging/configmap-navigation.yaml
    curl -o configmap-deeplinks.yaml https://raw.githubusercontent.com/kyma-project/telemetry-manager/main/docs/user/integration/sap-cloud-logging/configmap-deeplinks.yaml
    ```

3.  Replace placeholders in the ConfigMaps with the URL:

    ```
    sed -e "s/{PLACEHOLDER}/$DASHBOARD_URL/" configmap-navigation.yaml
    sed -e "s/{PLACEHOLDER}/$DASHBOARD_URL/" configmap-deeplinks.yaml
    ```

4.  Apply the ConfigMaps:

    ```
    kubectl apply -f configmap-navigation.yaml
    kubectl apply -f configmap-deeplinks.yaml
    ```


<a name="task_c2k_rbw_xbc"/>

<!-- task\_c2k\_rbw\_xbc -->

## Use SAP Cloud Logging Alerts

Learn how to define and import recommended alerts for SAP Cloud Logging. The following alerts are based on JSON documents defining a `Monitor` for the alerting plugin.



<a name="task_c2k_rbw_xbc__steps_wfs_1cw_xbc"/>

## Procedure

1.  Define a `destination`, which will be used by all your alerts.

2.  To import a monitor, use the development tools of the SAP Cloud Logging dashboard.

3.  Execute `POST _plugins/_alerting/monitors`, followed by the contents of the respective JSON file.

4.  Depending on the pipelines you are using, enable some or all of the following alerts:

    **Recommended Alerts**


    <table>
    <tr>
    <th valign="top">

    Category
    
    </th>
    <th valign="top">

    File
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    SAP Cloud Logging
    
    </td>
    <td valign="top">
    
    [OpenSearch cluster health](https://raw.githubusercontent.com/kyma-project/telemetry-manager/main/docs/user/integration/sap-cloud-logging/alert-health.json)
    
    </td>
    <td valign="top">
    
    The OpenSearch cluster might become unhealthy, which is indicated by a **red** status using the [cluster health API](https://opensearch.org/docs/1.3/api-reference/cluster-api/cluster-health).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Kyma Telemetry Integration
    
    </td>
    <td valign="top">
    
    [Application log ingestion](https://raw.githubusercontent.com/kyma-project/telemetry-manager/main/docs/user/integration/sap-cloud-logging/alert-app-log-ingestion.json)
    
    </td>
    <td valign="top">
    
    The `LogPipeline` for shipping application logs might lose connectivity to SAP Cloud Logging, with the effect that no application logs are ingested anymore.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Kyma Telemetry Integration
    
    </td>
    <td valign="top">
    
    [Access log ingestion](https://raw.githubusercontent.com/kyma-project/telemetry-manager/main/docs/user/integration/sap-cloud-logging/alert-access-log-ingestion.json)
    
    </td>
    <td valign="top">
    
    The `LogPipeline` for shipping access logs might lose connectivity to SAP Cloud Logging, with the effect that no access logs are ingested anymore.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Kyma Telemetry Integration
    
    </td>
    <td valign="top">
    
    [Trace ingestion](https://raw.githubusercontent.com/kyma-project/telemetry-manager/main/docs/user/integration/sap-cloud-logging/alert-trace-ingestion.json)
    
    </td>
    <td valign="top">
    
    The `TracePipeline` for shipping traces might lose connectivity to SAP Cloud Logging, with the effect that no traces are ingested anymore.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Kyma Telemetry Integration
    
    </td>
    <td valign="top">
    
    [Metric ingestion](https://raw.githubusercontent.com/kyma-project/telemetry-manager/main/docs/user/integration/sap-cloud-logging/alert-metric-ingestion.json)
    
    </td>
    <td valign="top">
    
    The `MetricPipeline` for shipping metrics might lose connectivity to SAP Cloud Logging, with the effect that no metrics are ingested anymore.
    
    </td>
    </tr>
    </table>
    
5.  Edit notification action: Add the `destination` and adjust the intervals and thresholds to your needs.

6.  Verify that the new monitor definition is listed among the SAP Cloud Logging alerts.


<a name="task_uw4_r2w_xbc"/>

<!-- task\_uw4\_r2w\_xbc -->

## Use SAP Cloud Logging Dashboards

You can view logs, traces, and metrics in SAP Cloud Logging dashboards:



<a name="task_uw4_r2w_xbc__steps-unordered_t2w_ffw_xbc"/>

## Procedure

-   To view the traffic and application logs, use the SAP Cloud Logging dashboards prefixed with `Kyma_`, which are based on both kinds of log ingestion: application and access logs.

-   To view distributed traces, use the OpenSearch plugin *Observability*.

-   To view the container- and Pod-related metrics collected by the `MetricPipeline` `runtime` input, use the dashboard *\[OTel\] K8s Container Metrics*.

-   To use the dashboard for Istio metrics of Pods that have an active Istio sidecar injection \(collected by the `MetricPipeline` `istio` input\), manually import the file [Kyma Istio Service Metrics](https://raw.githubusercontent.com/kyma-project/telemetry-manager/main/docs/user/integration/sap-cloud-logging/dashboard-istio.ndjson).


