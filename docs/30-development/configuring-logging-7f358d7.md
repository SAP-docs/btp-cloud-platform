<!-- loio7f358d7f19bf48ed9918a715d1b166fb -->

# Configuring Logging

Learn how to configure logging for Keda Manager and the Keda module components.



## Prerequisites

You have the [kubectl](https://kubernetes.io/docs/tasks/tools/) installed.

<a name="concept_mlp_kgd_k3c"/>

<!-- concept\_mlp\_kgd\_k3c -->

## Supported Log Levels

From the least to the most verbose: `fatal`, `panic`, `dpanic`, `error`, `warn`, `info` \(default\), `debug`.

<a name="concept_vf2_qgd_k3c"/>

<!-- concept\_vf2\_qgd\_k3c -->

## Supported Log Formats

The supported log formats are the following:

-   `json` - Structured JSON format \(default\)
-   `console` \(or `text`\) - Human-readable console format

<a name="concept_zgd_xgd_k3c"/>

<!-- concept\_zgd\_xgd\_k3c -->

## Configure Keda Manager Logging

Keda Manager \(`keda-manager`\) supports dynamic log-level reconfiguration using a ConfigMap. Changes take effect without requiring a Pod restart.

```
# Change log level only
kubectl patch configmap keda-log-configmap -n kyma-system --type merge -p '{"data":{"log-config.yaml":"logLevel: debug"}}'

# Change both level and format
kubectl patch configmap keda-log-configmap -n kyma-system --type merge -p '{"data":{"log-config.yaml":"logLevel: debug\nlogFormat: json"}}'
```

To verify the change, run:

```
kubectl logs -n kyma-system -l app.kubernetes.io/name=keda-manager
```

<a name="concept_wxb_jhd_k3c"/>

<!-- concept\_wxb\_jhd\_k3c -->

## Configure the Keda Module Components Logging

> ### Remember:  
> Applying logging configuration changes to the `operator`, `metrics-server`, and `admission-webhooks` components triggers a restart to apply the new settings.



## Supported Time Encodings

The supported time encodings are the following:

-   `rfc3339` - RFC3339 format \(default\): `2006-01-02T15:04:05Z07:00`
-   `rfc3339nano` - RFC3339 with nanoseconds: `2006-01-02T15:04:05.999999999Z07:00`
-   `iso8601` - ISO8601 format: `2006-01-02T15:04:05.000Z0700`
-   `epoch` - Unix timestamp in seconds
-   `millis` - Unix timestamp in milliseconds
-   `nano` - Unix timestamp in nanoseconds



## Configuration

Update the Keda custom resource to configure logging for the Keda module components.

```
apiVersion: operator.kyma-project.io/v1alpha1
kind: Keda
metadata:
  name: default
  namespace: kyma-system
spec:
  logging:
    operator:
      level: "debug"
      format: "json"
      timeEncoding: "rfc3339"
    metricServer:
      level: "info"
      format: "json"
      timeEncoding: "rfc3339"
    admissionWebhook:
      level: "info"
      format: "json"
      timeEncoding: "rfc3339"
```

> ### Note:  
> The zap logger used by the Keda module components \(`operator, metrics-apiserver, admission-webhooks`\) has the following fixed field names in JSON format that cannot be customized: `level`, `ts`, `logger`, `msg`, `caller`.



## Verify the Changes

-   Run the following command to check the `keda-operator` logs.

    ```
    kubectl logs -n kyma-system -l app=keda-operator
    ```

-   Run the following command to check the `keda-metrics-api-server` logs.

    ```
    kubectl logs -n kyma-system -l app=keda-operator-metrics-apiserver
    ```

-   Run the following command, to check the `keda-admission-webhooks` logs.

    ```
    kubectl logs -n kyma-system -l app=keda-admission-webhooks
    ```




## Limitations

The klog logs \(Kubernetes API server framework\) used by `keda-operator-metrics-apiserver` are always in text format, prefixed with `I`, `W`, `E` for Info, Warning, Error.

```
I0203 12:03:29.253333       1 requestheader_controller.go:180] Starting RequestHeaderAuthRequestController <- Actual log line
W0203 11:39:56.585970       1 this is a warning example
E0203 11:39:56.586030       1 this is an error example
```

**Related Information**  


[Configuring Keda Module](configuring-keda-module-3cc1f25.md "By default, the Keda module comes with the default configuration. You can change the configuration using the Keda CustomResourceDefinition (CRD). See how to configure the logging.level attribute, enable the Istio sidecar injection, change resource consumption, define custom annotations, or override the minimum TLS version.")

[KEDA Logs](https://keda.sh/docs/2.18/operate/cluster/#logs)

