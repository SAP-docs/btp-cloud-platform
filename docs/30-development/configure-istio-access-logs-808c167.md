<!-- loio808c167005d346f7b883a260c44e6f27 -->

# Configure Istio Access Logs

To monitor traffic in your service mesh, configure Istio to send access logs. The `LogPipeline` automatically receives these logs through its default OTLP input.



<a name="loio808c167005d346f7b883a260c44e6f27__section_prerequisites"/>

## Prerequisites

-   You have the Istio module in your cluster. See [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).
-   You have access to Kyma dashboard. Alternatively, if you prefer CLI, you need [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl).



<a name="loio808c167005d346f7b883a260c44e6f27__section_context"/>

## Context

Istio access logs help you monitor the "four golden signals" \(latency, traffic, errors, and saturation\) and troubleshoot anomalies.

By default, these logs are disabled because they can generate a high volume of data. To collect them, you apply an [Istio](https://istio.io/latest/docs/reference/config/telemetry/) `Telemetry` resource to a specific namespace, for the Istio Ingress Gateway, or for the entire mesh.

> ### Caution:  
> Enabling access logs, especially for the entire mesh, can significantly increase log volume and may lead to higher storage costs. Enable this feature only for the resources or components that you want to monitor.

After enabling Istio access logs, reduce data volume and costs by filtering them \(see [Filter Logs](filter-logs-58445a0.md)\).

The Istio module provides a preconfigured [extension provider](https://istio.io/latest/docs/reference/config/istio.mesh.v1alpha1/#MeshConfig-ExtensionProvider) called `kyma-logs`, which tells Istio to send access logs to the Telemetry module's OTLP endpoint. If your `LogPipeline` uses the legacy `http` output, you must use the `stdout-json` provider instead.

> ### Note:  
> You can only have one mesh-wide Istio `Telemetry` resource. If you also plan to enable Istio tracing \(see [Configure Istio Tracing](configure-istio-tracing-3f504d8.md)\), configure both access logging and tracing in this single resource.



<a name="loio808c167005d346f7b883a260c44e6f27__section_istio_logs_for_namespace"/>

## Enable Istio Logs for a Namespace

Apply the Istio `Telemetry` resource to a specifc namespace:

```
apiVersion: telemetry.istio.io/v1
kind: Telemetry
metadata:
  name: access-config
  namespace: $YOUR_NAMESPACE
spec:
  accessLogging:
    - providers:
      - name: kyma-logs
```



<a name="loio808c167005d346f7b883a260c44e6f27__section_istio_logs_for_ingress_gateway"/>

## Enable Istio Logs for the Ingress Gateway

To monitor all traffic entering your mesh, enable access logs on the Istio Ingress Gateway \(instead of the individual proxies of your workloads\).

Apply the Istio `Telemetry` resource to the `istio-system` namespace, selecting the gateway Pods:

```
apiVersion: telemetry.istio.io/v1
kind: Telemetry
metadata:
  name: mesh-default
  namespace: istio-system
spec:
  selector:
    matchLabels:
      istio: ingressgateway
  accessLogging:
    - providers:
      - name: kyma-logs
```



<a name="loio808c167005d346f7b883a260c44e6f27__section_istio_logs_for_entire_mesh"/>

## Enable Istio Logs for the Entire Mesh

To enable access logs globally for all proxies in the mesh, apply the Istio `Telemetry` resource to the `istio-system` namespace. Use this option with caution due to the high data volume.

```
apiVersion: telemetry.istio.io/v1
kind: Telemetry
metadata:
  name: mesh-default
  namespace: istio-system
spec:
  accessLogging:
    - providers:
      - name: kyma-logs
```

