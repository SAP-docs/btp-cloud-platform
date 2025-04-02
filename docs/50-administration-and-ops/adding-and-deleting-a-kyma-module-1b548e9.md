<!-- loio1b548e9ad4744b978b8b595288b0cb5c -->

# Adding and Deleting a Kyma Module

To use a Kyma module, you must add it first. Use Kyma dashboard or Kyma CLI to do that. If you don't need the module anymore, delete it to save resources.

<a name="loio83744213890d4efe979d72ce706e1115"/>

<!-- loio83744213890d4efe979d72ce706e1115 -->

## Adding and Deleting a Kyma Module Using Kyma Dashboard

Use Kyma dashboard to add and delete a Kyma module.



<a name="loio83744213890d4efe979d72ce706e1115__context_mls_vrz_2xb"/>

## Context

Follow this procedure to easily add a module from the dashboard's *Cluster Details* view.



<a name="loio83744213890d4efe979d72ce706e1115__steps_nls_vrz_2xb"/>

## Procedure

1.  Log in to Kyma dashboard. The URL is in the *Overview* section of your subaccount.

2.  Choose *Modify Modules*, and select *Add*.

3.  In the *Add Modules* section, check the modules you want to add, and select *Add*.

4.  **Optional:** At the module level, you can overwrite the default release channel for the modules you are adding: Under the *Advanced* options, choose your preferred release channel.




<a name="loio83744213890d4efe979d72ce706e1115__result_vlq_51k_3xb"/>

## Results

This process may take a while, depending on the number of modules. The operation was successful when the module status changes to ***READY***.



<a name="loio83744213890d4efe979d72ce706e1115__postreq_plv_fkz_2xb"/>

## Next Steps

-   To configure your module, use the module CR that you can find in the module repository.

-   To delete a module, choose *Modify Modules*, and click on the trash icon next to the module you want to delete.


<a name="loio5a3666c015fb476b8b94b8abcbe9a17d"/>

<!-- loio5a3666c015fb476b8b94b8abcbe9a17d -->

## Adding and Deleting a Kyma Module Using Kyma CLI

Use Kyma CLI to add and delete a Kyma module.



<a name="loio5a3666c015fb476b8b94b8abcbe9a17d__prereq_qvz_h3v_v2c"/>

## Prerequisites

You have Kyma CLI installed. For more information, see [Install Kyma CLI](../10-concepts/kyma-cli-292454b.md#loio292454b34bf543afa111dec20d9da434__section_xy1_41f_52c).



## Context

> ### Caution:  
> The `alpha` group commands are still in development, which means their functions and API may be modified over time. We encourage you to explore them, but keep in mind that changes may occur.

Add a Kyma module with simple Kyma CLI commands.



## Procedure

1.  Check the list of modules that are available to be added:

    ```
    kyma alpha module catalog
    ```

2.  Add a new module:

    -   To add a new module with the default configuration, use the following command:

        ```
        kyma alpha module add {MODULE-NAME} --default-cr
        ```

    -   To add a module with your specific configuration, create a YAML file containing your module custom resource \(CR\) settings, and use the`--cr-path={CR-FILEPATH}` flag:

        ```
        kyma alpha module add {MODULE-NAME} --cr-path={CR-FILEPATH}
        
        ```

    -   To add a module with the specified release channel, use the `-c {CHANNEL-NAME}` flag:

        ```
        kyma alpha module add {MODULE-NAME} -c {CHANNEL-NAME} --default-cr
        
        ```





<a name="loio5a3666c015fb476b8b94b8abcbe9a17d__result_pnf_p5l_52c"/>

## Results

To see if your module is added with the default or custom settings, run the following command.

```
kyma alpha module list
```



<a name="loio5a3666c015fb476b8b94b8abcbe9a17d__postreq_nxq_r5l_52c"/>

## Next Steps

To delete your module, use the following command:

```
kyma alpha module delete {MODULE-NAME} 

```

**Related Information**  


[Install Kyma CLI](../10-concepts/kyma-cli-292454b.md#loio292454b34bf543afa111dec20d9da434__section_xy1_41f_52c)

