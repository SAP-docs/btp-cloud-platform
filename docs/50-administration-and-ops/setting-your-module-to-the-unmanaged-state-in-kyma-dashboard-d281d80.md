<!-- loiod281d803c7d946f4adcc28ee72700119 -->

# Setting Your Module to the Unmanaged State in Kyma Dashboard

In some cases, for example, for testing, you may need to modify your module beyond what is supported by its configuration. By default, when a module is in the managed state, Kyma Control Plane governs its Kubernetes resources, reverting any manual changes during the next reconciliation loop. To modify Kubernetes objects directly without them being reverted, you must set the module to the unmanaged state. In this state, reconciliation is disabled, ensuring your manual changes are preserved.



## Context

Follow this procedure to set your module to the unmanaged state.

> ### Caution:  
> Setting your module to the unmanaged state may lead to instability and data loss within your cluster. It may also be impossible to revert the changes. In addition, we don't guarantee any service level agreement \(SLA\) or provide updates and maintenance for the module.



## Procedure

1.  Log in to Kyma dashboard. The URL is in the Overview section of your subaccount.

2.  Choose *Modify Modules*, and go to the *Edit* tab.

3.  Uncheck the *Managed* checkbox under your module.

4.  Save the changes.




<a name="loiod281d803c7d946f4adcc28ee72700119__result_s1l_jxn_22c"/>

## Results

In the *View* tab, your module should be now in the `Unmanaged` state.



<a name="loiod281d803c7d946f4adcc28ee72700119__postreq_usj_4xn_22c"/>

## Next Steps

To bring your module back to the managed state, go to the *Edit* tab, check the *Managed* box under your module, and save changes.

> ### Caution:  
> Depending on the introduced changes, bringing back the module to the managed state might not be possible.

