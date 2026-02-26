<!-- loio123c96567f0f461599b416e8b457d9ce -->

# Configuring Logging

Learn how to configure logging for the Serverless components.



## Prerequisites

You have the [kubectl](https://kubernetes.io/docs/tasks/tools/) installed.

<a name="concept_bzl_4gl_k3c"/>

<!-- concept\_bzl\_4gl\_k3c -->

## Supported Log Levels

From the least to the most verbose: `fatal`, `panic`, `dpanic`, `error`, `warn`, `info` \(default\), `debug`.

<a name="concept_gqj_sgl_k3c"/>

<!-- concept\_gqj\_sgl\_k3c -->

## Supported Log Formats

The supported log formats are the following:

-   `json` - Structured JSON format \(default\)
-   `console` - Human-readable console format

<a name="concept_ehh_hhl_k3c"/>

<!-- concept\_ehh\_hhl\_k3c -->

## Configuring Serverless Controller

To update the log configuration, modify the Serverless custom resource \(CR\) in the `kyma-system` namespace.

> ### Note:  
> The `logLevel` changes are applied dynamically without restarting the Serverless Pods. The `logFormat` changes automatically restart the Serverless Pods to apply the new format.

To change the log level, run:

```
kubectl patch serverless -n kyma-system default --type merge -p '{"spec":{"logLevel":"debug"}}'
```

To change the log format, run:

```
kubectl patch serverless -n kyma-system default --type merge -p '{"spec":{"logFormat":"console"}}'
```

To change the log level and format, run:

```
kubectl patch serverless -n kyma-system default --type merge -p '{"spec":{"logLevel":"debug","logFormat":"console"}}'
```

To verify the change, run:

```
kubectl logs -n kyma-system -l app.kubernetes.io/name=serverless
```

<a name="concept_z32_mkl_k3c"/>

<!-- concept\_z32\_mkl\_k3c -->

## Configuring Serverless Operator

Update the log configuration in the `serverless-operator-log-config` ConfigMap in the `kyma-system` namespace.

> ### Note:  
> You can't dynamically change the log format for the Serverless Operator. If you want to change it, update the ConfigMap and restart the Pods.

To change the log level, run:

```
kubectl patch configmap serverless-operator-log-config -n kyma-system --type merge -p '{"data":{"log-config.yaml":"logLevel: debug"}}'
```

To change the log level and format, run:

```
kubectl patch configmap serverless-operator-log-config -n kyma-system --type merge -p '{"data":{"log-config.yaml":"logLevel: debug\nlogFormat: console"}}'
```

To verify the change, run:

```
kubectl logs -n kyma-system -l control-plane=operator
```

