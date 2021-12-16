<!-- loio6062ecc852d04d63829f6c9164be928e -->

# Frequently Asked Questions





### My MTA deployment failed. What could be done?

Check the [Deployment Failed](troubleshooting-3530af7.md#loio3530af7ff2b449fbbc591dd3e2c0d151__section_ih3_xm2_p3b) section.



### What to do when my application start-up/staging failed?

Check the [Application Start-up Failed](troubleshooting-3530af7.md#loio3530af7ff2b449fbbc591dd3e2c0d151__section_ksz_pzk_p3b) section.



### How can I find the logs of an application from a failed/succeeded deployment?

There are several ways to find the application logs:

-   Use the `cf dmol -i <operation-id>` command in order to download the logs of the deployment of an operation with id `<operation-id>`. The id of the operation could be obtained using the `cf mta-ops` command. In the downloaded deployment logs, there will be a `<application-name>.log` file which contains the logs of the application.

-   Use `cf logs <application-name> --recent` in order to retrieve the recent logs of the application.

    > ### Note:  
    > The recent logs are available for only 10 minutes.

    For more information, check the options for downloading the deployment logs in the [Deployment Failed](troubleshooting-3530af7.md#loio3530af7ff2b449fbbc591dd3e2c0d151__section_ih3_xm2_p3b) section.




### How to find more information about the problematic deployment?

Use the `cf dmol -i <operation-id>` command in order to download the deployment operation logs as described in the [Deployment Failed](troubleshooting-3530af7.md#loio3530af7ff2b449fbbc591dd3e2c0d151__section_ih3_xm2_p3b) section. After downloading the deployment logs, locate the file with name `MAIN_LOG` which contains the whole logs of the deployment. You will find a detailed error message in it.



### Whom to contact in case of problems with deployment?

When an error occurs during deployment, there is a message which indicates whether the problem is in one of the components of the Cloud Foundry Platform. In such cases, an incident to the corresponding component could be created.

> ### Example:  
> “Controller operation failed: 400 Bad Request: Cannot bind application to service” 

For more information, you can also check the [Troubleshooting](troubleshooting-3530af7.md).



### How to check the state of my deployment?

Use the command `cf mta-ops` and find the id of the operation related to the desired deployment. There will be information about the status of the operation.



### How can I list the MTAs that I have deployed in my space?

Use the `cf mtas` command and locate the ID of the desired MTA. After locating the correct MTA ID, execute the command `cf mta <located-mta-id>` to get detailed information about the the MTA with the provided ID.



### What can I do with my deployment?

-   If the deployment fails, see [Deployment Failed](troubleshooting-3530af7.md#loio3530af7ff2b449fbbc591dd3e2c0d151__section_ih3_xm2_p3b)

-   If the deployment finishes successfully, you can check the deployment logs.

-   If the deployment is still running, you can abort or monitor it.

    The **Abort** action is described in more details in the [Deployment Failed](troubleshooting-3530af7.md#loio3530af7ff2b449fbbc591dd3e2c0d151__section_ih3_xm2_p3b) section.

    The **Monitor** action can be executed with the following command:

    `cf <operation> -i <operation-id> -a monitor. Example: cf deploy -i 12355 -a monitor`




### How can I redeploy my MTA when a deployment is already running?

You can abort the currently running deployment, using the command `cf <operation> -i <operation-id> -a abort` \(Example: `cf deploy -i 12353 -a abort`\) or you can execute the command for staring the deployment by providing the option -f as described in the [deploy](../50_administration_and_ops/multitarget-application-commands-for-the-cloud-foundry-environment-65ddb1b.md#loio65ddb1b51a0642148c6b468a759a8a2e__section_irt_3dc_zs) section.

> ### Example:  
> `cf deploy <path-to-mtar>.mtar -f`



### What are the size limits of an MTA?

4GB for the whole MTA and 1GB for a single module. For more information, see [Multitarget Applications for the Cloud Foundry Environment](multitarget-applications-in-the-cloud-foundry-environment-d04fc0e.md#loiod04fc0e2ad894545aebfd7126384307c__section_ph2_r5h_1cb)



### What to do in case of service creation failure?

See [Service Create/Update/Delete Failures](troubleshooting-3530af7.md#loio3530af7ff2b449fbbc591dd3e2c0d151__section_etb_bgk_p3b)



### How to make my deployment faster?

You can use a parallel deployment as described in section [Parallel Deployment](parallel-module-deployment-0384158.md#loio038415880116407d89765d26b36653e3__parallel_deployment)



### How can I resolve problems with the MTA descriptor modeling?

For more information, see [Defining Multitarget Application Deployment Descriptors for Cloud Foundry](defining-multitarget-application-deployment-descriptors-for-cloud-foundry-f48880b.md)



### What is the deployment order of services, applications and other content?

Services are always deployed in parallel.

The applications and content deployment order is determined based on the `deployed-after` module parameter. If `deployed-after` is not used and parallel deployments are not enabled for the MTA, the`requires`/`provides` module sections define the order. For more information, see [Parallel Module Deployment](parallel-module-deployment-0384158.md).



### How to reuse one backing service in two different MTAs?

If you want one MTA to “own” the lifecycle of the service and another to use it only as an “existing service”, use the `org.cloudfoundry.managed-service` and`org.cloudfoundry.existing-service` resource types respectively.



### How to define service instance and bindings parameters?

For more information, see [Service Binding Parameters](service-binding-parameters-c7b09b7.md) as well as [Service Creation Parameters](service-creation-parameters-a36df26.md).



### How to make sure that my archive is signed correctly by SAP and its content has not been changed ?

Use the deployment option `*--verify-archive-signature*` as described in [Multitarget Application Commands for the Cloud Foundry Environment](../50_administration_and_ops/multitarget-application-commands-for-the-cloud-foundry-environment-65ddb1b.md).

