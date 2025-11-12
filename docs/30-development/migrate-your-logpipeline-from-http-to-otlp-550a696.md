<!-- loio550a696a5be641898303b2c79cec72ed -->

# Migrate Your LogPipeline From HTTP to OTLP

To use the OpenTelemetry Protocol \(OTLP\) for sending logs, you must migrate your `LogPipeline` from the `http` output to the `otlp` output. With OTLP, you can correlate logs with traces and metrics, collect logs pushed directly from applications, and use features available only for the OTLP-based stack.



<a name="loio550a696a5be641898303b2c79cec72ed__prereq_w5p_g4f_pgc"/>

## Prerequisites

-   You have an active Kyma cluster with the Telemetry module added.

-   You have one or more `LogPipeline` resources that use the `http` output.

-   Your observability backend has an OTLP ingestion endpoint.




## Context

When you want to migrate to the `otlp` output, create a new `LogPipeline`. To prevent data loss, run it in parallel with your existing pipeline. After verifying that the new pipeline works correctly, you can delete the old one.

You can't modify an existing `LogPipeline` to change its output type. You must create a new resource.



## Procedure

1.  Create a new `LogPipeline` that uses the `otlp` output.

    Pay special attention to the following settings \(for details, see [Integrate With Your OTLP Backend](integrate-with-your-otlp-backend-e726417.md)\):

    -   Endpoint URL: Use the OTLP-specific ingestion endpoint from your observability backend. This URL is different from the one used for the legacy `http` output.

    -   Protocol: The `otlp` output defaults to the gRPC protocol. If your backend uses HTTP, you must include the protocol in the endpoint URL \(for example, `https://my-otlp-http-endpoint:4318`\).

    -   Authentication: The OTLP endpoint often uses different credentials or API permissions than your previous log ingestion endpoint. Verify that your credentials have the necessary permissions for OTLP log ingestion.


    ```
    apiVersion: telemetry.kyma-project.io/v1alpha1
    kind: LogPipeline
    metadata:
      name: <my-otlp-pipeline>
    spec:
      output:
        otlp:
          endpoint:
            value: "<my-backend>:4317"
    ```

2.  **Optional:** To enrich logs with Pod labels, configure the central `Telemetry` resource \([Telemetry CRD](https://kyma-project.io/#/telemetry-manager/user/resources/01-telemetry)\).

    In contrast to a Fluent Bit `LogPipeline`, the `otlp` output doesn't automatically add all Pod labels. To continue enriching logs with specific labels, you must explicitly enable it in the `spec.enrichments.extractPodLabels` field.

    > ### Note:  
    > Enrichment with Pod annotations is no longer supported.

3.  Deploy the new `LogPipeline`:

    ```
    kubectl apply -f logpipeline.yaml
    ```

4.  Check that the new `LogPipeline` is healthy:

    ```
    kubectl get logpipeline <my-otlp-pipeline>
    ```

5.  Check your observability backend to confirm that log data is arriving.

6.  Delete the old `LogPipeline`:

    ```
    kubectl delete logpipeline <my-old-pipeline>
    ```




## Results

Your cluster now sends logs exclusively through your new OTLP-based `LogPipeline`. Your enrichment logic is preserved.

