<!-- loiod3f20b6b01a34987a0ae3e6097d3c69a -->

# Configuring Istio Access Logs

Use the Telemetry API to selectively enable the Istio access logs.



<a name="loiod3f20b6b01a34987a0ae3e6097d3c69a__prereq_ndk_whb_tcc"/>

## Prerequisites

-   You have the Istio module added. See [Add and Delete a Kyma Module](../50-administration-and-ops/add-and-delete-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).
-   To use CLI instructions, you must install [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl) and [curl](https://curl.se/). Alternatively, you can use Kyma dashboard.



## Context

You can enable [Istio access logs](https://istio.io/latest/docs/tasks/observability/logs/access-log/) to provide fine-grained details about the access to workloads that are part of the Istio service mesh. This can help indicate the four “golden signals” of monitoring \(latency, traffic, errors, and saturation\) and troubleshooting anomalies. The Istio setup shipped with the Istio module provides a pre-configured [extension provider](https://istio.io/latest/docs/tasks/observability/telemetry) for access logs, which configures the Istio proxies to print access logs to stdout using the JSON format. It uses a configuration similar to the following one:

```
extensionProviders:
  - name: stdout-json
    envoyFileAccessLog:
      path: "/dev/stdout"
      logFormat:
        labels:
          ...
          traceparent: "%REQ(TRACEPARENT)%"
          tracestate: "%REQ(TRACESTATE)%"
```

The [log format](https://github.com/kyma-project/istio/blob/main/internal/istiooperator/istio-operator.yaml#L160) is based on the Istio default format enhanced with the attributes relevant for identifying the related trace context conforming to the [w3c-tracecontext](https://www.w3.org/TR/trace-context/) protocol. See [Traces](traces-f98cda5.md) for details. See [Istio tracing](https://kyma-project.io/#/telemetry-manager/user/03-traces?id=istio) on how to enable trace context propagation with Istio.

> ### Caution:  
> Enabling access logs may drastically increase logs volume and quickly fill up your log storage.

<a name="task_iy3_mmf_scc"/>

<!-- task\_iy3\_mmf\_scc -->

## Configuring Istio Access Logs for a Namespace



<a name="task_iy3_mmf_scc__steps-unordered_rnp_l4f_scc"/>

## Procedure

-   Use Kyma dashboard

    1.  Go to the namespace for which you want to configure Istio access logs.

    2.  Go to *Istio \> Telemetries*.

    3.  Choose *Create*.

    4.  Provide a name, for example, *access-config*.

    5.  Choose *Create*.


-   Use kubectl

    1.  Export the name of the namespace for which you want to configure Istio access logs.

        ```
        export YOUR_NAMESPACE=namespace-name
        ```

    2.  To apply the configuration, run:

        ```
        cat <<EOF | kubectl apply -f -
        apiVersion: telemetry.istio.io/v1
        kind: Telemetry
        metadata:
          name: access-config
          namespace: $YOUR_NAMESPACE
        spec:
          accessLogging:
            - providers:
              - name: stdout-json
        EOF
        ```

    3.  To verify that the resource is applied, run:

        ```
        kubectl -n $YOUR_NAMESPACE get telemetries.telemetry.istio.io
        
        ```



<a name="task_gfp_5nf_scc"/>

<!-- task\_gfp\_5nf\_scc -->

## Configuring Istio Access Logs for a Selective Workload

To configure label-based selection of workloads, use a [selector](https://istio.io/latest/docs/reference/config/type/workload-selector/#WorkloadSelector).



<a name="task_gfp_5nf_scc__steps-unordered_br5_m4f_scc"/>

## Procedure

-   Use Kyma dashboard

    1.  Go to the namespace of the workload for which you want to configure Istio access logs.

    2.  Go to *Istio \> Telemetries*.

    3.  Choose *Create*.

    4.  Switch to the YAML section and paste the following configuration into the editor.

        ```
        apiVersion: telemetry.istio.io/v1
        kind: Telemetry
        metadata:
          name: access-config
          namespace: {your-namespace}
        spec:
          selector:
            matchLabels:
              service.istio.io/canonical-name: {your-label}
          accessLogging:
            - providers:
              - name: stdout-json
        ```

    5.  Replace *\{your-namespace\}* with the name of the workload's namespace and *\{your-label\}* with the name of the workloads' label.

    6.  Choose *Create*.


-   Use kubectl

    1.  Export the name of the workloads' namespace and the workloads' label as environment variables.

        ```
        export YOUR_NAMESPACE={namespace-name}
        export YOUR_LABEL={label}
        ```

    2.  To apply the configuration, run:

        ```
        cat <<EOF | kubectl apply -f -
        apiVersion: telemetry.istio.io/v1
        kind: Telemetry
        metadata:
          name: access-config
          namespace: $YOUR_NAMESPACE
        spec:
          selector:
            matchLabels:
              service.istio.io/canonical-name: $YOUR_LABEL
          accessLogging:
            - providers:
              - name: stdout-json
        EOF
        ```

    3.  To verify that the resource is applied, run:

        ```
        kubectl -n $YOUR_NAMESPACE get telemetries.telemetry.istio.io
        
        ```



<a name="task_et1_wnf_scc"/>

<!-- task\_et1\_wnf\_scc -->

## Configuring Istio Access Logs for a Selecitve Gateway

Instead of enabling the access logs for all the individual proxies of the workloads you have, you can enable the logs for the proxy used by the related Istio Ingress Gateway.



<a name="task_et1_wnf_scc__steps-unordered_trq_vd1_tcc"/>

## Procedure

-   Use Kyma dashboard

    1.  Go to the `istio-system`.

    2.  Go to *Istio \> Telemetries*.

    3.  Choose *Create*.

    4.  Switch to the YAML section and paste the following configuration into the editor.

        ```
        apiVersion: telemetry.istio.io/v1
        kind: Telemetry
        metadata:
          name: access-config
          namespace: istio-system
        spec:
          selector:
            matchLabels:
              istio: ingressgateway
          accessLogging:
            - providers:
              - name: stdout-json
        ```

    5.  Choose *Create*.


-   Use kubectl

    1.  To apply the configuration, run:

        ```
        cat <<EOF | kubectl apply -f -
        apiVersion: telemetry.istio.io/v1
        kind: Telemetry
        metadata:
          name: access-config
          namespace: istio-system
        spec:
          selector:
            matchLabels:
              istio: ingressgateway
          accessLogging:
            - providers:
              - name: stdout-json
        EOF
        ```

    2.  To verify that the resource is applied, run:

        ```
        kubectl -n istio-system get telemetries.telemetry.istio.io
        
        ```



<a name="task_vbw_xnf_scc"/>

<!-- task\_vbw\_xnf\_scc -->

## Configuring Istio Access Logs for the Entire Mesh

Enable access logs for all individual proxies of all your workloads and Istio Ingress Gateways.



<a name="task_vbw_xnf_scc__steps-unordered_w4p_pg1_tcc"/>

## Procedure

-   Use Kyma dashboard

    1.  Go to the `istio-system`.

    2.  Go to *Istio \> Telemetries*.

    3.  Choose *Create*.

    4.  Switch to the YAML section and paste the following configuration into the editor.

        ```
        apiVersion: telemetry.istio.io/v1
        kind: Telemetry
        metadata:
          name: access-config
          namespace: istio-system
        spec:
          accessLogging:
            - providers:
              - name: stdout-json
        ```

    5.  Select *Create*.


-   Use kubectl

    1.  To apply the configuration, run:

        ```
        cat <<EOF | kubectl apply -f -
        apiVersion: telemetry.istio.io/v1
        kind: Telemetry
        metadata:
          name: access-config
          namespace: istio-system
        spec:
          accessLogging:
            - providers:
              - name: stdout-json
        EOF
        ```

    2.  To verify that the resource is applied, run:

        ```
        kubectl -n istio-system get telemetries.telemetry.istio.io
        
        ```


