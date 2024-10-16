<!-- loio05402110821742479725338cc8d7fe8c -->

# Applications

If you want to create an application in Cloud Foundry and use the SAP Cloud Deployment service, you must create an MTA module first.

In most of cases, an MTA module represents a Cloud Foundry application, but there are cases where they represent an entirely different type of entity, for example content. Modules can have different types and parameters that modify their behavior. See [Modules](modules-177d34d.md) for more information.

> ### Note:  
> We strongly recommend that you specify the appropriate buildpack for your application. This ensures that the application is handled by the buildpack for which it is intended and tested. It also speeds up application deployment, because only the specified buildpack is downloaded for use during the staging process.
> 
> You have to use the `buildpack` module parameter, if you are using any of the following MTA module types:
> 
> -   `application`
> -   `custom`
> -   `javascript.nodejs`



<a name="loio05402110821742479725338cc8d7fe8c__section_spx_wx5_jgb"/>

## MTA Deployment Optimizations

The MTA deployment is an incremental process. This means that the state of the artifacts in the Cloud Foundry environment is compared to the desired state described in the `mtad.yaml`. If there's a difference, a set of operations are computed in order to make the MTA reach the desired state. The following optimizations are possible during the MTA redeployment:

-   The application bits are uploaded again if the following is true:
    -   The application content is changed and there is no cache of the same content for a different application, even in a different space. The Cloud Foundry environment has global caching of application bits without organizational and space isolation.

-   The application is restaged and restarted if the following is true:
    -   The application attributes, such as commands, buildpacks, memory, `health-check-url`, and so on, are changed.
    -   The application environment is changed.
    -   There are new services to which the application is bound.
    -   There are services the application is bound to, which are discontinued \(not available\) in the new version of the MTA.

        > ### Note:  
        > Currently, Cloud Foundry environment applications are restaged if they are bound to any service with parameters. This is necessary, because it's not possible to get the current Cloud Foundry service parameters and compare them with the desired ones.

    -   The application is bound to service whose configuration parameters have been changed. This requires an update of the service instance and rebind, restage, and restart of the application.
    -   The service binding parameters are changed. This requires an update of the service binding and restage of the application.
    -   The MTA version is changed, which requires a change of special application environment variables, managed by the deploy service.




<a name="loio05402110821742479725338cc8d7fe8c__section_qlj_kky_ncc"/>

## **Application-Specific Timeouts**

When creating Cloud Foundry applications as part of the MTA deployment, you have the option to set specific timeouts for different phases of the application's creation or execution. When any of these timeouts occur, the MTA operation fails with a relevant error message to avoid MTA deployment run indefinitely. When any of these timeouts occurs, the MTA operation fails and a relevant error message is displayed. This is to prevent the MTA deployment from running indefinitely.

Currently the following timeouts are supported:

-   **Upload timeout** – the time it takes to upload the application binary to the Cloud Controller. Once the upload is complete, the application is ready to use.


-   **Stage timeout** – the time it takes to stage the application.


-   **Start timeout** – the time it takes to start all application instances.


-   **Task execution timeout** – the time between when you run a Cloud Foundry task and when it reaches its final state.




### Priority of Timeout Parameters

You can configure application timeouts at different levels according to your needs. When the same timeout \(for example, start timeout\) is configured in several places for one MTA deployment, a certain order of priority is applied.

The order provides flexibility when you want to define common timeouts for all applications which are part of an MTA but at the same time, you need to define application-specific timeouts.

The timeout parameters follow the following descending order of priority:

1.  **Operation parameters / Command-Line Options \(Highest Priority\):** 

    The highest priority is given to operation parameters passed during the MTA deployment. If you provide a timeout value as a command-line option, it overrides any other parameters defined into the MTA descriptor. These operation parameters apply to all applications.

    > ### Example:  
    > ```
    > cf deploy … --apps-upload-timeout 40 –apps-upload-timeout 50 --apps-start-timeout 30 –apps-task-execution-timeout 100 
    > ```

2.  **Module-Level Parameters:** 

    If you do not provide any command-line arguments, the module-level parameters are used instead.

    > ### Example:  
    > ```
    > 
    > modules: 
    >    - name: java 
    >      .......... 
    >      parameters: 
    >         upload-timeout: 100 
    >         stage-timeout: 50 
    >         start-timeout: 60 
    >         task-execution-timeout:120 
    > ```

3.  **Global-Level Parameters:** 

    If neither a command-line option nor a module-level parameter are provided, the global parameters are used. Global parameters are applicable to all applications.

    > ### Example:  
    > ```
    > 
    > parameters: 
    >      apps-upload-timeout: 50 
    >      apps-stage-timeout: 60 
    >      apps-start-timeout: 70 
    >      apps-task-execution-timeout:110  
    > ```

4.  **Default Values:**

    If you do not provide any of the above parameters, the application uses the predefined default timeout values. This ensures that there is always a time limit in place to prevent MTA operations from running indefinitely.

    Default values:

    -   Start timeout: 1h

    -   Upload timeout: 1h

    -   Stage timeout: 1h

    -   Task execution timeout: 12h





### Maximum Allowed Values

-   Upload timeout: 3h

-   Stage timeout: 3h

-   Start timeout: 3h

-   Task execution timeout: 24h


**Related Information**  


[Modules](modules-177d34d.md "The modules section of the deployment descriptor lists the deployable parts contained in the MTA deployment archive.")

