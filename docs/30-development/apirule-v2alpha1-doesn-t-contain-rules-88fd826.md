<!-- loio88fd826444b14f8d9424ca856613c141 -->

# APIRule `v2alpha1` Doesn't Contain Rules



<a name="loio88fd826444b14f8d9424ca856613c141__section_emq_cl5_gfc"/>

## Symptom

An APIRule custom resource \(CR\) does not contain the `rules` field, for example:

```
kubectl get apirules.v2alpha1.gateway.kyma-project.io -n $NAMESPACE $APIRULE_NAME -o yaml
```

```
apiVersion: gateway.kyma-project.io/v2alpha1
kind: APIRule
metadata:
  name: httpbin
  namespace: test
spec:
  gateway: kyma-system/kyma-gateway
  hosts:
    - httpbin.local.kyma.dev
  service:
    name: httpbin
    namespace: test
    port: 8000
status:
  lastProcessedTime: "2025-04-25T11:16:11Z"
  state: Ready
```



<a name="loio88fd826444b14f8d9424ca856613c141__section_zzc_dl5_gfc"/>

## Cause

The APIRule was originally created using version `v1beta1`, and you haven’t yet migrated it to version `v2`.

To display the resource in version `v2alpha1`, a conversion from `v1beta1` to `v2alpha1` is performed. This conversion only affects the displayed resource’s textual format and does not modify the resource in the cluster. If the full conversion is possible, the `rules` field is presented in the output. However, if the conversion cannot be completed, the rules are missing, and the original rules are stored in the resource’s annotations.



<a name="loio88fd826444b14f8d9424ca856613c141__section_g12_dl5_gfc"/>

## Solution

Specify explicitly `v1beta1` version when requesting the APIRule resource:

```
kubectl get apirules.v1beta1.gateway.kyma-project.io -n $NAMESPACE $APIRULE_NAME -o yaml
```

