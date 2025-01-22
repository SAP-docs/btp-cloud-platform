<!-- loio4a0ae14c2b8b4598998539d6ed25a7e5 -->

# Serverless Configuration

The Serverless module has its own operator \(Serverless Operator\). It watches the Serverless custom resource \(CR\) and reconfigures \(reconciles\) the Serverless workloads.

The Serverless CR is an API to configure the Serverless module. You can use it to perform the following actions:

-   Enable or disable the internal Docker registry

-   Configure the external Docker registry

-   Override endpoint for traces collected by the Serverless Functions

-   Override endpoint for Eventing

-   Override the target CPU utilization percentage

-   Override the Function requeue duration

-   Override the Function build executor arguments

-   Override the Function build max simultaneous jobs

-   Override the healthz liveness timeout

-   Override the Function request body limit

-   Override the Function timeout

-   Override the default build Job preset

-   Override the default runtime Pod preset


The default configuration of the Serverless module is the following:

```
apiVersion: operator.kyma-project.io/v1alpha1
kind: Serverless
metadata:
  name: serverless-sample
spec:
  dockerRegistry:
    enableInternal: true
```

> ### Caution:  
> The `spec.dockerRegistry` field is deprecated and will be removed in a future version of Serverless where Functions won't require building images.



<a name="loio4a0ae14c2b8b4598998539d6ed25a7e5__section_mwx_swv_4dc"/>

## Configure Docker Registry

By default, Serverless uses PersistentVolume \(PV\) as the internal registry to store Docker images for Functions. The default storage size of a single volume is 20 GB. This internal registry is suitable for local development.

> ### Remember:  
> If you use Serverless for production purposes, it is recommended that you use an external registry, such as Docker Hub, Artifact Registry, or Azure Container Registry \(ACR\).

Follow these steps to use the external Docker registry in Serverless:

