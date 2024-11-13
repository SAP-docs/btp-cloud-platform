<!-- loiobf80b705e9514bbc8aefed7f96c0456a -->

# Reverting the Istio Module's Deletion

Follow the steps outlined in this troubleshooting guide if you unintentionally deleted the Istio module and want to restore the cluster to its normal state without losing any resources created in the cluster.



<a name="loiobf80b705e9514bbc8aefed7f96c0456a__section_rx5_mnd_5cc"/>

## Symptom

The Istio custom resource \(CR\) is in the ***Warning*** state. The condition of type `Ready` is set to ***false*** with the reason ***IstioCustomResourcesDangling***. To verify this, run the command:

```
kubectl get istio default -n kyma-system -o jsonpath='{.status.conditions[0]}'
```

You get an output similar to this:

```
{"lastTransitionTime":"2024-09-26T18:23:00Z","message":"Istio deletion blocked because of existing Istio custom resources","reason":"IstioCustomResourcesDangling","status":"False","type":"Ready"}
```

> ### Note:  
> If you intended to delete the Istio module, the symptoms described in this document are expected, and you must clean up the remaining resources yourself. To check which resources are blocking the deletion, see the logs of the `istio-controller-manager` container.



<a name="loiobf80b705e9514bbc8aefed7f96c0456a__section_t2b_nnd_5cc"/>

## Cause

The Istio module wasn't completely removed because related resources still exist in the cluster.

For example, the issue occurs when you delete Istio, but there are still `VirtualService` resources either created by you or installed by another Kyma component or module. In such cases, the hooked finalizer pauses the deletion of Istio until you remove all the related resources. This blocking deletion strategy is intentionally designed and is enabled by default for the Istio module.



<a name="loiobf80b705e9514bbc8aefed7f96c0456a__section_evb_l3g_xcc"/>

## Solution



### Use Kyma dashboard.

1.  In the *Cluster Details* section, select *Modify Modules*.
2.  Select the Istio module.
3.  Choose *Edit*.
4.  Switch to the *YAML* section.
5.  To remove the finalizers from the Istio custom resource, delete the following lines:

    ```
    finalizers:
        - istios.operator.kyma-project.io/istio-installation
    ```

    When the finalizers are removed, the Istio module is deleted. All the other resources remain in the cluster.

6.  Choose *Save*.
7.  Add the Istio module again.

When you re-add the Istio module, its reconciliation is reinitiated. The Istio CR returns to the ***Ready*** state within a few seconds.



### Use kubectl.

1.  To edit the Istio CR, run:

    ```
    kubectl edit istio -n kyma-system default
    ```

2.  To remove the finalizers from the Istio custom resource, delete the following lines:

    ```
    finalizers:
        - istios.operator.kyma-project.io/istio-installation
    ```

    When the finalizers are removed, the Istio module is deleted. All the other resources remain in the cluster.

3.  Save the changes.
4.  Add the Istio module again.

When you re-add the Istio module, its reconciliation is reinitiated. The Istio CR returns to the ***Ready*** state within a few seconds.

