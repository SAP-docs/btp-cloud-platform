<!-- loiobc6c34804e1c4afca391516ecd0dac5e -->

# APIRule v2 Doesn't Contain Rules



<a name="loiobc6c34804e1c4afca391516ecd0dac5e__section_ds2_pzg_2fc"/>

## Symptom

An APIRule custom resource \(CR\) does not contain the `rules` field, for example:

```
kubectl get apirules.gateway.kyma-project.io -n $NAMESPACE $APIRULE_NAME -o yaml
```

```
apiVersion: gateway.kyma-project.io/v2
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



<a name="loiobc6c34804e1c4afca391516ecd0dac5e__section_aj3_qzg_2fc"/>

## Cause

The APIRule was originally created using version `v1beta1`, and you haven’t yet migrated it to version `v2`. Since the latest stable version of the APIRule in the Kubernetes API is now `v2`, running the `kubectl get` command without specifying a version of APIRule assumes version `v2`.

To display the resource in version `v2`, a conversion from `v1beta1` to `v2` is performed. This conversion only affects the displayed resource’s textual format and does not modify the resource in the cluster. If the full conversion is possible, the `rules` field is presented in the output. However, if the conversion cannot be completed, the rules are missing, and the original rules are stored in the resource’s annotations.



<a name="loiobc6c34804e1c4afca391516ecd0dac5e__section_sxj_qzg_2fc"/>

## Solution

Specify explicitly `v1beta1` version when requesting the APIRule resource:

```
kubectl get apirules.v1beta1.gateway.kyma-project.io -n $NAMESPACE $APIRULE_NAME -o yaml
```

