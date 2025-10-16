<!-- loioeac5771068bb4c25afc9ae63cd2b5ef8 -->

# Integrate with SAP Cloud Logging

Learn how to configure the Telemetry module to ingest application and access logs as well as distributed trace data and metrics in instances of SAP Cloud Logging.



<a name="loioeac5771068bb4c25afc9ae63cd2b5ef8__prereq_esy_hvv_xbc"/>

## Prerequisites

-   Kyma as the target deployment environment.

-   Make sure the following Kyma modules are added. For details, see [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c)

    -   Telemetry module

    -   SAP BTP Operator module \(default module\)

    -   If you want to collect Istio access logs: Istio module \(default module\)


-   An instance of [SAP Cloud Logging](https://help.sap.com/docs/cloud-logging?locale=en-US&version=Cloud) with OpenTelemetry enabled to ingest distributed traces. For details, see [Ingest via OpenTelemetry API Endpoint](https://help.sap.com/docs/SAP_CLOUD_LOGGING/d82d23dc499c44079e1e779c1d3a5191/fdc78af7c69246bc87315d90a061b321.html?locale=en-US).

    > ### Tip:  
    > Create the instance with the SAP BTP service operator \(see [Create an SAP Cloud Logging Instance through SAP BTP Service Operator](https://help.sap.com/docs/cloud-logging/cloud-logging/create-sap-cloud-logging-instance-through-sap-btp-service-operator?locale=en-US&version=Cloud)\), because it takes care of creation and rotation of the required Secret. However, you can choose any other method of creating the instance and the Secret, as long as the parameter for OTLP ingestion is enabled in the instance. For details, see [Configuration Parameters](https://help.sap.com/docs/cloud-logging/cloud-logging/configuration-parameters?locale=en-US&version=Cloud).

-   A Secret in the respective namespace in the Kyma cluster, holding the credentials and endpoints for the instance. It’s recommended that you rotate your Secret \(see [SAP BTP Security Recommendation BTP-CLS-0003](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-index=BTP-CLS-0003&version=Cloud)\).

    In the following example, the Secret is named “sap-cloud-logging” and the namespace “sap-cloud-logging-integration”, as illustrated in the [secret-example.yaml](https://github.com/kyma-project/telemetry-manager/blob/main/docs/user/integration/sap-cloud-logging/secret-example.yaml).

-   Kubernetes CLI \(kubectl\) \(see [Install the Kubernetes Command Line Tool](https://developers.sap.com/tutorials/cp-kyma-download-cli.html)\).

-   UNIX shell or Windows Subsystem for Linux \(WSL\) to execute commands.




## Context

The Telemetry module supports shipping logs and ingesting distributed traces as well as metrics from applications and the Istio service mesh to SAP Cloud Logging. Furthermore, you can set up Kyma dashboard integration and use SAP Cloud Logging alerts and dashboards.

SAP Cloud Logging is an instance-based and environment-agnostic observability service to store, visualize, and analyze logs, metrics, and traces.

![](images/Kyma_SAP_Cloud_Logging_Integration_c99a164.svg)

<a name="task_ship_logs_to_CLS"/>

<!-- task\_ship\_logs\_to\_CLS -->

## Ship Logs to SAP Cloud Logging

You can set up shipment of applications and access logs to SAP Cloud Logging. The following instructions distinguish application logs and access logs, which can be configured independently.



<a name="task_ship_logs_to_CLS__steps_drj_4xv_xbc"/>

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

3.  Enable Istio sidecar injection for your workload. See [Enabling Istio Sidecar Proxy Injection](enabling-istio-sidecar-proxy-injection-b3c6f1d.md).

4.  Enable Istio access logs for your workload. See [Configuring Istio Access Logs](configuring-istio-access-logs-d3f20b6.md).

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


<a name="task_ship_traces_to_CLS"/>

<!-- task\_ship\_traces\_to\_CLS -->

## Ship Distributed Traces to SAP Cloud Logging

You can set up ingestion of distributed traces from applications and the Istio service mesh to the OTLP endpoint of the SAP Cloud Logging service instance.



<a name="task_ship_traces_to_CLS__steps_x1d_szv_xbc"/>

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


<a name="task_ship_metrics_to_CLS"/>

<!-- task\_ship\_metrics\_to\_CLS -->

## Ship Metrics to SAP Cloud Logging

You can set up ingestion of metrics from applications and the Istio service mesh to the OTLP endpoint of the SAP Cloud Logging service instance.



<a name="task_ship_metrics_to_CLS__steps_ylh_m1w_xbc"/>

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


<a name="task_set_up_kyma_dashboard_integration"/>

<!-- task\_set\_up\_kyma\_dashboard\_integration -->

## Set Up Kyma Dashboard Integration

For easier access from the Kyma dashboard, add links to the navigation under *SAP Cloud Logging*, and add deep links to the *Pod*, *Deployment*, and *Namespace* views.



<a name="task_set_up_kyma_dashboard_integration__context_a1p_htz_3gc"/>

## Context

Depending on the output you use in your `LogPipeline`, apply the `ConfigMap`. If your Secret has a different name or namespace, then download the file first and adjust the namespace and name accordingly in the `dataSources` section of the file.



<a name="task_set_up_kyma_dashboard_integration__steps_jw2_hbw_xbc"/>

## Procedure

-   For OTLP, run:

    ```
    kubectl apply -f https://raw.githubusercontent.com/kyma-project/telemetry-manager/main/docs/user/integration/sap-cloud-logging/kyma-dashboard-configmap.yaml
    
    ```

-   For HTTP, run:

    ```
    kubectl apply -f https://raw.githubusercontent.com/kyma-project/telemetry-manager/main/docs/user/integration/sap-cloud-logging/kyma-dashboard-http-configmap.yaml
    
    ```


<a name="task_use_CLS_alerts"/>

<!-- task\_use\_CLS\_alerts -->

## Use SAP Cloud Logging Alerts

Learn how to define and import recommended alerts for SAP Cloud Logging. The following alerts are based on JSON documents defining a `Monitor` for the alerting plugin.



<a name="task_use_CLS_alerts__steps_wfs_1cw_xbc"/>

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
    <tr>
    <td valign="top">
    
    Kyma Telemetry Integration
    
    </td>
    <td valign="top">
    
    [Kyma Telemetry Status](https://raw.githubusercontent.com/kyma-project/telemetry-manager/main/docs/user/integration/sap-cloud-logging/alert-telemetry-status.json)
    
    </td>
    <td valign="top">
    
    The Telemetry module might report a non-ready state indicating a configuration or data flow problem.
    
    </td>
    </tr>
    </table>
    
5.  Edit notification action: Add the `destination` and adjust the intervals and thresholds to your needs.

6.  Verify that the new monitor definition is listed among the SAP Cloud Logging alerts.


<a name="task_use_CLS_dashboards"/>

<!-- task\_use\_CLS\_dashboards -->

## Use SAP Cloud Logging Dashboards

You can view logs, traces, and metrics in SAP Cloud Logging dashboards:



<a name="task_use_CLS_dashboards__steps-unordered_t2w_ffw_xbc"/>

## Procedure

-   To view the traffic and application logs, use the SAP Cloud Logging dashboards prefixed with `Kyma_`, which are based on both kinds of log ingestion: application and access logs.

-   To view distributed traces, use the OpenSearch plugin *Observability*.

-   To view the container- and Pod-related metrics collected by the `MetricPipeline` `runtime` input, use the dashboard *\[OTel\] K8s Container Metrics*.

-   To view the Kubernetes Node-related metrics collected by the `MetricPipeline` `runtime` input, manually import the file [K8s Nodes](https://raw.githubusercontent.com/kyma-project/telemetry-manager/main/docs/user/integration/sap-cloud-logging/dashboard-nodes.ndjson).

-   To view the Kubernetes Volume-related metrics collected by the `MetricPipeline` `runtime` input, manually import the file [K8s Volumes](https://raw.githubusercontent.com/kyma-project/telemetry-manager/main/docs/user/integration/sap-cloud-logging/dashboard-volumes.ndjson).

-   To view the Kubernetes Workload-related metrics collected by the `MetricPipeline` `runtime` input, manually import the file [K8s Workloads](https://raw.githubusercontent.com/kyma-project/telemetry-manager/main/docs/user/integration/sap-cloud-logging/dashboard-volumes.ndjson).

-   To view the status of the SAP Cloud Logging integration with the Kyma Telemetry module, manually import the file [Kyma Telemetry Status](https://raw.githubusercontent.com/kyma-project/telemetry-manager/main/docs/user/integration/sap-cloud-logging/dashboard-status.ndjson).

-   To use the dashboard for Istio metrics of Pods that have an active Istio sidecar injection \(collected by the `MetricPipeline` `istio` input\), manually import the file [Kyma Istio Service Metrics](https://raw.githubusercontent.com/kyma-project/telemetry-manager/main/docs/user/integration/sap-cloud-logging/dashboard-istio.ndjson).


