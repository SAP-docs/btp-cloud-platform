<!-- loio12871325f46f48f6b4340c8ef47bdc66 -->

# Application Logs

With application logs, you can debug an application and derive the internal state of an application. When logs are emitted with the correct severity level and context, they're essential for observing an application.



<a name="loio12871325f46f48f6b4340c8ef47bdc66__section_f2l_w4h_1bc"/>

## Overview

The Telemetry module provides the [Fluent Bit](https://fluentbit.io/) log agent for the collection and shipment of application logs of any container running in the Kyma runtime.

You can configure the log agent with external systems using runtime configuration with a dedicated Kubernetes API \([CRD](https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/#customresourcedefinitions)\) named `LogPipeline`. With the `LogPipeline`’s HTTP output, you can natively integrate with vendors that support this output, or with any vendor using a [Fluentd integration](https://medium.com/hepsiburadatech/fluent-logging-architecture-fluent-bit-fluentd-elasticsearch-ca4a898e28aa).

The feature is optional, if you don’t want to use the Logs feature, simply don’t set up a `LogPipeline`.



<a name="loio12871325f46f48f6b4340c8ef47bdc66__section_kyma_logs_prerequisites"/>

## Prerequisites

Your application must log to `stdout` or `stderr`, which ensures that the logs can be processed by Kubernetes primitives like `kubectl logs`. For details, see [Kubernetes: Logging Architecture](https://kubernetes.io/docs/concepts/cluster-administration/logging/).



<a name="loio12871325f46f48f6b4340c8ef47bdc66__section_kyma_logs_architecture"/>

## Architecture



### Log Agent

In the Kyma cluster, the Telemetry module provides a DaemonSet of [Fluent Bit](https://fluentbit.io/) acting as a agent. The agent tails container logs from the Kubernetes container runtime and ships them to a backend.

![](images/Kyma_Logs_Architecture_c4cfebf.svg)

1.  Container logs are stored by the Kubernetes container runtime under the `var/log` directory and its subdirectories.

2.  Fluent Bit runs as a [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/) \(one instance per Node\), detects any new log files in the folder, and tails them using a filesystem buffer for reliability.

3.  Fluent Bit discovers additional Pod metadata, such as Pod annotations and labels.

4.  Telemetry Manager configures Fluent Bit with your output configuration, observes the log flow, and reports problems in the `LogPipeline` status.

5.  The log agent sends the data to the observability system that’s specified in your `LogPipeline` resource - either within the Kyma cluster, or, if authentication is set up, to an external observability backend. You can use the integration with HTTP to integrate a system directly or with an additional Fluentd installation.

6.  To analyze and visualize your logs, access the internal or external observability system.




### Telemetry Manager

The `LogPipeline` resource is watched by Telemetry Manager, which is responsible for generating the custom parts of the Fluent Bit configuration.

![](images/Logging_Resources_2289864.svg)

1.  Telemetry Manager watches all `LogPipeline` resources and related Secrets.

2.  Furthermore, Telemetry Manager takes care of the full lifecycle of the Fluent Bit DaemonSet itself. Only if you defined a `LogPipeline`, the agent is deployed.

3.  Whenever the configuration changes, Telemetry Manager validates the configuration \(with a [validating webhook](https://kubernetes.io/docs/reference/access-authn-authz/extensible-admission-controllers/)\) and generates a new configuration for the Fluent Bit DaemonSet, where several ConfigMaps for the different aspects of the configuration are generated.

4.  Referenced Secrets are copied into one Secret that is also mounted to the DaemonSet.




### Log Agent

If a `LogPipeline` is defined, a DaemonSet is deployed acting as an agent. The agent is based on [Fluent Bit](https://fluentbit.io/) and encompasses the collection of application logs provided by the Kubernetes container runtime. The agent sends all data to the configured backend.



<a name="loio12871325f46f48f6b4340c8ef47bdc66__section_kyma_logs_logpipeline_setup"/>

## Setting up a LogPipeline

In the following steps, you can see how to construct and deploy a typical `LogPipeline`. Learn more about the available [parameters and attributes](https://kyma-project.io/#/telemetry-manager/user/resources/02-logpipeline).



### 1. Create a LogPipeline and Output

To ship application logs to a new output, create a resource of the kind `LogPipeline` and save the file \(named, for example, `logpipeline.yaml`\).

```
kind: LogPipeline
apiVersion: telemetry.kyma-project.io/v1alpha1
metadata:
  name: http-backend
spec:
  output:
    http:
      dedot: false
      port: "80"
      uri: "/"
      host:
        value: https://myhost/logs
      user:
        value: "user"
      password:
        value: "not-required"
```

An output is a data destination configured by a [Fluent Bit output](https://docs.fluentbit.io/manual/pipeline/outputs) of the relevant type. The `LogPipeline` supports the *http* output type: It sends the data to the specified HTTP destination. The output is designed to integrate with a [Fluentd HTTP Input](https://docs.fluentd.org/input/http), which opens up a huge ecosystem of integration possibilities.



### 2. Filter Your Input

`kube-system`, `istio-system`, `kyma-system`\), which are excluded by default.

To filter your application logs by namespace or container, use an `input` spec to restrict or specify which resources you want to include. For example, you can define the namespaces to include in the input collection, exclude namespaces from the input collection, or choose that only system namespaces are included. Learn more about the available By default, input is collected from all namespaces, except the system namespaces \([parameters and attributes](https://kyma-project.io/#/telemetry-manager/user/resources/02-logpipeline).

The following example collects input from all namespaces excluding `kyma-system` and only from the `istio-proxy` containers:

```
kind: LogPipeline
apiVersion: telemetry.kyma-project.io/v1alpha1
metadata:
  name: http-backend
spec:
  input:
    application:
      namespaces:
        exclude:
          - kyma-system
      containers:
        include:
          - istio-proxy
  output:
    ...
```

It might happen that Fluent Bit prints an error per processed log line, which is then collected and re-processed. To avoid problems with such recursive logs, it is recommended that you exclude the logs of the Fluent Bit container. The following example collects input from all namespaces including system namespaces, but excludes the Fluent Bit container:

```
spec:
  input:
    application:
      namespaces:
        system: true
      containers:
        exclude:
        - fluent-bit

```



### 3. Add Authentication Details From Secrets

By defIntegrations into external systems usually need authentication details dealing with sensitive data. To handle that data properly in Secrets, `LogPipeline` supports the reference of Secrets.

Using the *http* output definition and the `valueFrom` attribute, you can map Secret keys for mutual TLS \(mTLS\) or Basic Authentication:

-   mTLS:

    ```
    apiVersion: telemetry.kyma-project.io/v1alpha1
    kind: LogPipeline
    metadata:
      name: http-backend
    spec:
      output:
        http:
          dedot: false
          port: "80"
          uri: "/"
          host:
            valueFrom:
                secretKeyRef:
                  name: http-backend-credentials
                  namespace: default
                  key: HTTP_ENDPOINT
          tls:
            cert:
              valueFrom:
                secretKeyRef:
                  name: http-backend-credentials
                  namespace: default
                  key: TLS_CERT
            key:
              valueFrom:
                secretKeyRef:
                  name: http-backend-credentials
                  namespace: default
                  key: TLS_KEY
      input:
        ...
      filters:
        ...
    
    ```

-   Basic Authentication:

    ```
    apiVersion: telemetry.kyma-project.io/v1alpha1
    kind: LogPipeline
    metadata:
      name: http-backend
    spec:
      output:
        http:
          dedot: false
          port: "80"
          uri: "/"
          host:
            valueFrom:
              secretKeyRef:
                name: http-backend-credentials
                namespace: default
                key: HTTP_ENDPOINT
          user:
            valueFrom:
              secretKeyRef:
                name: http-backend-credentials
                namespace: default
                key: HTTP_USER
          password:
            valueFrom:
              secretKeyRef:
                name: http-backend-credentials
                namespace: default
                key: HTTP_PASSWORD
      input:
        ...
      filters:
        ...
    ```


The related Secret must have the referenced name, be located in the referenced namespace, and contain the mapped key. See the following example:

```
kind: Secret
apiVersion: v1
metadata:
  name: http-backend-credentials
stringData:
  HTTP_ENDPOINT: https://myhost/logs
  HTTP_USER: myUser
  HTTP_PASSWORD: XXX
  TLS_CERT: ...
  TLS_KEY: ...

```



### 4. Rotate the Secret

Telemetry Manager continuously watches the Secret referenced with the *secretKeyRef* construct. You can update the Secret’s values, and Telemetry Manager detects the changes and applies the new Secret to the setup.

> ### Tip:  
> If you use a Secret owned by the [SAP BTP Service Operator](https://github.com/SAP/sap-btp-service-operator), you can configure an automated rotation using a credentialsRotationPolicy with a specific rotationFrequency and don’t have to intervene manually.



### 5. Deploy the Pipeline

To activate the `LogPipeline`, apply the `logpipeline.yaml` resource file in your cluster:

```
kubectl apply -f logpipeline.yaml
```



### Result

You activated a `LogPipeline` and logs start streaming to your backend.

To check that the pipeline is running, wait until the status conditions of the `LogPipeline` in your cluster have status ***True***:

> ### Output Code:  
> ```
> kubectl get logpipeline
> NAME      CONFIGURATION GENERATED   AGENT HEALTHY   FLOW HEALTHY
> backend   True                      True            True        
> ```



<a name="loio12871325f46f48f6b4340c8ef47bdc66__section_kyma_logs_logrecord_processing"/>

## Log Record Processing

After a log record has been read, it is preprocessed by configured plugins, like the `kubernetes` filter. Thus, when a record is ready to be processed by the sections defined in the `LogPipeline` definition, it has several attributes available for processing and shipment.

![](images/Telemetry_Log_Flow_7c6a7a6.svg)

Learn more about the flow of the log record through the general pipeline and the available log attributes in the following stages:



### Container Log Message

The following example assumes that there’s a container `myContainer` of Pod `myPod`, running in namespace `myNamespace`, logging to `stdout` with the following log message in the JSON format:

> ### Output Code:  
> ```
> {
>   "level": "warn",
>   "message": "This is the actual message",
>   "tenant": "myTenant",
>   "traceID": "123"
> }
> ```



### Tail Input

The `tail` input plugin reads the log message from a log file managed by the container runtime. The input plugin brings a dedicated filesystem buffer for the pipeline. The file name contains the namespace, Pod, and container information that will be available later as part of the [tag](https://docs.fluentbit.io/manual/concepts/key-concepts#tag). The tag is prefixed with the pipeline name. The resulting log record available in an internal Fluent Bit representation looks similar to the following example:

> ### Output Code:  
> ```
> {
>   "time": "2022-05-23T15:04:52.193317532Z",
>   "stream": "stdout",
>   "_p": "F",
>   "log": "{\"level\": \"warn\",\"message\": \"This is the actual message\",\"tenant\": \"myTenant\",\"traceID\": \"123\"}
> }
> ```

The attributes have the following meaning:

-   `time`: The timestamp generated by the container runtime at the moment the log was written to the log file.

-   `stream`: The stream to which the application wrote the log, either `stdout` or `stderr`.

-   `_p`: Indicates if the log message is partial \(*P*\) or final \(*F*\). Optional, dependent on container runtime. Because a CRI multiline parser is applied for the tailing phase, all multilines on the container runtime level are aggregated already and no partial entries must be left.

-   `log`: The raw and unparsed log message.




### Kubernetes Filter \(Metadata\)

After the tail input, the [Kubernetes filter](https://docs.fluentbit.io/manual/pipeline/filters/kubernetes) is applied. The container information from the log file name \(available in the tag\) is interpreted and used for a Kubernetes API Server request to resolve more metadata of the container. All the resolved metadata enrich the existing record as a new attribute `kubernetes`:

> ### Output Code:  
> ```
> {
>   "kubernetes":
>   {
>       "pod_name": "myPod-74db47d99-ppnsw",
>       "namespace_name": "myNamespace",
>       "pod_id": "88dbd1ef-d977-4636-804d-ef220454be1c",
>       "host": "myHost1",
>       "container_name": "myContainer",
>       "docker_id": "5649c36fcc1e956fc95e3145441f427d05d6e514fa439f4e4f1ccee80fb2c037",
>       "container_hash": "myImage@sha256:1f8d852989c16345d0e81a7bb49da231ade6b99d51b95c56702d04c417549b26",
>       "container_image": "myImage:myImageTag",
>       "labels":
>       {
>           "app": "myApp",
>           "sidecar.istio.io/inject": "true",
>           ...
>       }
>   }
> }
> 
> ```



### Kubernetes Filter \(JSON Parser\)

After the enrichment of the log record with the Kubernetes-relevant metadata, the [Kubernetes filter](https://docs.fluentbit.io/manual/pipeline/filters/kubernetes) also tries to parse the record as a JSON document. If that is successful, all the parsed root attributes of the parsed document are added as new individual root attributes of the log.

The record **before** applying the JSON parser:

> ### Output Code:  
> ```
> {
>   "time": "2022-05-23T15:04:52.193317532Z",
>   "stream": "stdout",
>   "_p": "F",
>   "log": "{\"level\": \"warn\",\"message\": \"This is the actual message\",\"tenant\": \"myTenant\",\"traceID\": \"123\"}",
>   "kubernetes": {...}
> }
> 
> ```

The record **after** applying the JSON parser:

> ### Output Code:  
> ```
> {
>   "time": "2022-05-23T15:04:52.193317532Z",
>   "stream": "stdout",
>   "_p": "F",
>   "log": "{\"level\": \"warn\",\"message\": \"This is the actual message\",\"tenant\": \"myTenant\",\"traceID\": \"123\"}",
>   "kubernetes": {...},
>   "level": "warn",
>   "message": "This is the actual message",
>   "tenant": "myTenant",
>   "traceID": "123"
> }
> 
> ```



<a name="loio12871325f46f48f6b4340c8ef47bdc66__section_kyma_logs_operations"/>

## Operations

The Telemetry module ensures that the log agent instances are operational and healthy at any time, for example, with buffering and retries. However, there may be situations when the instances drop logs, or cannot handle the log load.

To detect and fix such situations, check the pipeline status and check out [Troubleshooting](application-logs-1287132.md#loio12871325f46f48f6b4340c8ef47bdc66__section_kyma_logs_troubleshooting).



<a name="loio12871325f46f48f6b4340c8ef47bdc66__section_kyma_logs_limitations"/>

## Limitations

-   **Reserved Log Attributes**: The log attribute named `kubernetes` is a special attribute that’s enriched by the `kubernetes` filter. When you use that attribute as part of your structured log payload, the metadata enriched by the filter are overwritten by the payload data. Filters that rely on the original metadata might no longer work as expected.

-   **Buffer Limits**: Fluent Bit buffers up to 1 GB of logs if a configured output cannot receive logs. The oldest logs are dropped when the limit is reached or after 300 retries.

-   **Throughput**: Each Fluent Bit Pod \(each running on a dedicated Node\) can process up to 10 MB/s of logs for a single `LogPipeline`. With multiple pipelines, the throughput per pipeline is reduced. The used logging backend or performance characteristics of the output plugin might limit the throughput earlier.

-   **Max Amount of Pipelines**: The maximum amount of LogPipeline resources is 5.




<a name="loio12871325f46f48f6b4340c8ef47bdc66__section_kyma_logs_troubleshooting"/>

## Troubleshooting



### No Logs Arrive at the Backend

**Symptom**:

-   No logs arrive at the backend.

-   In the `LogPipeline` status, the `TelemetryFlowHealthy` condition has status ***AllDataDropped***.


**Cause**: Incorrect backend endpoint configuration \(for example, using the wrong authentication credentials\) or the backend being unreachable.

**Solution**:

-   Check the `telemetry-fluent-bit` Pods for error logs by calling `kubectl logs -n kyma-system {POD_NAME}`.

-   Check if the backend is up and reachable.




### Not All Logs Arrive at the Backend

**Symptom**: The backend is reachable and the connection is properly configured, but some logs are refused. In the `LogPipeline` status, the `TelemetryFlowHealthy` condition has status ***SomeDataDropped***.

**Cause**: It can happen due to a variety of reasons. For example, a possible reason may be that the backend is limiting the ingestion rate, or the backend is refusing logs because they are too large.

**Solution**:

1.  Check the `telemetry-fluent-bit` Pods for error logs by calling `kubectl logs -n kyma-system {POD_NAME}`. Also, check your observability backend to investigate potential causes.

2.  If backend is limiting the rate by refusing logs, try the options described in **Agent Buffer Filling Up**.

3.  Otherwise, take the actions appropriate to the cause indicated in the logs.




### Agent Buffer Filling Up

**Symptom**: In the `LogPipeline` status, the `TelemetryFlowHealthy` condition has status ***BufferFillingUp***.

**Cause**: The backend export rate is too low compared to the log collection rate.

**Solution**:

-   Option 1: Increase maximum backend ingestion rate. For example, by scaling out the SAP Cloud Logging instances.

-   Option 2: Reduce emitted logs by re-configuring the `LogPipeline` \(for example, by applying namespace or container filters\).

-   Option 3: Reduce emitted logs in your applications \(for example, by changing severity level\).


