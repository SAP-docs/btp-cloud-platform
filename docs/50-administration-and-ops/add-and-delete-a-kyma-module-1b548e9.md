<!-- loio1b548e9ad4744b978b8b595288b0cb5c -->

# Add and Delete a Kyma Module

To use a Kyma module, you must add it first. Use Kyma dashboard or kubectl to do that. If you don't need the module anymore, delete it to save resources.

<a name="loio83744213890d4efe979d72ce706e1115"/>

<!-- loio83744213890d4efe979d72ce706e1115 -->

## Add and Delete a Kyma Module Using Kyma Dashboard

Use Kyma dashboard to add and delete a Kyma module.



<a name="loio83744213890d4efe979d72ce706e1115__context_mls_vrz_2xb"/>

## Context

Follow this procedure to easily add a module from the dashboard's *Cluster Details* view.



<a name="loio83744213890d4efe979d72ce706e1115__steps_nls_vrz_2xb"/>

## Procedure

1.  Log in to Kyma dashboard. The URL is in the *Overview* section of your subaccount.

2.  Choose *Modify Modules*, and select *Add*.

3.  In the *Add Modules* section, check the modules you want to add, and select *Add*.




<a name="loio83744213890d4efe979d72ce706e1115__result_vlq_51k_3xb"/>

## Results

This process may take a while, depending on the number of modules. The operation was successful when the module status changes to ***READY***.



<a name="loio83744213890d4efe979d72ce706e1115__postreq_plv_fkz_2xb"/>

## Next Steps

-   To configure your module, use the module CR that you can find in the module repository.

-   To delete a module, choose *Modify Modules*, and click on the trash icon next to the module you want to delete.


<a name="loio88a8e99e4be945398dae2baa69f8ad30"/>

<!-- loio88a8e99e4be945398dae2baa69f8ad30 -->

## Add and Delete a Kyma Module Using kubectl

Use kubectl to add or delete a Kyma module in the default channel.



<a name="loio88a8e99e4be945398dae2baa69f8ad30__context_rvd_zqz_2xb"/>

## Context

To add a module using [kubectl](https://kubernetes.io/docs/reference/kubectl/), perform the following steps:



<a name="loio88a8e99e4be945398dae2baa69f8ad30__steps_svd_zqz_2xb"/>

## Procedure

1.  Run the following command:

    ```
    kubectl edit kyma default -n kyma-system
    ```

2.  In the editor, add a module on your cluster in `spec.modules` by adding the module's name:

    ```
    spec:
      modules:
        - name: {NAME_OF_THE_MODULE}
    
    ```

3.  Save the changes.

    You should see the following message:

    ```
    kyma.operator.kyma-project.io/default edited
    ```




<a name="loio88a8e99e4be945398dae2baa69f8ad30__postreq_edw_skz_2xb"/>

## Next Steps

-   To configure your module, edit the module CR.

-   To delete a module, remove its name from the editor.


**Related Information**  


[Kyma's Modular Approach](../10-concepts/kyma-s-modular-approach-95a4101.md "With Kyma's modular approach, you can install only the modules you need, instead of a predefined set of components.")

[Kyma Release Channels](../10-concepts/kyma-s-modular-approach-95a4101.md#loio95a410144d7c449687c957da0cc43a0d__section_kyma_release_channels)

[Kyma Modules](../10-concepts/kyma-modules-0dda141.md "With Kyma's modular approach, you can install just the modules you need, instead of a predefined set of components.")

