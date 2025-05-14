<!-- loioc07168072c8340ecbb392260cf52c165 -->

# Setting Your Module to the Unmanaged and Managed State

In some cases, for example, for testing, you may need to modify your module beyond what is supported by its configuration. By default, when a module is in the managed state, Kyma Control Plane governs its Kubernetes resources, reverting any manual changes during the next reconciliation loop. To modify Kubernetes objects directly without them being reverted, you must set the module to the unmanaged state. In this state, reconciliation is disabled, ensuring your manual changes are preserved.

<a name="task_qmd_tk1_cfc"/>

<!-- task\_qmd\_tk1\_cfc -->

## Setting Your Module to the Unmanaged State



## Procedure

-   Use Kyma dashboard

    1.  Go to Kyma dashboard. The URL is in the Overview section of your subaccount.

    2.  Choose *Modify Modules*, and go to the *Edit* tab.

    3.  In the *Form* view, uncheck the *Managed* checkbox under your module.

    4.  Save the changes.

        In the *View* tab, you see your module in the `Unmanaged` state.


-   Use Kyma CLI

    > ### Caution:  
    > The `alpha` group commands are still in development, which means their functions and API may be modified over time. We encourage you to explore them, but keep in mind that changes may occur.

    -   To set a module to the unmanaged state, use the following command:

        ```
        kyma alpha module unmanage {MODULE-NAME}
        ```


    You should see the following message:

    ```
    Module {MODULE-NAME} set to unmanaged
    ```


**Related Information**  


[Kyma Dashboard](../10-concepts/kyma-dashboard-482ae2f.md "Use Kyma dashboard to access various features and functionalities of SAP BTP, Kyma runtime.")

[Kyma CLI](../10-concepts/kyma-cli-292454b.md "Kyma CLI is an essential tool for application developers who want to get started quickly and efficiently with SAP BTP, Kyma runtime. Designed to streamline workflows, it simplifies complex tasks, enabling developers to deploy and manage applications easily.")

<a name="task_qww_pm1_cfc"/>

<!-- task\_qww\_pm1\_cfc -->

## Setting Your Module to the Managed State



## Procedure

-   Use Kyma dashboard

    1.  Go to Kyma dashboard. The URL is in the Overview section of your subaccount.

    2.  Choose *Modify Modules*, and go to the *Edit* tab.

    3.  In the *Form* view, check the *Managed* checkbox under your module.

    4.  Save the changes.

        In the *View* tab, you see your module in the `Ready` state.


-   Use Kyma CLI

    > ### Caution:  
    > The `alpha` group commands are still in development, which means their functions and API may be modified over time. We encourage you to explore them, but keep in mind that changes may occur.

    -   To set a module to the managed state, use the following command:

        ```
        kyma alpha module manage {MODULE-NAME}
        ```


    You should see the following message:

    ```
    Module {MODULE-NAME} set to managed
    ```


**Related Information**  


[Kyma Dashboard](../10-concepts/kyma-dashboard-482ae2f.md "Use Kyma dashboard to access various features and functionalities of SAP BTP, Kyma runtime.")

[Kyma CLI](../10-concepts/kyma-cli-292454b.md "Kyma CLI is an essential tool for application developers who want to get started quickly and efficiently with SAP BTP, Kyma runtime. Designed to streamline workflows, it simplifies complex tasks, enabling developers to deploy and manage applications easily.")

