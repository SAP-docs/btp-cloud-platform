<!-- loio6062ecc852d04d63829f6c9164be928e -->

# Frequently Asked Questions





### My MTA deployment failed. What could be done?

Check the [MTA Operation Failure](mta-operation-failure-f3e97ff.md) section.



### What to do when my application start-up/staging failed?

Check the [MTA Operation Failure](mta-operation-failure-f3e97ff.md) section.



### How can I find the logs of an application from a failed/succeeded deployment?

There are several ways to find the application logs:

-   `OPERATION.LOG` – contains the whole deployment log.

-   `<application-name>.log` – there is a separate file for each application. It holds the logs related to the application during staging and starting.

    > ### Note:  
    > Note that the operation logs are kept for 3 days. Make sure that you download them before the retention period expires.

    To download the logs, execute the following command:

    `cf dmol -i <process-id>`

    > ### Sample Code:  
    > ```
    > cf dmol -i cbe58aeb-0c40-4a3e-972d-82a499815745
    > ```




### Whom to contact in case of problems with deployment?

When an error occurs during deployment, there is a message which indicates whether the problem is in one of the components of the Cloud Foundry Platform. In such cases, an incident to the corresponding component could be created.

> ### Example:  
> “Controller operation failed: 400 Bad Request: Cannot bind application to service” 

For more information, you can also check the [Troubleshooting](troubleshooting-3530af7.md).



### How to check the state of my deployment?

Use the command `cf mta-ops` and find the id of the operation related to the desired deployment. There will be information about the status of the operation.



### How can I list the MTAs that I have deployed in my space?

Use the `cf mtas` command and locate the ID of the desired MTA. After locating the correct MTA ID, execute the command `cf mta <located-mta-id>` to get detailed information about the MTA with the provided ID.



### What can I do with my deployment?

-   If the deployment fails, see [MTA Operation Failure](mta-operation-failure-f3e97ff.md).

-   If the deployment finishes successfully, you can check the deployment logs.

-   If the deployment is still running, you can abort or monitor it.

    The **Abort** action is described in more details in the [MTA Operation Failure](mta-operation-failure-f3e97ff.md) section.

    The **Monitor** action can be executed with the following command:

    `cf <operation> -i <operation-id> -a monitor. Example: cf deploy -i 12355 -a monitor`




### How can I redeploy my MTA when a deployment is already running?

You can abort the currently running deployment, using the command `cf <operation> -i <operation-id> -a abort` \(Example: `cf deploy -i 12353 -a abort`\) or you can execute the command for starting the deployment by providing the option -f as described in the [deploy](../50-administration-and-ops/multitarget-application-commands-for-the-cloud-foundry-environment-65ddb1b.md#loio65ddb1b51a0642148c6b468a759a8a2e__section_irt_3dc_zs) section.

> ### Example:  
> `cf deploy <path-to-mtar>.mtar -f`



### What are the size limits of an MTA?

4GB for the whole MTA and 1GB for a single module. For more information, see [Prerequisites and Restrictions](multitarget-applications-in-the-cloud-foundry-environment-d04fc0e.md#loiod04fc0e2ad894545aebfd7126384307c__section_ph2_r5h_1cb).



### What to do in case of service creation failure?

See [MTA Operation Failure](mta-operation-failure-f3e97ff.md).



### How to make my deployment faster?

You can use a parallel deployment as described in section [Parallel Deployment](parallel-module-deployment-0384158.md#loio038415880116407d89765d26b36653e3__parallel_deployment).



### How can I resolve problems with the MTA descriptor modeling?

For more information, see [Defining Multitarget Application Deployment Descriptors for Cloud Foundry](defining-multitarget-application-deployment-descriptors-for-cloud-foundry-f48880b.md).



### What is the deployment order of services, applications and other content?

Services are always deployed in parallel.

The applications and content deployment order is determined based on the `deployed-after` module parameter. If `deployed-after` is not used and parallel deployments are not enabled for the MTA, the`requires`/`provides` module sections define the order. For more information, see [Parallel Module Deployment](parallel-module-deployment-0384158.md).



### How to reuse one backing service in two different MTAs?

If you want one MTA to “own” the lifecycle of the service and another to use it only as an “existing service”, use the `org.cloudfoundry.managed-service` and`org.cloudfoundry.existing-service` resource types respectively.



### How to define service instance and bindings parameters?

For more information, see [Service Binding Parameters](service-binding-parameters-c7b09b7.md) as well as [Service Instance Parameters](service-instance-parameters-a36df26.md).

