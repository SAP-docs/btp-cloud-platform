<!-- loiode724afc31e64476ae0a2884b2804840 -->

# APIRule v2 Contains a Changed Status Schema



<a name="loiode724afc31e64476ae0a2884b2804840__section_e3b_rw4_ffc"/>

## Symptom

There is a changed `status` schema in an APIRule custom resource \(CR\), for example:

```
kubectl get apirules.gateway.kyma-project.io -n $NAMESPACE $APIRULE_NAME -o yaml
```

```
...
status:
  lastProcessedTime: "2025-04-25T11:16v:11Z"
  state: Ready
```



<a name="loiode724afc31e64476ae0a2884b2804840__section_enc_zw4_ffc"/>

## Cause

The schema of the **status.state** field in the `v2` APIRule CR introduces a unified approach, similar to the one used in the API Gateway CR. The possible states of the **status.state** field are `Ready`, `Warning`, `Error`, `Processing`, or `Deleting`.



<a name="loiode724afc31e64476ae0a2884b2804840__section_xjc_hx4_ffc"/>

## Solution

To get the APIRule in its original version, run:

```
kubectl get apirules.v1beta1.gateway.kyma-project.io -n $NAMESPACE $APIRULE_NAME -o yaml
```

You get an output similar to this one:

```
...
status:
APIRuleStatus:
  code: OK
accessRuleStatus:
  code: OK
lastProcessedTime: "2025-04-25T11:16:11Z"
observedGeneration: 1
virtualServiceStatus:
  code: OK  
```

