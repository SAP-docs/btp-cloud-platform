<!-- loiof3e97ffa696045c8846cb709905e058f -->

# MTA Operation Failure

There might be different reasons for an MTA deployment failure. Retrying the last failed step\(s\) of an operation is the first basic step you can take to recover from a failed deployment. This approach is useful for temporary issues with the underlying infrastructure but not helpful for configuration or functional problems.

To do this, enter the following command:

`cf <deployment-action> -i <process-id> -a retry`

> ### Example:  
> `cf undeploy -i cbe58aeb-0c40-4a3e-972d-82a499815745 -a retry`

If retrying the last failed step\(s\) does not solve the problem, you can either try redeploying your MTA or troubleshoot the problem on your own.

To redeploy your MTA, proceed as follows:

1.  Terminate the deployment process. To do this, enter the following command:

    `cf <deployment-action> -i <operation-id> -a abort`

    > ### Example:  
    > `cf deploy -i cbe58aeb-0c40-4a3e-972d-82a499815745 -a abort`

    > ### Note:  
    > This action will not roll back all applied changes to the previous stable version. It will allow the next deployments of that MTA to proceed without confirmation and the current process will end without any possibilities to retry it from the failed step-on.

2.  Start a new deployment. See [Deploying to SAP BTP](https://help.sap.com/docs/btp/sap-business-technology-platform/multitarget-application-commands-for-cloud-foundry-environment?version=Cloud).


To troubleshoot the problem on your own, check the list of possible problems that may occur during the Multitarget Application deployment. If the problem cannot be categorized into any of the sections below, you need to [create an incident](troubleshooting-3530af7.md#loio3530af7ff2b449fbbc591dd3e2c0d151__create_incident).





### Service Create Failure

If the service create fails, an error message with the following format will be displayed:

```
...Error creating service "<service-name>" from offering "<service-offering>" and plan "<service-plan>": <cause-of-failure>
```

Such an error usually occurs due to a problem with the service provisioning infrastructure or the declared service creation parameters. To check if the issue is within the service provisioning infrastructure or the configuration outside the MTA, try creating the service using any of the listed methods in [Creating Service Instances](https://help.sap.com/docs/btp/sap-business-technology-platform/creating-service-instances?locale=en-US&version=Cloud)

> ### Note:  
> If any `create` parameters are used, make sure that they are the same as those that are used in the MTA. Note that the service creation parameters within the MTA may be located in different places, and their combination is required. For more information, see [Service Creation Parameters](https://help.sap.com/docs/btp/sap-business-technology-platform/service-creation-parameters?locale=en-US&version=Cloud).

Depending on the result, proceed in one of the following ways:

-   If the same error occurs, there is a problem with the service broker rather than the deploy service. Check the following:

    -   Check your entitlement and quotas. Make sure that the quota is enough.

    -   Check if the service parameters are correct.


    If none of the above solves the problem, create an incident to the corresponding service broker component.

-   If the above error is not reproduced, download the logs as described in [Troubleshooting](troubleshooting-3530af7.md). Afterward,[create an incident](troubleshooting-3530af7.md#loio3530af7ff2b449fbbc591dd3e2c0d151__create_incident) or contact the SAP support.




### Service Update Failure

If the service update fails, an error message with the following format will be displayed:

```
Error updating service "<service-name>" from offering "<service-offering>" and plan "<service-plan>": <cause-of-failure>
```

Usually, such an error is produced when there is a problem with the services provisioning infrastructure. To check if the issue is within the service provisioning infrastructure or the configuration outside the MTA deployment, try updating the service using any of the listed methods in [Updating Service Instances](https://help.sap.com/docs/btp/sap-business-technology-platform/updating-service-instances?locale=en-US&version=Cloud).

> ### Note:  
> If any `update` parameters are used, make sure that they are the same as those that are used in the MTA. Note that the service update parameters within the MTA may be located in different places, and their combination is important. For more information, see [Service Creation Parameters](https://help.sap.com/docs/btp/sap-business-technology-platform/service-creation-parameters?locale=en-US&version=Cloud).

Depending on the result, proceed in one of the following ways:

-   If the same error occurs, there is a problem with the service broker rather than the deploy service. Check the following:

    -   Check your entitlement and quotas. Make sure that the quota is enough.

    -   Check if the service parameters are correct.


    If none of the above solves the problem, create an incident to the corresponding service broker component.

-   If the above error is not reproduced, download the logs as described in [Troubleshooting](troubleshooting-3530af7.md). Afterward,[create an incident](troubleshooting-3530af7.md#loio3530af7ff2b449fbbc591dd3e2c0d151__create_incident) or contact the SAP support.




### Service Delete Failure

If the service delete fails, an error message with the following format will be displayed:

```
Error deleting service "<service-name>" from offering "<service-offering>" and plan "<service-plan>": <cause-of-failure>
```

Usually, such an error is produced when there is a problem with the services provisioning infrastructure. To check if there is a problem with the service itself, execute the following command:

`cf delete-service <service-name> -f [-c PARAMETERS_AS_JSON]` 

Depending on the result, proceed in one of the following ways:

-   If the same error occurs, there is a problem with the service broker rather than the deploy service. Create an incident to the corresponding service broker component.

-   If the above error is not reproduced, download the logs as described in [Troubleshooting](troubleshooting-3530af7.md). Afterward,[create an incident](troubleshooting-3530af7.md#loio3530af7ff2b449fbbc591dd3e2c0d151__create_incident) or contact the SAP support.




### Application Binding to Service Failure

This error can occur when the services are created and the deployment is in phase, in which the application is being bound to the services. The error has the following format:

```
Could not bind application "<application-name>" to service "<service-name>": <cause-of-the-error> 
```

Usually, this error happens when the service provider for the service fails to initiate the binding. The problem might also occur when the Cloud Foundry Cloud Controller component has internal issues.

Try to resolve the issue by unbinding/binding the application to the service manually, using the commands:

-   `cf bind-service <application-name> <service-name> [ADDITIONAL OPTIONS]` - binds the application with the given name to service.
-   `cf unbind-service <application-name> <service-name>` - unbinds the application with the given name from service.

If the above error is not reproduced, download the logs as described in [Troubleshooting](troubleshooting-3530af7.md). Afterward,[create an incident](troubleshooting-3530af7.md#loio3530af7ff2b449fbbc591dd3e2c0d151__create_incident) or contact the SAP support.



### Application Content Upload Failure

The following error occurs:

```
Error uploading application <specific description>
```

To check if the issue is related to the MTA deployment, execute `cf push` instead of `cf deploy` using only the application with the problematic content.

If the command fails, there is a problem with the application, or the native Cloud Foundry, such as Cloud Controller or used buildpack\(s\). Troubleshoot your application and/or contact your application developer.

If the command is executed successfully, the problem is not related to the application, but there is a problem with the MTA deployment. You **must** download the logs as described in [Troubleshooting](troubleshooting-3530af7.md). Afterward,[create an incident](troubleshooting-3530af7.md#loio3530af7ff2b449fbbc591dd3e2c0d151__create_incident) or contact the SAP support.



### Application Tasks Execution Failure

To check if the issue is related to the MTA deployment, execute `cf run-task APPNAME "TASK"` instead of `cf deploy` using only the problematic task of the application.

If the command fails, there is a problem with the application, or the native Cloud Foundry, such as Cloud Controller. Troubleshoot your application and/or contact your application developer.

If the command is executed successfully, the problem is not related to the application or the task, but there is a problem with the MTA deployment. You **must** download the logs as described in [Troubleshooting](troubleshooting-3530af7.md). Afterward,[create an incident](troubleshooting-3530af7.md#loio3530af7ff2b449fbbc591dd3e2c0d151__create_incident) or contact the SAP support.



### Applicatoin Starting Failure

In order to locate the problem in the application starting, the logs of the application should be checked.

Download the logs as described in [Troubleshooting](troubleshooting-3530af7.md). There should be a dedicated file for the relevant application, which contains more traces for the starting and staging of the application. For instance, if the application is called `my-cf-app`, there would be a file called `my-cf-app.log`.

Normally, the failures during application starting indicate coding or configuration mistakes and self-troubleshooting is a must. Rarely, they might be related to problems in the Cloud Controller or the MTA deployment itself.

The following errors in the console output indicate problems during application starting:

```
Error starting application "<app_name>": Some instances have crashed. Check the logs of your application for more information.
```

```
Error starting application "<app_name>": Some instances are down. Check the logs of your application for more information.
```



### Application Staging Failure

In order to locate the problem in the application staging, the logs of the application should be checked.

Download the logs as described in [Troubleshooting](troubleshooting-3530af7.md). There should be a dedicated file for the relevant application, which contains more traces for the starting and staging of the application. For instance, if the application is called `my-cf-app`, there would be a file called `my-cf-app.log`.

Normally, the failures during application staging indicate coding or configuration mistakes and self-troubleshooting is a must. Rarely, they might be related to problems in the Cloud Controller, buildpack or the MTA deployment itself.

The following error in the console output indicate problems during application staging:

```
Error staging application "<app_name>": …
```

