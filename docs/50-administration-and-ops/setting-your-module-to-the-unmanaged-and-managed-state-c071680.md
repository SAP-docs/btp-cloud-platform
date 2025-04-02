<!-- loioc07168072c8340ecbb392260cf52c165 -->

# Setting Your Module to the Unmanaged and Managed State

In some cases, for example, for testing, you may need to modify your module beyond what is supported by its configuration. By default, when a module is in the managed state, Kyma Control Plane governs its Kubernetes resources, reverting any manual changes during the next reconciliation loop. To modify Kubernetes objects directly without them being reverted, you must set the module to the unmanaged state. In this state, reconciliation is disabled, ensuring your manual changes are preserved.

<a name="loiod281d803c7d946f4adcc28ee72700119"/>

<!-- loiod281d803c7d946f4adcc28ee72700119 -->

## Setting Your Module to the Unmanaged and Managed State using Kyma Dashboard

Use Kyma dashboard to set your module to the unmanaged state.



## Context

Follow this procedure to easily set your module to the unmanaged state from the dashboard's *Cluster Details* view.

> ### Caution:  
> Setting your module to the unmanaged state may lead to instability and data loss within your cluster. It may also be impossible to revert the changes. In addition, we don't guarantee any service level agreement \(SLA\) or provide updates and maintenance for the module.



## Procedure

1.  Go to Kyma dashboard. The URL is in the Overview section of your subaccount.

2.  Choose *Modify Modules*, and go to the *Edit* tab.

3.  In the *Form* view, uncheck the *Managed* checkbox under your module.

4.  Save the changes.




<a name="loiod281d803c7d946f4adcc28ee72700119__result_s1l_jxn_22c"/>

## Results

In the *View* tab, you see your module in the `Unmanaged` state.



<a name="loiod281d803c7d946f4adcc28ee72700119__postreq_usj_4xn_22c"/>

## Next Steps

To bring your module back to the managed state, go to the *Edit* tab, check the *Managed* box under your module, and save changes.

> ### Caution:  
> Depending on the introduced changes, bringing back the module to the managed state might not be possible.

<a name="loio2a0ba7160e5145688f1b8cc21f89651d"/>

<!-- loio2a0ba7160e5145688f1b8cc21f89651d -->

## Setting Your Module to the Unmanaged and Managed State in Kyma CLI

Use Kyma CLI to set your module to the unmanaged state.



<a name="loio2a0ba7160e5145688f1b8cc21f89651d__prereq_qvz_h3v_v2c"/>

## Prerequisites

You have Kyma CLI installed. For more information, see [Install Kyma CLI](../10-concepts/kyma-cli-292454b.md#loio292454b34bf543afa111dec20d9da434__section_xy1_41f_52c).



## Context

Set your module to the unmanaged state with a simple Kyma CLI command.

> ### Caution:  
> Setting your module to the unmanaged state may lead to instability and data loss within your cluster. It may also be impossible to revert the changes. In addition, we don't guarantee any service level agreement \(SLA\) or provide updates and maintenance for the module.



## Procedure

To set a module to the unmanaged state, use the following command:

```
kyma alpha module unmanage {MODULE-NAME}

```



<a name="loio2a0ba7160e5145688f1b8cc21f89651d__result_i1q_mgk_52c"/>

## Results

Your module is now in the unmanaged state.



<a name="loio2a0ba7160e5145688f1b8cc21f89651d__postreq_scs_tgk_52c"/>

## Next Steps

To bring your module back to the managed state, use the following command:

```
kyma alpha module manage {MODULE-NAME}

```

Even if the module is already in the managed state, you can change its policy by adding the optional flag `--policy {POLICY-NAME}`. The default policy is `CreateAndDelete`.

> ### Caution:  
> Depending on the introduced changes, bringing back the module to the managed state might not be possible.

