<!-- loiob40a11952da84394b430118082754e6c -->

# Configuring Serverless

By default, the Serverless module comes with the default configuration. You can change the configuration using the Serverless CustomResourceDefinition \(CRD\), which manages Serverless custom resource \(CR\).



<a name="loiob40a11952da84394b430118082754e6c__prereq_sdh_3wq_rfc"/>

## Prerequisites

-   You have the Serverless module added. See [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).

-   You have access to Kyma dashboard. Alternatively, to use CLI instructions, you must install [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl).




## Context

The Serverless CR is an API to configure the Serverless module. You can use it to perform the following actions:

-   Enable or disable the internal Docker registry.

-   Configure the external Docker registry.

-   Override endpoint for traces collected by the Serverless Functions.

-   Override endpoint for Eventing.

-   Override the target CPU utilization percentage.

-   Override the Function requeue duration.

-   Override the Function build executor arguments.

-   Override the Function build max simultaneous jobs.

-   Override the healthz liveness timeout.

-   Override the Function request body limit.

-   Override the Function timeout.

-   Override the default build Job preset.

-   Override the default runtime Pod preset.

-   Override the default log level.

-   Override the default log format.

-   Enable network policies.

-   Enable buildless mode of Serverless.


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



## Procedure

1.  Go to Kyma dashboard. The URL is in the Overview section of your subaccount.

2.  Choose *Modify Modules*, and in the *View* tab, choose *serverless*.

3.  Go to *Edit*, and provide your configuration changes. You can use the *Form* or *YAML* tab.


<a name="task_obs_wwq_rfc"/>

<!-- task\_obs\_wwq\_rfc -->

## Configuring Docker Registry

By default, Serverless uses PersistentVolume \(PV\) as the internal registry to store Docker images for Functions. The default storage size of a single volume is 20 GB. This internal registry is suitable for local development. Follow these steps to use the external Docker registry in Serverless:



## Procedure

1.  > ### Caution:  
    > If you use Serverless for production purposes, it is recommended that you use an external registry, such as Docker Hub, Artifact Registry, or Azure Container Registry \(ACR\).

    Create a Secret in the `kyma-system` namespace with the required data \(`username`, `password`, `serverAddress`, and `registryAddress`\):

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


<a name="concept_f2n_rzq_rfc"/>

<!-- concept\_f2n\_rzq\_rfc -->

## Configuring Trace Endpoint

By default, the Serverless operator checks if there is a trace endpoint available. If available, the detected trace endpoint is used as the trace collector URL in Functions. If no trace endpoint is detected, Functions are configured with no trace collector endpoint. You can configure a custom trace endpoint so that Function traces are sent to any tracing backend you choose. The currently used trace endpoint is visible in the Serverless CR status.

```
spec:
  tracing:
    endpoint: http://jaeger-collector.observability.svc.cluster.local:4318/v1/traces
```

<a name="concept_nz5_h1r_rfc"/>

<!-- concept\_nz5\_h1r\_rfc -->

## Configuring Eventing Endpoint

You can configure a custom Eventing endpoint to publish events sent from your Functions. The currently used trace endpoint is visible in the Serverless CR status. By default`http://eventing-publisher-proxy.kyma-system.svc.cluster.local/publish` is used.

```
spec:
  eventing:
    endpoint: http://eventing-publisher-proxy.kyma-system.svc.cluster.local/publish
```

<a name="concept_dyx_41r_rfc"/>

<!-- concept\_dyx\_41r\_rfc -->

## Configuring Target CPU Utilization Percentage

You can set a custom target threshold for CPU utilization. The default value is set to `50%`.

```
   spec:
      targetCPUUtilizationPercentage: 50
```

> ### Caution:  
> The `spec.targetCPUUtilizationPercentage` field is deprecated and will be removed in a future version of Serverless, where automatic HPA creation will be disabled.

<a name="concept_b1t_v1r_rfc"/>

<!-- concept\_b1t\_v1r\_rfc -->

## Configuring the Function Requeue Duration

By default, the Function associated with the default configuration will be requeued every 5 minutes.

```
   spec:
      functionRequeueDuration: 5m
```

<a name="concept_afc_cbr_rfc"/>

<!-- concept\_afc\_cbr\_rfc -->

