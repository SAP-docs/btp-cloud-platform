<!-- loio44ac6c5afef0464480fa18acb7483972 -->

# Metrics

The goal of the Telemetry module is to support you in collecting all relevant metrics of a workload in a Kyma cluster and ship them to a backend for further analysis. Kyma modules like [Istio Module](istio-module-26ffe00.md) or [Serverless](https://kyma-project.io/#/serverless-manager/user/README) contribute metrics instantly, and the Telemetry module enriches the data. You can choose among multiple [vendors for OTLP-based backends](https://opentelemetry.io/ecosystem/vendors/).



<a name="loio44ac6c5afef0464480fa18acb7483972__section_jv4_qlp_1bc"/>

## Overview

Observability is all about exposing the internals of the components belonging to a distributed application and making that data analysable at a central place. While application logs and traces usually provide request-oriented data, metrics are aggregated statistics exposed by a component to reflect the internal state. Typical statistics like the amount of processed requests, or the amount of registered users, can be very useful to monitor the current state and also the health of a component. Also, you can define proactive and reactive alerts if metrics are about to reach thresholds, or if they already passed thresholds.

The Telemetry module provides a metric gateway and, optionally, an agent for the collection and shipment of metrics of any container running in the Kyma runtime.

You can configure the metric gateway with external systems using runtime configuration with a dedicated Kubernetes API \([CRD](https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/#customresourcedefinitions)\) named `MetricPipeline`. The Metric feature is optional. If you don't want to use it, simply don't set up a `MetricPipeline`.



<a name="loio44ac6c5afef0464480fa18acb7483972__section_kyma_metrics_prerequisites"/>

## Prerequisites

-   Before you can collect metrics data from a component, it must expose \(or instrument\) the metrics. Typically, it instruments specific metrics for the used language runtime \(like Node.js\) and custom metrics specific to the business logic. Also, the exposure can be in different formats, like the pull-based Prometheus format or the [push-based OTLP format](https://opentelemetry.io/docs/specs/otlp/).

-   If you want to use Prometheus-based metrics, you must have instrumented your application using a library like the [Prometheus client library](https://prometheus.io/docs/instrumenting/clientlibs/), with a port in your workload exposed serving as a Prometheus metrics endpoint.

-   For the instrumentation, you typically use an SDK, namely the [Prometheus client libraries](https://prometheus.io/docs/instrumenting/clientlibs/) or the [Open Telemetry SDKs](https://opentelemetry.io/docs/languages/). Both libraries provide extensions to activate language-specific auto-instrumentation like for Node.js, and an API to implement custom instrumentation.




<a name="loio44ac6c5afef0464480fa18acb7483972__section_kyma_metrics_architecture"/>

## Architecture

In the Telemetry module, a central in-cluster Deployment of an [OTel Collector](https://opentelemetry.io/docs/collector/) acts as a gateway. The gateway exposes endpoints for the [OpenTelemetry Protocol \(OTLP\)](https://opentelemetry.io/docs/specs/otlp/) for GRPC and HTTP-based communication using the dedicated `telemetry-otlp-metrics` service, to which all Kyma modules and users’ applications send the metrics data.

Optionally, the Telemetry module provides a DaemonSet of an OTel Collector acting as an agent. This agent can pull metrics of a workload and the Istio sidecar in the [Prometheus pull-based format](https://prometheus.io/docs/instrumenting/exposition_formats/) and can provide runtime-specific metrics for the workload.

![](images/Metrics_Architecture_99c13a2.svg)

1.  An application \(exposing metrics in OTLP\) sends metrics to the central metric gateway service.

2.  An application \(exposing metrics in Prometheus protocol\) activates the agent to scrape the metrics with an annotation-based configuration.

3.  Additionally, you can activate the agent to pull metrics of each Istio sidecar.

4.  The agent supports collecting metrics from the Kubelet and Kubernetes APIServer.

5.  The agent converts and sends all collected metric data to the gateway in OTLP.

6.  The gateway discovers the metadata and enriches all received data with typical metadata of the source by communicating with the Kubernetes APIServer. Furthermore, it filters data according to the pipeline configuration.

7.  Telemetry Manager configures the agent and gateway according to the `MetricPipeline` resource specification, including the target backend for the metric gateway. Also, it observes the metrics flow to the backend and reports problems in the `MetricPipeline` status.

8.  The metric gateway sends the data to the observability system that’s specified in your `MetricPipeline` resource - either within the Kyma cluster, or, if authentication is set up, to an external observability backend.

9.  You can analyze the metric data with your preferred backend system.




### Telemetry Manager

The `MetricPipeline` resource is watched by Telemetry Manager, which is responsible for generating the custom parts of the OTel Collector configuration.

![](images/Metrics_Resources_aa58947.svg)

1.  Telemetry Manager watches all `MetricPipeline` resources and related Secrets.

2.  Furthermore, Telemetry Manager takes care of the full lifecycle of the gateway Deployment and the agent DaemonSet. Only if you defined a `MetricPipeline`, the gateway and agent are deployed.

3.  Whenever the user configuration changes, Telemetry Manager validates it and generates a single configuration for the gateway and agent.

4.  Referenced Secrets are copied into one Secret that is mounted to the gateway as well.




### Metric Gateway

In a Kyma cluster, the metric gateway is the central component to which all components can send their individual metrics. The gateway collects, enriches, and dispatches the data to the configured backend. For more information, see [Telemetry Gateways](telemetry-gateways-61567b7.md).



### Metric Agent

If a `MetricPipeline` configures a feature in the `input` section, an additional DaemonSet is deployed acting as an agent. The agent is also based on an [OTel Collector](https://opentelemetry.io/docs/collector/) and encompasses the collection and conversion of Prometheus-based metrics. Hereby, the workload puts a `prometheus.io/scrape` annotation on the specification of the Pod or service, and the agent collects it. The agent sends all data in OTLP to the central gateway.



<a name="loio44ac6c5afef0464480fa18acb7483972__section_kyma_metrics_metricpipeline_setup"/>

## Setting up a MetricPipeline

In the following steps, you can see how to construct and deploy a typical `MetricPipeline`. Learn more about the available [parameters and attributes](https://kyma-project.io/#/telemetry-manager/user/resources/05-metricpipeline).



### 1. Create a MetricPipeline

To ship metrics to a new OTLP output, create a resource of the kind `MetricPipeline` and save the file \(named, for example, `metricpipeline.yaml`\).

This configures the underlying OTel Collector with a pipeline for metrics and opens a push endpoint that is accessible with the `telemetry-otlp-metrics` service. For details, see [Usage](telemetry-gateways-61567b7.md#loio61567b79e6db41cd81de5f58ec077201__section_usage).

The following push URLs are set up:

-   GRPC: `http://telemetry-otlp-metrics.kyma-system:4317`
-   HTTP: `http://telemetry-otlp-metrics.kyma-system:4318`

The default protocol for shipping the data to a backend is GRPC, but you can choose HTTP instead. Depending on the configured protocol, an `otlp` or an `otlphttp` exporter is used. Ensure that the correct port is configured as part of the endpoint.

-   For GRPC, use:

    ```
    apiVersion: telemetry.kyma-project.io/v1alpha1
    kind: MetricPipeline
    metadata:
      name: backend
    spec:
      output:
        otlp:
          endpoint:
            value: https://backend.example.com:4317
    
    ```

-   For HTTP, use the `protocol` attribute:

    ```
    apiVersion: telemetry.kyma-project.io/v1alpha1
    kind: MetricPipeline
    metadata:
      name: backend
    spec:
      output:
        otlp:
          protocol: http
          endpoint:
            value: https://backend.example.com:4318
    
    ```




### 2a. Add Authentication Details From Plain Text

To integrate with external systems, you must configure authentication details. You can use mutual TLS \(mTLS\), Basic Authentication, or custom headers:

-   mTLS:

    ```
    apiVersion: telemetry.kyma-project.io/v1alpha1
    kind: MetricPipeline
    metadata:
      name: backend
    spec:
      output:
        otlp:
          endpoint:
            value: https://backend.example.com/otlp:4317
          tls:
            cert:
              value: |
                -----BEGIN CERTIFICATE-----
                ...
            key:
              value: |
                -----BEGIN RSA PRIVATE KEY-----
                ...
    
    ```

-   Basic Authentication:

    ```
    apiVersion: telemetry.kyma-project.io/v1alpha1
    kind: MetricPipeline
    metadata:
      name: backend
    spec:
      output:
        otlp:
          endpoint:
            value: https://backend.example.com/otlp:4317
          authentication:
            basic:
              user:
                value: myUser
              password:
                value: myPwd
    
    ```

-   Token-based authentication with custom headers:

    ```
    apiVersion: telemetry.kyma-project.io/v1alpha1
    kind: MetricPipeline
    metadata:
      name: backend
    spec:
      output:
        otlp:
          endpoint:
            value: https://backend.example.com/otlp:4317
          headers:
            - name: Authorization
              prefix: Bearer
              value: "myToken"
    
    ```




### 2b. Add Authentication Details From Secrets

Integrations into external systems usually need authentication details dealing with sensitive data. To handle that data properly in Secrets, `MetricsPipeline` supports the reference of Secrets.

Using the `valueFrom` attribute, you can map Secret keys for mutual TLS \(mTLS\), Basic Authentication, or with custom headers.

You can store the value of the token in the referenced Secret without any prefix or scheme, and you can configure it in the `headers` section of the `MetricPipeline`. In this example, the token has the prefix “Bearer”.

-   mTLS:

    ```
    apiVersion: telemetry.kyma-project.io/v1alpha1
    kind: MetricPipeline
    metadata:
      name: backend
    spec:
      output:
        otlp:
          endpoint:
            value: https://backend.example.com/otlp:4317
          tls:
            cert:
              valueFrom:
                secretKeyRef:
                    name: backend
                    namespace: default
                    key: cert
            key:
              valueFrom:
                secretKeyRef:
                    name: backend
                    namespace: default
                    key: key
    
    ```

-   Basic Authentication:

    ```
    apiVersion: telemetry.kyma-project.io/v1alpha1
    kind: MetricPipeline
    metadata:
      name: backend
    spec:
      output:
        otlp:
          endpoint:
            valueFrom:
                secretKeyRef:
                    name: backend
                    namespace: default
                    key: endpoint
          authentication:
            basic:
              user:
                valueFrom:
                  secretKeyRef:
                    name: backend
                    namespace: default
                    key: user
              password:
                valueFrom:
                  secretKeyRef:
                    name: backend
                    namespace: default
                    key: password
    
    ```

-   Token-based authentication with custom headers:

    ```
    apiVersion: telemetry.kyma-project.io/v1alpha1
    kind: MetricPipeline
    metadata:
      name: backend
    spec:
      output:
        otlp:
          endpoint:
            value: https://backend.example.com:4317
          headers:
            - name: Authorization
              prefix: Bearer
              valueFrom:
                secretKeyRef:
                    name: backend
                    namespace: default
                    key: token 
    
    ```


The related Secret must have the referenced name, be located in the referenced namespace, and contain the mapped key. See the following example:

```
kind: Secret
apiVersion: v1
metadata:
  name: backend
  namespace: default
stringData:
  endpoint: https://backend.example.com:4317
  user: myUser
  password: XXX
  token: YYY

```



### 3. Rotate the Secret

Telemetry Manager continuously watches the Secret referenced with the *secretKeyRef* construct. You can update the Secret’s values, and Telemetry Manager detects the changes and applies the new Secret to the setup.

> ### Tip:  
> If you use a Secret owned by the [SAP BTP Service Operator](https://github.com/SAP/sap-btp-service-operator), you can configure an automated rotation using a credentialsRotationPolicy with a specific rotationFrequency and don’t have to intervene manually.



### 4. Activate Prometheus-Based Metrics

> ### Remember:  
> For the following approach, you must have instrumented your application using a library like the [Prometheus client library](https://prometheus.io/docs/instrumenting/clientlibs/), with a port in your workload exposed serving as a Prometheus metrics endpoint.

To enable collection of Prometheus-based metrics, define a `MetricPipeline` that has the `prometheus` section enabled as input:

```
apiVersion: telemetry.kyma-project.io/v1alpha1
kind: MetricPipeline
metadata:
  name: backend
spec:
  input:
    prometheus:
      enabled: true
  output:
    otlp:
      endpoint:
        value: https://backend.example.com:4317

```

The Metric agent is configured with a generic scrape configuration, which uses annotations to specify the endpoints to scrape in the cluster.

For metrics ingestion to start automatically, use the annotations of the following table. If an Istio sidecar is present, apply them to a Service that resolves your metrics port. By annotating the Service, all endpoints targeted by the Service are resolved and scraped by the Metric agent bypassing the Service itself. Only if Istio sidecar is not present, you can alternatively apply the annotations directly to the Pod.

**Prometheus Metrics Annotations**


<table>
<tr>
<th valign="top">

Annotation Key

</th>
<th valign="top">

Example Values

</th>
<th valign="top">

Default Value

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`prometheus.io/scrape` \(mandatory\)

</td>
<td valign="top">

*true*, *false*

</td>
<td valign="top">

none

</td>
<td valign="top">

Controls whether Prometheus Receiver automatically scrapes metrics from this target.

</td>
</tr>
<tr>
<td valign="top">

`prometheus.io/port` \(mandatory\)

</td>
<td valign="top">

*8080*, *9100*

</td>
<td valign="top">

none

</td>
<td valign="top">

Specifies the port where the metrics are exposed.

</td>
</tr>
<tr>
<td valign="top">

`prometheus.io/path` 

</td>
<td valign="top">

*/metrics*, */custom\_metrics*

</td>
<td valign="top">

*/metrics*

</td>
<td valign="top">

Defines the HTTP path where Prometheus Receiver can find metrics data.

</td>
</tr>
<tr>
<td valign="top">

`prometheus.io/scheme` \(only relevant when annotating a Service\)

</td>
<td valign="top">

*http*, *https*

</td>
<td valign="top">

If Istio is active, *https* is supported; otherwise, only *http* is available.

The default scheme is *http* unless an Istio sidecar is present, denoted by the label `security.istio.io/tlsMode=istio`, in which case *https* becomes the default.

</td>
<td valign="top">

Determines the protocol used for scraping metrics — either HTTPS with mTLS or plain HTTP.

</td>
</tr>
<tr>
<td valign="top">

`prometheus.io/param_<name>: <value>` 

</td>
<td valign="top">

*prometheus.io/param\_format: prometheus*

</td>
<td valign="top">

none

</td>
<td valign="top">

Instructs Prometheus Receiver to pass name-value pairs as URL parameters when calling the metrics endpoint.

</td>
</tr>
</table>

If you're running the Pod targeted by a Service with Istio, Istio must be able to derive the [appProtocol](https://kubernetes.io/docs/concepts/services-networking/service/#application-protocol) from the Service port definition; otherwise the communication for scraping the metric endpoint cannot be established. You must either prefix the port name with the protocol like in *http-metrics*, or explicitly define the `appProtocol` attribute. For example, see the following `Service` configuration:

```
apiVersion: v1
kind: Service
metadata:
  annotations:
    prometheus.io/port: "8080"
    prometheus.io/scrape: "true"
  name: sample
spec:
  ports:
  - name: http-metrics
    appProtocol: http
    port: 8080
    protocol: TCP
    targetPort: 8080
  selector:
    app: sample
  type: ClusterIP
```

> ### Note:  
> The Metric agent can scrape endpoints even if the workload is a part of the Istio service mesh and accepts mTLS communication. However, there’s a constraint: For scraping through HTTPS, Istio must configure the workload using “STRICT” mTLS mode. Without “STRICT” mTLS mode, you can set up scraping through HTTP by applying the annotation `prometheus.io/scheme=http`. For related troubleshooting, see [Log Entry: Failed to Scrape Prometheus Endpoint](https://help.sap.com/docs/BTP/60f1b283f0fd4d0aa7b3f8cea4d73d1d/44ac6c5afef0464480fa18acb7483972.html?locale=en-US#subsection_troubleshooting_log_entry_failed_to_scrape_prometheus).



### 5. Monitor Pipeline Health

By default, a `MetricPipeline` emits metrics about the health of all pipelines managed by the Telemetry module. Based on these metrics, you can track the status of every individual pipeline and set up alerting for it.

**Metrics for Pipelines and the Telemetry Module**


<table>
<tr>
<th valign="top">

Metric

</th>
<th valign="top">

Description

</th>
<th valign="top">

Availability

</th>
</tr>
<tr>
<td valign="top">

`kyma.resource.status.conditions`

</td>
<td valign="top">

Value represents status of different conditions reported by the resource. Possible values are *1* \(“True”\), *0* \(“False”\), and *\-1* \(other status values\)

</td>
<td valign="top">

Available for both, the pipelines and the Telemetry resource

</td>
</tr>
<tr>
<td valign="top">

`kyma.resource.status.state`

</td>
<td valign="top">

Value represents the state of the resource \(if present\)

</td>
<td valign="top">

Available for the Telemetry resource

</td>
</tr>
</table>

**Metric Attributes for Monitoring**


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`metric.attributes.Type`

</td>
<td valign="top">

Type of the condition

</td>
</tr>
<tr>
<td valign="top">

`metric.attributes.status`

</td>
<td valign="top">

Status of the condition

</td>
</tr>
<tr>
<td valign="top">

`metric.attributes.reason`

</td>
<td valign="top">

Contains a programmatic identifier indicating the reason for the condition's last transition

</td>
</tr>
</table>

To set up alerting, use an alert rule. In the following example, the alert is triggered if metrics are not delivered to the backend:

```
min by (k8s_resource_name) ((kyma_resource_status_conditions{type="TelemetryFlowHealthy",k8s_resource_kind="metricpipelines"})) == 0

```



### 6. Activate Runtime Metrics

To enable collection of runtime metrics, define a `MetricPipeline` that has the `runtime` section enabled as input:

```
apiVersion: telemetry.kyma-project.io/v1alpha1
kind: MetricPipeline
metadata:
  name: backend
spec:
  input:
    runtime:
      enabled: true
  output:
    otlp:
      endpoint:
        value: https://backend.example.com:4317

```

By default, metrics for all resources \(Pod, container, Node, Volume, DaemonSet, Deployment, StatefulSet, and Job\) are collected.

To enable or disable the collection of metrics for a specific resource, use the `resources` section in the `runtime` input.

The following example collects only DaemonSet, Deployment, StatefulSet, and Job metrics:

```
apiVersion: telemetry.kyma-project.io/v1alpha1
kind: MetricPipeline
metadata:
  name: backend
spec:
  input:
    runtime:
      enabled: true
      resources:
          pod:
            enabled: false
          container:
            enabled: false
          node:
            enabled: false
          volume:
            enabled: false
          daemonset:
            enabled: true
          deployment:
            enabled: true
          statefulset:
            enabled: true
          job:
            enabled: true
  output:
    otlp:
      endpoint:
        value: https://backend.example.com:4317

```

**Collected Metrics per Resource**


<table>
<tr>
<th valign="top">

Resource

</th>
<th valign="top">

From the [kubletstatsreceiver](https://github.com/open-telemetry/opentelemetry-collector-contrib/tree/main/receiver/kubeletstatsreceiver)

</th>
<th valign="top">

From the [k8sclusterreceiver](https://github.com/open-telemetry/opentelemetry-collector-contrib/tree/main/receiver/k8sclusterreceiver)

</th>
</tr>
<tr>
<td valign="top">

Pod

</td>
<td valign="top">

-   k8s.pod.cpu.capacity

-   k8s.pod.cpu.usage

-   k8s.pod.filesystem.available

-   k8s.pod.filesystem.capacity

-   k8s.pod.filesystem.usage

-   k8s.pod.memory.available

-   k8s.pod.memory.major\_page\_faults

-   k8s.pod.memory.page\_faults

-   k8s.pod.memory.rss

-   k8s.pod.memory.usage

-   k8s.pod.memory.working\_set

-   k8s.pod.network.errors

-   k8s.pod.network.io




</td>
<td valign="top">

-   k8s.pod.phase




</td>
</tr>
<tr>
<td valign="top">

Container

</td>
<td valign="top">

-   container.cpu.time

-   container.cpu.usage

-   container.filesystem.available

-   container.filesystem.capacity

-   container.filesystem.usage

-   container.memory.available

-   container.memory.major\_page\_faults

-   container.memory.page\_faults

-   container.memory.rss

-   container.memory.usage

-   container.memory.working\_set




</td>
<td valign="top">

-   k8s.container.cpu\_request

-   k8s.container.cpu\_limit

-   k8s.container.memory\_request

-   k8s.container.memory\_limit

-   k8s.container.restarts




</td>
</tr>
<tr>
<td valign="top">

Node

</td>
<td valign="top">

-   k8s.node.cpu.usage

-   k8s.node.filesystem.available

-   k8s.node.filesystem.capacity

-   k8s.node.filesystem.usage

-   k8s.node.memory.available

-   k8s.node.memory.usage

-   k8s.node.memory.rss

-   k8s.node.memory.working\_set




</td>
<td valign="top">

\-

</td>
</tr>
<tr>
<td valign="top">

Volume

</td>
<td valign="top">

-   k8s.volume.available

-   k8s.volume.capacity

-   k8s.volume.inodes

-   k8s.volume.inodes.free

-   k8s.volume.inodes.used




</td>
<td valign="top">

\-

</td>
</tr>
<tr>
<td valign="top">

Deployment

</td>
<td valign="top">

\-

</td>
<td valign="top">

-   k8s.deployment.available

-   k8s.deployment.desired




</td>
</tr>
<tr>
<td valign="top">

DaemonSet

</td>
<td valign="top">

\-

</td>
<td valign="top">

-   k8s.daemonset.current\_scheduled\_nodes

-   k8s.daemonset.desired\_scheduled\_nodes

-   k8s.daemonset.misscheduled\_nodes

-   k8s.daemonset.ready\_nodes




</td>
</tr>
<tr>
<td valign="top">

StatefulSet

</td>
<td valign="top">

\-

</td>
<td valign="top">

-   k8s.statefulset.current\_pods

-   k8s.statefulset.desired\_pods

-   k8s.statefulset.ready\_pods

-   k8s.statefulset.updated\_pods




</td>
</tr>
<tr>
<td valign="top">

Job

</td>
<td valign="top">

\-

</td>
<td valign="top">

-   k8s.job.active\_pods

-   k8s.job.desired\_successful\_pods

-   k8s.job.failed\_pods

-   k8s.job.max\_parallel\_pods

-   k8s.job.successful\_pods




</td>
</tr>
</table>



### 7. Activate Istio Metrics

To enable collection of Istio metrics, define a `MetricPipeline` that has the `istio` section enabled as input:

```
apiVersion: telemetry.kyma-project.io/v1alpha1
kind: MetricPipeline
metadata:
  name: backend
spec:
  input:
    istio:
      enabled: true
  output:
    otlp:
      endpoint:
        value: https://backend.example.com:4317

```

With this, the agent starts collecting all Istio metrics from Istio sidecars.

If you are using the `istio` input, you can also collect Envoy metrics. Envoy metrics provide insights into the performance and behavior of the Envoy proxy, such as request rates, latencies, and error counts. These metrics are useful for observability and troubleshooting service mesh traffic.

For details, see the list of available [Envoy metrics](https://www.envoyproxy.io/docs/envoy/latest/configuration/upstream/cluster_manager/cluster_stats) and [server metrics](https://www.envoyproxy.io/docs/envoy/latest/configuration/observability/statistics).

> ### Note:  
> Envoy metrics are only available for the `istio` input. Ensure that Istio sidecars are correctly injected into your workloads for Envoy metrics to be available.

By default, Envoy metrics collection is disabled.

To activate Envoy metrics, enable the `envoyMetrics` section in the `MetricPipeline` specification under the `istio` input:

```
apiVersion: telemetry.kyma-project.io/v1alpha1
kind: MetricPipeline
metadata:
  name: envoy-metrics
spec:
  input:
    istio:
      enabled: true
      envoyMetrics:
        enabled: true
  output:
    otlp:
      endpoint:
        value: https://backend.example.com:4317

```



### 8. Deactivate OTLP Metrics

By default, `otlp` input is enabled.

To drop the push-based OTLP metrics that are received by the metric gateway, define a `MetricPipeline` that has the `otlp` section disabled as an input:

```
apiVersion: telemetry.kyma-project.io/v1alpha1
kind: MetricPipeline
metadata:
  name: backend
spec:
  input:
    istio:
      enabled: true
    otlp:
      disabled: true
  output:
    otlp:
      endpoint:
        value: https://backend.example.com:4317

```

With this, the agent starts collecting all Istio metrics from Istio sidecars, and the push-based OTLP metrics are dropped.



### 9. Add Filters

To filter metrics by namespaces, define a `MetricPipeline` that has the `namespaces` section defined in one of the inputs. For example, you can specify the namespaces from which metrics are collected or the namespaces from which metrics are dropped. Learn more about the available [parameters and attributes](https://kyma-project.io/#/telemetry-manager/user/resources/05-metricpipeline).

-   The following example collects runtime metrics **only** from the `foo` and `bar` namespaces:

    ```
    apiVersion: telemetry.kyma-project.io/v1alpha1
    kind: MetricPipeline
    metadata:
      name: backend
    spec:
      input:
        runtime:
          enabled: true
          namespaces:
            include:
              - foo
              - bar
      output:
        otlp:
          endpoint:
            value: https://backend.example.com:4317
    
    ```

-   The following example collects runtime metrics from all namespaces **except** the `foo` and `bar` namespaces:

    ```
    apiVersion: telemetry.kyma-project.io/v1alpha1
    kind: MetricPipeline
    metadata:
      name: backend
    spec:
      input:
        runtime:
          enabled: true
          namespaces:
            exclude:
              - foo
              - bar
      output:
        otlp:
          endpoint:
            value: https://backend.example.com:4317
    
    ```


> ### Note:  
> The default settings depend on the input:
> 
> If no namespace selector is defined for the `prometheus` or `runtime` input, then metrics from system namespaces are **excluded** by default.
> 
> However, if the namespace selector is not defined for the `istio` and `otlp` input, then metrics from system namespaces are **included** by default.



### 10. Activate Diagnostic Metrics

If you use the `prometheus` or `istio` input, for every metric source typical scrape metrics are produced, such as `up`, `scrape_duration_seconds`, `scrape_samples_scraped`, `scrape_samples_post_metric_relabeling`, and `scrape_series_added`.

By default, they are disabled.

If you want to use them for debugging and diagnostic purposes, you can activate them. To activate diagnostic metrics, define a `MetricPipeline` that has the `diagnosticMetrics` section defined.

-   The following example collects diagnostic metrics **only** for input `istio`:

    ```
    apiVersion: telemetry.kyma-project.io/v1alpha1
    kind: MetricPipeline
    metadata:
      name: backend
    spec:
      input:
        istio:
          enabled: true
          diagnosticMetrics:
            enabled: true
      output:
        otlp:
          endpoint:
            value: https://backend.example.com:4317
    
    ```

-   The following example collects diagnostic metrics **only** for input `prometheus`:

    ```
    apiVersion: telemetry.kyma-project.io/v1alpha1
    kind: MetricPipeline
    metadata:
      name: backend
    spec:
      input:
        prometheus:
          enabled: true
          diagnosticMetrics:
            enabled: true
      output:
        otlp:
          endpoint:
            value: https://backend.example.com:4317
    
    ```


> ### Note:  
> Diagnostic metrics are only available for inputs `prometheus` and `istio`. Learn more about the available [parameters and attributes](https://kyma-project.io/#/telemetry-manager/user/resources/05-metricpipeline).



### 11. Deploy the Pipeline

To activate the `MetricPipeline`, apply the `metricpipeline.yaml` resource file in your cluster:

```
kubectl apply -f metricpipeline.yaml
```



### Result

You activated a `MetricPipeline` and metrics start streaming to your backend.

To check that the pipeline is running, wait until the status conditions of the `MetricPipeline` in your cluster have status ***True***:

> ### Output Code:  
> ```
> kubectl get metricpipeline
> NAME      CONFIGURATION GENERATED   GATEWAY HEALTHY   AGENT HEALTHY   FLOW HEALTHY
> backend   True                      True              True            True       
> ```



<a name="loio44ac6c5afef0464480fa18acb7483972__section_kyma_metrics_operations"/>

## Operations

A `MetricPipeline` runs several OTel Collector instances in your cluster. This Deployment serves OTLP endpoints and ships received data to the configured backend.

The Telemetry module ensures that the OTel Collector instances are operational and healthy at any time, for example, with buffering and retries. However, there may be situations when the instances drop metrics, or cannot handle the metric load.

To detect and fix such situations, check the pipeline status and check out [Troubleshooting](metrics-44ac6c5.md#loio44ac6c5afef0464480fa18acb7483972__section_kyma_metrics_troubleshooting).

If you have set up pipeline health monitoring, check the alerts and reports in an integrated backend like SAP Cloud Logging. For details, see [Setting up a MetricPipeline](metrics-44ac6c5.md#loio44ac6c5afef0464480fa18acb7483972__section_kyma_metrics_metricpipeline_setup), step *Monitor Pipeline Health*, as well as [Integrate with SAP Cloud Logging](integrate-with-sap-cloud-logging-eac5771.md).

> ### Caution:  
> It's not recommended to access the metrics endpoint of the used OTel Collector instances directly, because the exposed metrics are no official API of the Kyma Telemetry module. Breaking changes can happen if the underlying OTel Collector version introduces such.
> 
> Instead, use the [pipeline status](https://github.com/a-thaler/telemetry-manager/blob/ebbee2c1c785162ffe0970a238e1e775f9992d33/docs/user/resources/05-metricpipeline.md#metricpipeline-status).



<a name="loio44ac6c5afef0464480fa18acb7483972__section_kyma_metrics_limitations"/>

## Limitations

-   **Throughput**: Assuming an average metric with 20 metric data points and 10 labels, the default metric **gateway** setup has a maximum throughput of 34K metric data points/sec. If more data is sent to the gateway, it is refused. To increase the maximum throughput, manually scale out the gateway by increasing the number of replicas for the metric gateway. See [Module Configuration and Status](telemetry-manager-04d79d5.md#loio04d79d5517204da68029f43b9f052396__section_telemetry_module_configuration).

    The metric **agent** setup has a maximum throughput of 14K metric data points/sec per instance. If more data must be ingested, it is refused. If a metric data endpoint emits more than 50.000 metric data points per scrape loop, the metric agent refuses all the data.

-   **Load Balancing With Istio**: To ensure availability, the metric gateway runs with multiple instances. If you want to increase the maximum throughput, use manual scaling and enter a higher number of instances.

    By design, the connections to the gateway are long-living connections \(because OTLP is based on gRPC and HTTP/2\). For optimal scaling of the gateway, the clients or applications must balance the connections across the available instances, which is automatically achieved if you use an Istio sidecar. If your application has no Istio sidecar, the data is always sent to one instance of the gateway.

-   **Unavailability of Output**: For up to 5 minutes, a retry for data is attempted when the destination is unavailable. After that, data is dropped.

-   **No Guaranteed Delivery**: The used buffers are volatile. If the gateway or agent instances crash, metric data can be lost.

-   **Multiple MetricPipeline Support**: The maximum amount of `MetricPipeline` resources is 5.




<a name="loio44ac6c5afef0464480fa18acb7483972__section_kyma_metrics_troubleshooting"/>

## Troubleshooting



### No Metrics Arrive at the Backend

**Symptom**:

-   No metrics arrive at the backend.

-   In the `MetricPipeline` status, the `TelemetryFlowHealthy` condition has status ***AllDataDropped***.


**Cause**: Incorrect backend endpoint configuration \(such as using the wrong authentication credentials\) or the backend is unreachable.

**Solution**:

1.  Check the `telemetry-metric-gateway` Pods for error logs by calling `kubectl logs -n kyma-system {POD_NAME}`.

2.  Check if the backend is up and reachable.

3.  Fix the errors.




### Not All Metrics Arrive at the Backend

**Symptom**:

-   The backend is reachable and the connection is properly configured, but some metrics are refused.

-   In the `MetricPipeline` status, the `TelemetryFlowHealthy` condition has status ***SomeDataDropped***.


**Cause**: It can happen due to a variety of reasons - for example, the backend is limiting the ingestion rate.

**Solution**:

1.  Check the `telemetry-metric-gateway` Pods for error logs by calling `kubectl logs -n kyma-system {POD_NAME}`. Also, check your observability backend to investigate potential causes.

2.  If backend is limiting the rate by refusing metrics, try the options described in [Gateway Buffer Filling Up](https://help.sap.com/docs/BTP/60f1b283f0fd4d0aa7b3f8cea4d73d1d/44ac6c5afef0464480fa18acb7483972.html?locale=en-US#subsection_troubleshoot_bufferfllingup).

3.  Otherwise, take the actions appropriate to the cause indicated in the logs.




### Only Istio Metrics Arrive at the Backend

**Symptom**: Custom metrics don’t arrive at the backend, but Istio metrics do.

**Cause**: Your SDK version is incompatible with the OTel Collector version.

**Solution**:

1.  Check which SDK version you are using for instrumentation.

2.  Investigate whether it is compatible with the OTel Collector version.

3.  If required, upgrade to a supported SDK version.




### Log Entry: Failed to Scrape Prometheus Endpoint

**Symptom**: Custom metrics don’t arrive at the destination. The OTel Collector produces log entries saying “Failed to scrape Prometheus endpoint”, such as the following example:

> ### Output Code:  
> ```
> 2023-08-29T09:53:07.123Z warn internal/transaction.go:111 Failed to scrape Prometheus endpoint {"kind": "receiver", "name": "prometheus/app-pods", "data_type": "metrics", "scrape_timestamp": 1693302787120, "target_labels": "{__name__=\"up\", instance=\"10.42.0.18:8080\", job=\"app-pods\"}"}
> 
> ```

**Cause 1**: The workload is not configured to use “STRICT” mTLS mode. For details, see [Activate Prometheus-Based Metrics](https://help.sap.com/docs/BTP/60f1b283f0fd4d0aa7b3f8cea4d73d1d/44ac6c5afef0464480fa18acb7483972.html?locale=en-US#subsection_activate_prometheus_metrics).

**Solution 1**: You can either set up “STRICT” mTLS mode or HTTP scraping:

-   Configure the workload using “STRICT” mTLS mode \(for example, by applying a corresponding PeerAuthentication\).

-   Set up scraping through HTTP by applying the `prometheus.io/scheme=http` annotation.


**Cause 2**: The Service definition enabling the scrape with Prometheus annotations does not reveal the application protocol to use in the port definition. For details, see [Activate Prometheus-Based Metrics](https://help.sap.com/docs/BTP/60f1b283f0fd4d0aa7b3f8cea4d73d1d/44ac6c5afef0464480fa18acb7483972.html?locale=en-US#subsection_activate_prometheus_metrics).

**Solution 2**: Define the application protocol in the Service port definition by either prefixing the port name with the protocol, like in *http-metrics* or define the `appProtocol` attribute.

**Cause 3**: A deny-all `NetworkPolicy` was created in the workload namespace, which prevents that the agent can scrape metrics from annotated workloads.

**Solution 3**: Create a separate `NetworkPolicy` to explicitly let the agent scrape your workload using the `telemetry.kyma-project.io/metric-scrape` label. For example, see the following `NetworkPolicy` configuration:

```
yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-traffic-from-agent
spec:
  podSelector: 
    matchLabels:
      app.kubernetes.io/name: "annotated-workload" # <your workload here>
  ingress:
  - from:
    - namespaceSelector:
        matchLabels:
          kubernetes.io/metadata.name: kyma-system
      podSelector:
        matchLabels:
          telemetry.kyma-project.io/metric-scrape: "true"
  policyTypes:
  - Ingress
```



### Gateway Buffer Filling Up

**Symptom**: In the `MetricPipeline` status, the `TelemetryFlowHealthy` condition has status ***BufferFillingUp***.

**Cause**: The backend export rate is too low compared to the gateway ingestion rate.

**Solution**:

-   Option 1: Increase maximum backend ingestion rate. For example, by scaling out the SAP Cloud Logging instances.

-   Option 2: Reduce emitted metrics by re-configuring the `MetricPipeline` \(for example, by disabling certain inputs or applying namespace filters\).

-   Option 3: Reduce emitted metrics in your applications.




### Gateway Throttling

**Symptom**: In the `MetricPipeline` status, the `TelemetryFlowHealthy` condition has status ***GatewayThrottling***.

**Cause**: Gateway cannot receive metrics at the given rate.

**Solution**: Manually scale out the gateway by increasing the number of replicas for the metric gateway. See [Module Configuration and Status](telemetry-manager-04d79d5.md#loio04d79d5517204da68029f43b9f052396__section_telemetry_module_configuration).

