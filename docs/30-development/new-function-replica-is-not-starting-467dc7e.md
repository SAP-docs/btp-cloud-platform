<!-- loio467dc7e9251d4215b158bff48dbb2bc1 -->

# New Function Replica is Not Starting



## Symptom

After migration to Serverless 1.9.3, some of the Functions show `Running=False` condition.

```

kubectl get function -A
NAMESPACE   NAME                        CONFIGURED   RUNNING   RUNTIME    VERSION   AGE
foo         function1                   True         True      nodejs22   2         2d
foo         function2                   True         True      nodejs22   3         2d
foo         function3                   True         False     nodejs22   2         2d
foo         function4                   True         False     nodejs22   3         2d

```



## Cause

With Serverless 1.9.3, we introduced [Serverless Buildless Mode](serverless-buildless-mode-dc25fff.md), which removes the in-cluster image build step. This reduces overall resource usage and speeds up delivery. As a result, dependency resolution \(`pip install`/`npm install`\) now happens at Function Pod startup. During this brief initialization phase, the Pod may require slightly more CPU and memory. If the Function’s resource limits are very low \(for example, custom-defined strict memory/CPU limits using `resourceConfiguration`\), the Pod can be OOMKilled by Kubernetes.



## Solution

Increase the resource limits in `spec.resourceConfiguration.function` or use a [larger preset](https://kyma-project.io/external-content/serverless/docs/user/technical-reference/07-80-available-presets.html), especially for Functions with multiple or heavy dependencies.

```

apiVersion: serverless.kyma-project.io/v1alpha2
kind: Function
metadata:
  labels:
    app.kubernetes.io/name: function3
  name: function3
  namespace: foo
  uid: ...
spec:
...
  resourceConfiguration:
    function:
      resources:
        limits:
          cpu: 100m # needs increasing
          memory: 64Mi
        requests:
          cpu: 50m # needs increasing
          memory: 32Mi

```

To learn how to specify resources per Function, see [Function](https://kyma-project.io/external-content/serverless/docs/user/resources/06-10-function-cr.html). To learn how to configure the default resource preset for all Functions, see [Configuring Serverless](configuring-serverless-b40a119.md).