## Configuring the Function Build Executor Arguments

Use this label to choose the [arguments](https://github.com/GoogleContainerTools/kaniko?tab=readme-ov-file#additional-flags) passed to the Function build executor, for example:

-   `--insecure` - executor operates in an insecure mode

-   `--skip-tls-verify` - executor skips the TLS certificate verification

-   `--skip-unused-stages` - executor skips any stages that aren't used for the current execution

-   `--log-format=text` - executor uses logs in a given format

-   `--cache=true` - enables caching for the executor

-   `--compressed-caching=false` - prevents tar compression for cached layers. This increases the runtime of the build, but decreases the memory usage, especially for large builds

-   `--use-new-run` - improves performance by avoiding the full filesystem snapshots


```
   spec:
      functionBuildExecutorArgs: "--insecure,--skip-tls-verify,--skip-unused-stages,--log-format=text,--cache=true,--use-new-run,--compressed-caching=false"
```

> ### Caution:  
> The `spec.functionBuildExecutorArgs` field is deprecated and will be removed in a future version of Serverless where Functions won't require building images.

<a name="concept_qyr_scr_rfc"/>

<!-- concept\_qyr\_scr\_rfc -->

## Configuring the Function Build Max Simultaneous Jobs

You can set a custom maximum number of simultaneous jobs which can run at the same time. The default value is set to `5`.

```
   spec:
      functionBuildMaxSimultaneousJobs: 5
```

> ### Caution:  
> The `spec.functionBuildMaxSimultaneousJobs` field is deprecated and will be removed in a future version of Serverless where Functions won't require building images.

<a name="concept_qtd_zcr_rfc"/>

<!-- concept\_qtd\_zcr\_rfc -->

## Configuring the healthz Liveness Timeout

By default, Function is considered unhealthy if the liveness health check endpoint does not respond within 10 seconds.

```
   spec:
      healthzLivenessTimeout: "10s"
```

<a name="concept_n1v_2dr_rfc"/>

<!-- concept\_n1v\_2dr\_rfc -->

## Configuring the Default Build Job Preset

You can configure the default build Job preset to be used.

```
   spec:
      defaultBuildJobPreset: "normal"
```

> ### Caution:  
> The `spec.defaultBuildJobPreset` field is deprecated and will be removed in a future version of Serverless where Functions won't require building images.

<a name="concept_w4q_mdr_rfc"/>

<!-- concept\_w4q\_mdr\_rfc -->

## Configuring the Default Runtime Pod Preset

You can configure the default runtime Pod preset to be used.

```
   spec:
      defaultRuntimePodPreset: "M"
```

For more information on presets, [see Available Presets](https://kyma-project.io/#/serverless-manager/user/technical-reference/07-80-available-presets).

<a name="concept_dml_sdr_rfc"/>

<!-- concept\_dml\_sdr\_rfc -->

## Configuring the Log Level

You can configure the desired log level to be used.

```
   spec:
      logLevel: "debug"

```

<a name="concept_h3q_wdr_rfc"/>

<!-- concept\_h3q\_wdr\_rfc -->

## Configuring the Log Format

You can configure the desired log format to be used.

```
   spec:
      logFormat: "yaml"

```

<a name="concept_pmj_b2r_rfc"/>

<!-- concept\_pmj\_b2r\_rfc -->

## Enabling Network Policies

You can enable built-in network policies to ensure that the necessary communication channels required by Serverless workloads remain functional, even on Kubernetes clusters where strict "deny-all" network policies are enforced. This allows Serverless components to operate correctly by permitting essential traffic while maintaining a secure cluster environment.

```
   spec:

      enableNetworkPolicies: true
```

<a name="concept_ulf_k2g_ggc"/>

<!-- concept\_ulf\_k2g\_ggc -->

## Enabling Buildless Mode

You can enable buildless mode in Serverless to skip the image build step for Functions, accelerating prototype development by eliminating the need to build and push custom Function images.

> ### Caution:  
> Buildless mode is a feature flag that you can enable through an annotation. Before enabling the feature, see [Serverless Buildless Mode](serverless-buildless-mode-dc25fff.md).

```
 annotations:
   serverless.kyma-project.io/buildless-mode: "enabled"

```

