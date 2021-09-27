<!-- loio3530af7ff2b449fbbc591dd3e2c0d151 -->

# Troubleshooting

This section contains information about the following problems that may occur during the Multitarget Application deployment:

-   [Deployment Failed](Troubleshooting_3530af7.md#loio3530af7ff2b449fbbc591dd3e2c0d151__section_ih3_xm2_p3b)

-   [Service Create/Update/Delete Failures](Troubleshooting_3530af7.md#loio3530af7ff2b449fbbc591dd3e2c0d151__section_etb_bgk_p3b)

-   [Route Mapping Failure](Troubleshooting_3530af7.md#loio3530af7ff2b449fbbc591dd3e2c0d151__section_kvc_wmk_p3b)

-   [Application Binding to Service Failure](Troubleshooting_3530af7.md#loio3530af7ff2b449fbbc591dd3e2c0d151__section_fns_4nk_p3b)

-   [Application Content Upload Failure](Troubleshooting_3530af7.md#loio3530af7ff2b449fbbc591dd3e2c0d151__section_fj2_tvk_p3b)

-   [One-off Tasks Execution Failure](Troubleshooting_3530af7.md#loio3530af7ff2b449fbbc591dd3e2c0d151__section_ofv_dyk_p3b)

-   [Application Start-up Failed](Troubleshooting_3530af7.md#loio3530af7ff2b449fbbc591dd3e2c0d151__section_ksz_pzk_p3b)




<a name="loio3530af7ff2b449fbbc591dd3e2c0d151__section_ih3_xm2_p3b"/>

## Deployment Failed

There might be different reasons for a deployment failure. This section describes the basic steps you should perform in order to recover from a failed deployment. To interact with the failed deployment, you can execute the following actions:

-   **Abort** – terminates a deployment with a given operation id.

    > ### Note:  
    > This action will not roll back all applied changes. It will allow the next deployments of that MTA to proceed without confirmation and the current process will end without any possibilities to retry it from the failed step-on.

    Command: ***cf <deployment-action\> -i <process-id\> -a abort*** 

    > ### Example:  
    > ```
    > 
    > cf bg-deploy -i cbe58aeb-0c40-4a3e-972d-82a499815745 -a abort
    > ```

-   **Retry** – retries the last failed step\(s\) of a deployment with the given operation id.

    Command: ***cf <deployment-action\> -i <process-id\> -a retry*** 

    > ### Example:  
    > ```
    > 
    > cf undeploy -i cbe58aeb-0c40-4a3e-972d-82a499815745 -a retry
    > ```

-   **Download deployment operation logs** – downloads the logs for the current deployment. The logs contain the following structure of files:

    -   MAIN\_LOG - contains the whole deployment log

    -   <application-name\>.log – there is a separate file for each application. It holds the logs, related to the application during staging and starting

    Command: ***cf dmol -i <process-id\>*** 

    > ### Example:  
    > ```
    > 
    > cf dmol -i cbe58aeb-0c40-4a3e-972d-82a499815745
    > ```


Semantics of the commands:

`<deploy-action>` - it may be deploy or bg-deploy or undeploy

`<process-id>` - the process id of the failed deployment. It can be taken from the result of the execution of the `cf mta-ops` command.



<a name="loio3530af7ff2b449fbbc591dd3e2c0d151__section_etb_bgk_p3b"/>

## Service Create/Update/Delete Failures

If a service operation fails, an error message with the following format will be displayed:

-   **Service Create Failure**

    ```
    ...Error creating service "<service-name>" from offering "<service-offering>" and plan "<service-plan>": <cause-of-failure> 
    ```

-   **Service Update Failure**

    ```
    Error updating service "<service-name>" from offering "<service-offering>" and plan "<service-plan>": <cause-of-failure> 
    ```

-   **Service Delete Failure**

    ```
    Error deleting service "<service-name>" from offering "<service-offering>" and plan "<service-plan>": <cause-of-failure> 
    ```


Usually, such errors are produced when there is a problem with the services provisioning infrastructure. To check if there is a problem with the service, perform the following manual steps depending on the failure:

> ### Note:  
> If any create or update parameters are used, make sure that they are the same as those that are used in the MTA.

-   **Service Create Failure**

    ***cf create-service <service-plan\> <service-offering\> <service-instance-name\> \[-c PARAMETERS\_AS\_JSON\]***

-   **Service Update Failure**

    ***cf update-service <service-name\> \[additional arguments if used\] \[-c PARAMETERS\_AS\_JSON\]***

-   **Service Delete Failure**

    ***cf delete-service <service-name\> -f \[-c PARAMETERS\_AS\_JSON\]***


If the same error is reproduced, there is a problem with the service broker rather than the deploy service. Check the following:

1.  Check your entitlement and quotas. Make sure that the quota is enough.

2.  Check if the service parameters are correct.
3.  If none of the above solves the problem, create an incident to the corresponding service broker component.



<a name="loio3530af7ff2b449fbbc591dd3e2c0d151__section_kvc_wmk_p3b"/>

## Route Mapping Failure

If a route could not be mapped to an application and the deployment fails, the following checks can be performed:

1.  ***cf routes*** – displays all the created routes. Verify that the route does not exist.

2.  ***cf map-route <application-name\> <domain\> \[ADDITIONAL OPTIONS\]*** – maps a route to the application with the given name. If the process finishes successfully, retry the deployment operation.

3.  ***cf unmap-route <application-name\> <domain\> \[ADDITIONAL OPTIONS\]*** – removes a route for the application with the given name. If this step is successful, execute step 2.




<a name="loio3530af7ff2b449fbbc591dd3e2c0d151__section_fns_4nk_p3b"/>

## Application Binding to Service Failure

This error can occur when the services are created and the deployment is in phase, in which the application is being bound to the services. The error has the following format:

```
Could not bind application "<application-name>" to service "<service-name>": <cause-of-the-error> 
```

Usually, this error happens when the service provider for the service fails to initiate the binding. The problem might also occur when the Cloud Foundry Cloud Controller component has internal issues. The following steps might help to investigate the issue and eventually resolve it:

1.  Retry the deployment process – for more information about actions related with the deployment, see [Deployment Failed](Troubleshooting_3530af7.md#loio3530af7ff2b449fbbc591dd3e2c0d151__section_ih3_xm2_p3b) section.

2.  If the deployment fails after it is retried, you can try to unbind/bind the application to the service manually, using the commands:

    1.  ***cf bind-service <application-name\> <service-name\> \[ADDITIONAL OPTIONS\]*** - binds the application with the given name to service.

    2.  ***cf unbind-service <application-name\> <service-name\>*** - unbinds the application with the given name from service.




<a name="loio3530af7ff2b449fbbc591dd3e2c0d151__section_fj2_tvk_p3b"/>

## Application Content Upload Failure

Such errors can occur in the following case::

-   There is a problem with the Cloud Controller. The Cloud Controller is responsible for taking the application binaries and storing them, so that it executes the operations stage and starts it afterwards. The status code and the response returned from the Cloud Controller of such errors are in the following format:

    ```
    400 Bad Request, Request entity too large.
    ```

-   The application archive size is bigger than 1GB in size. This limitation is set by the SAP Business Technology Platform and could not be modified.

-   There is a problem with the processing of the application content by the deployer. If this is the case, then an incident to the following component should be created:

    `BC-XS-SL-DS`


When such an error occurs, there are two possible workarounds:

-   Retry the deployment process – for more information about actions related with the deployment, see [Deployment Failed](Troubleshooting_3530af7.md#loio3530af7ff2b449fbbc591dd3e2c0d151__section_ih3_xm2_p3b) section.

-   Execute `cf push` instead of `cf deploy` using only the application with the problematic content.




<a name="loio3530af7ff2b449fbbc591dd3e2c0d151__section_ofv_dyk_p3b"/>

## One-off Tasks Execution Failure

These errors happen when there the one-off tasks defined for some application and their execution fail. Usually, they fail because:

-   There is a problem with the command of the one-off task

    You have to review and fix the command, which the one-off task is executing

-   There is a problem with an SAP Business Technology Platform component responsible for the execution of the one-off task

    You have to retry the deployment process – for more information about actions related with the deployment, see [Deployment Failed](Troubleshooting_3530af7.md#loio3530af7ff2b449fbbc591dd3e2c0d151__section_ih3_xm2_p3b) section.




<a name="loio3530af7ff2b449fbbc591dd3e2c0d151__section_ksz_pzk_p3b"/>

## Application Start-up Failed

Usually, this error happens when there is a problem in the application code. It should be resolved by the developer of the MTA.

In order to locate the problem in the application start-up, the logs of the application should be checked.

You can download the logs as described in the [Deployment Failed](Troubleshooting_3530af7.md#loio3530af7ff2b449fbbc591dd3e2c0d151__section_ih3_xm2_p3b) section.

