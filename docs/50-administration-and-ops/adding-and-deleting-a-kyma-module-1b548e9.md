<!-- loio1b548e9ad4744b978b8b595288b0cb5c -->

# Adding and Deleting a Kyma Module

To use a Kyma module, you must add it first. Use Kyma dashboard or Kyma CLI to do that. If you don't need the module anymore, delete it to save resources.



## Context

> ### Tip:  
> -   To see which modules you have in your cluster, go to Kyma dashboard and under *Cluster Overview*, choose *Modify Modules*.
> 
> -   If you prefer Kyma CLI, run `kyma module list`.

<a name="task_ux4_wxz_bfc"/>

<!-- task\_ux4\_wxz\_bfc -->

## Adding a Kyma Module



## Context



## Procedure

-   Use Kyma dashboard

    1.  Go to Kyma dashboard. The URL is in the Overview section of your subaccount.

    2.  Choose *Modify Modules* \> *Add*.

    3.  In the *Add Modules* section, check the modules you want to add, and select *Add*.

    4.  **Optional:** At the module level, you can overwrite the default release channel for the modules you are adding. Under the *Advanced* options, choose your preferred release channel.


    This process may take a while, depending on the number of modules. The operation was successful when the module status changes to ***READY***.

-   Use Kyma CLI

    1.  Check the list of modules that are available to be added:

        ```
        kyma module catalog
        ```

    2.  Add a new module:

        -   To add a new module with the default configuration, use the following command:

            ```
            kyma module add {MODULE-NAME} --default-cr
            ```

        -   To add a module with your specific configuration, create a YAML file containing your module custom resource \(CR\) settings, and use the`--cr-path={CR-FILEPATH}` flag:

            ```
            kyma module add {MODULE-NAME} --cr-path={CR-FILEPATH}
            
            ```

        -   To add a module with the specified release channel, use the `-c {CHANNEL-NAME}` flag:

            ```
            kyma module add {MODULE-NAME} -c {CHANNEL-NAME} --default-cr
            
            ```


        To see if your module is added, run the following command.

        ```
        kyma module list
        ```



**Related Information**  


[Kyma Dashboard](../10-concepts/kyma-dashboard-482ae2f.md "Use Kyma dashboard to access various features and functionalities of SAP BTP, Kyma runtime.")

[Kyma CLI](../10-concepts/kyma-cli-292454b.md "Kyma CLI is an essential tool for application developers who want to get started quickly and efficiently with SAP BTP, Kyma runtime. Designed to streamline workflows, it simplifies complex tasks, enabling developers to deploy and manage applications easily.")

<a name="task_o3l_vg1_cfc"/>

<!-- task\_o3l\_vg1\_cfc -->

## Deleting a Kyma Module



## Procedure

-   Use Kyma dashboard

    1.  Go to Kyma dashboard. The URL is in the Overview section of your subaccount.

    2.  Choose *Modify Modules*, and delete your module.


-   Use Kyma CLI

    1.  Check the list of installed modules:

        ```
        kyma module list
        ```

    2.  To delete your module, use the following command:

        ```
        kyma module delete {MODULE-NAME}
        ```

        You should see the following message:

        ```
        {MODULE-NAME} module disabled
        ```



**Related Information**  


[Kyma Dashboard](../10-concepts/kyma-dashboard-482ae2f.md "Use Kyma dashboard to access various features and functionalities of SAP BTP, Kyma runtime.")

[Kyma CLI](../10-concepts/kyma-cli-292454b.md "Kyma CLI is an essential tool for application developers who want to get started quickly and efficiently with SAP BTP, Kyma runtime. Designed to streamline workflows, it simplifies complex tasks, enabling developers to deploy and manage applications easily.")

