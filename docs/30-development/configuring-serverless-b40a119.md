<!-- loiob40a11952da84394b430118082754e6c -->

# Configuring Serverless

By default, the Serverless module comes with the default configuration. You can change the configuration using the Serverless CustomResourceDefinition \(CRD\), which manages Serverless custom resource \(CR\).



<a name="loiob40a11952da84394b430118082754e6c__prereq_sdh_3wq_rfc"/>

## Prerequisites

-   You have the Serverless module added. See [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).

-   You have access to Kyma dashboard. Alternatively, to use CLI instructions, you must install [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl).




## Context

The Serverless CR is an API to configure the Serverless module. You can use it to perform the following actions:

-   Configuring trace endpoint.

-   Configuring Eventing endpoint.

-   Configuring the Function requeue duration.

-   Configuring the healthz liveness timeout.

-   Configuring the default runtime Pod preset

-   Configuring the log level.

-   Configuring the log format.

-   Disabling buildless mode.


The default configuration of the Serverless module is the following:

```
apiVersion: operator.kyma-project.io/v1alpha1
kind: Serverless
metadata:
  name: serverless-sample
spec: {}

```



## Procedure

1.  Go to Kyma dashboard. The URL is in the Overview section of your subaccount.

2.  Choose *Modify Modules*, and in the *View* tab, choose *serverless*.

3.  Go to *Edit*, and provide your configuration changes. You can use the *Form* or *YAML* tab.


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

<a name="concept_b1t_v1r_rfc"/>

<!-- concept\_b1t\_v1r\_rfc -->

## Configuring the Function Requeue Duration

By default, the Function associated with the default configuration will be requeued every 5 minutes.

```
   spec:
      functionRequeueDuration: 5m
```

<a name="concept_qtd_zcr_rfc"/>

<!-- concept\_qtd\_zcr\_rfc -->

## Configuring the healthz Liveness Timeout

By default, Function is considered unhealthy if the liveness health check endpoint does not respond within 10 seconds.

```
   spec:
      healthzLivenessTimeout: "10s"
```

<a name="concept_w4q_mdr_rfc"/>

<!-- concept\_w4q\_mdr\_rfc -->

## Configuring the Default Runtime Pod Preset

You can configure the default runtime Pod preset to be used.

```
   spec:
      defaultRuntimePodPreset: "M"
```

For more information on presets, [see Available Presets](https://kyma-project.io/external-content/serverless/docs/user/technical-reference/07-80-available-presets.html).

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

<a name="task_s5c_3nf_shc"/>

<!-- task\_s5c\_3nf\_shc -->

## Disabling Buildless Mode

Serverless buildless mode is enabled by default. To use the legacy image-building Serverless functionality, disable buildless mode through an annotation.



## Prerequisites

You have [kubectl](https://kubernetes.io/docs/reference/kubectl/) installed.

> ### Caution:  
> The legacy image-building mode is deprecated and will be removed in a future version of Serverless. This functionality is scheduled for removal and will no longer be available in upcoming releases.



## Procedure

1.  Edit the Serverless CR:

    `kubectl edit -n kyma-system serverlesses.operator.kyma-project.io default`

2.  In the `metadata` section, add `annotations`, and add the `serverless.kyma-project.io/buildless-mode: "disabled"` key-value pair in it, and save the changes.

    ```
       apiVersion: operator.kyma-project.io/v1alpha1
    kind: Serverless
    metadata:
      name: default
      namespace: kyma-system
      annotations:
        serverless.kyma-project.io/buildless-mode: "disabled"
    spec: {}
    
    ```

    You have disabled Serverless buildless mode.