1.  To use the external Docker registry create a Secret in the `kyma-system` namespace with the required data \(`username`, `password`, `serverAddress`, and `registryAddress`\):

    ```
    kubectl create secret generic my-registry-config \
        --namespace kyma-system \
        --from-literal=username={USERNAME} \
        --from-literal=password={PASSWORD} \
        --from-literal=serverAddress={SERVER_URL} \
        --from-literal=registryAddress={REGISTRY_URL}
    ```

    > ### Tip:  
    > In the case of Docker Hub, usually the Docker `registryAddress` is the same as the account name.

    Examples:

    -   Docker Hub

        ```
        kubectl create secret generic my-registry-config \
           --namespace kyma-system \
           --from-literal=username={USERNAME} \
           --from-literal=password={PASSWORD} \
           --from-literal=serverAddress=https://index.docker.io/v1/ \
           --from-literal=registryAddress={USERNAME}
        ```

    -   Artifact Registry

        ```
        kubectl create secret generic my-registry-config \
            --namespace kyma-system \
            --from-literal=username=_json_key \
            --from-literal=password={GCR_KEY_JSON} \
            --from-literal=serverAddress=gcr.io \
            --from-literal=registryAddress=gcr.io/{YOUR_GCR_PROJECT}
        ```

        For more information on how to set up authentication for Docker with Artifact Registry, see the [Artifact Registry documentation](https://cloud.google.com/artifact-registry/docs/docker/authentication#json-key).

    -   ACR

        ```
        kubectl create secret generic my-registry-config \
            --namespace kyma-system \
            --from-literal=username=00000000-0000-0000-0000-000000000000 \
            --from-literal=password={ACR_TOKEN} \
            --from-literal=serverAddress={AZ_REGISTRY_NAME}.azurecr.io \
            --from-literal=registryAddress={AZ_REGISTRY_NAME}.azurecr.io
        ```

        For more information on how to authenticate with ACR, see the [ACR documentation](https://learn.microsoft.com/en-us/azure/container-registry/container-registry-authentication?tabs=azure-cli#az-acr-login-with---expose-token).


2.  Reference the Secret in the Serverless CR:

    ```
    spec:
      dockerRegistry:
        secretName: my-registry-config 
    ```

    The URL of the currently used Docker registry is visible in the Serverless CR status.




<a name="loio4a0ae14c2b8b4598998539d6ed25a7e5__section_n4h_y3w_4dc"/>

## Configure Trace Endpoint

By default, the Serverless operator checks if there is a trace endpoint available. If available, the detected trace endpoint is used as the trace collector URL in Functions. If no trace endpoint is detected, Functions are configured with no trace collector endpoint. You can configure a custom trace endpoint so that Function traces are sent to any tracing backend you choose. The currently used trace endpoint is visible in the Serverless CR status.

```
spec:
  tracing:
    endpoint: http://jaeger-collector.observability.svc.cluster.local:4318/v1/traces
```



<a name="loio4a0ae14c2b8b4598998539d6ed25a7e5__section_mkc_cjw_4dc"/>

## Configure Eventing Endpoint

You can configure a custom Eventing endpoint to publish events sent from your Functions. The currently used trace endpoint is visible in the Serverless CR status. By default`http://eventing-publisher-proxy.kyma-system.svc.cluster.local/publish` is used.

```
spec:
  eventing:
    endpoint: http://eventing-publisher-proxy.kyma-system.svc.cluster.local/publish
```



<a name="loio4a0ae14c2b8b4598998539d6ed25a7e5__section_bdm_hjw_4dc"/>

## Configure Target CPU Utilization Percentage

You can set a custom target threshold for CPU utilization. The default value is set to `50%`.

```
   spec:
      targetCPUUtilizationPercentage: 50
```

> ### Caution:  
> The `spec.targetCPUUtilizationPercentage` field is deprecated and will be removed in a future version of Serverless, where automatic HPA creation will be disabled.



<a name="loio4a0ae14c2b8b4598998539d6ed25a7e5__section_lz5_4jw_4dc"/>

## Configure the Function Requeue Duration

By default, the Function associated with the default configuration will be requeued every 5 minutes.

```
   spec:
      functionRequeueDuration: 5m
```



<a name="loio4a0ae14c2b8b4598998539d6ed25a7e5__section_mlm_qjw_4dc"/>

## Configure the Function Build Executor Arguments

Use this label to choose the [arguments](https://github.com/GoogleContainerTools/kaniko?tab=readme-ov-file#additional-flags) passed to the Function build executor, for example:

-   `--insecure` - executor operates in an insecure mode

-   `--skip-tls-verify` - executor skips the TLS certificate verification

-   `--skip-unused-stages` - executor skips any stages that aren't used for the current execution

-   `--log-format=text` - executor uses logs in a given format

-   `--cache=true` - enables caching for the executor

-   `--compressed-caching=false` - prevents tar compression for cached layers. This increases the runtime of the build, but decreases the memory usage, especially for large builds.

-   `--use-new-run` - improves performance by avoiding the full filesystem snapshots


```
   spec:
      functionBuildExecutorArgs: "--insecure,--skip-tls-verify,--skip-unused-stages,--log-format=text,--cache=true,--use-new-run,--compressed-caching=false"
```

> ### Caution:  
> The `spec.functionBuildExecutorArgs` field is deprecated and will be removed in a future version of Serverless where Functions won't require building images.



<a name="loio4a0ae14c2b8b4598998539d6ed25a7e5__section_jjj_mkw_4dc"/>

## Configure the Function Build Max Simultaneous Jobs

You can set a custom maximum number of simultaneous jobs which can run at the same time. The default value is set to `5`.

```
   spec:
      functionBuildMaxSimultaneousJobs: 5
```

> ### Caution:  
> The `spec.functionBuildMaxSimultaneousJobs` field is deprecated and will be removed in a future version of Serverless where Functions won't require building images.



<a name="loio4a0ae14c2b8b4598998539d6ed25a7e5__section_rh5_hlw_4dc"/>

## Configure the healthz Liveness Timeout

By default, Function is considered unhealthy if the liveness health check endpoint does not respond within 10 seconds.

```
   spec:
      healthzLivenessTimeout: "10s"
```



<a name="loio4a0ae14c2b8b4598998539d6ed25a7e5__section_uxr_klw_4dc"/>

## Configure the Default Build Job Preset

You can configure the default build Job preset to be used.

```
   spec:
      defaultBuildJobPreset: "normal"
```

> ### Caution:  
> The `spec.defaultBuildJobPreset` field is deprecated and will be removed in a future version of Serverless where Functions won't require building images.



<a name="loio4a0ae14c2b8b4598998539d6ed25a7e5__section_egc_plw_4dc"/>

## Configure the Default Runtime Pod Preset

You can configure the default runtime Pod preset to be used.

```
   spec:
      defaultRuntimePodPreset: "M"
```

For more information on presets, [see Available Presets](https://kyma-project.io/#/serverless-manager/user/technical-reference/07-80-available-presets).

