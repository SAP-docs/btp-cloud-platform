<!-- loio4c40fdaa0795488d86f370e11866f2a6 -->

# Sensitive Data Handling During MTA Deployment

Securely manage credentials and other sensitive values during MTA deployment.



## Feature Overview

When deploying applications, developers often need to specify some sensitive data during deployment, such as passwords, certificates, or credentials to external services, that will later be used during application runtime. The SAP Cloud Deployment service provides a secure mechanism for handling such sensitive data during multitarget application deployment. This eliminates the need to put credentials and secret values in MTA descriptors, which are normally stored in source control repositories or file systems.

The feature is enabled by adding the `--require-secure-parameters` flag to the `cf deploy` command. After that, sensitive values \(declared as specially-formatted environment variables before the deployment\) are:

1.  Collected by the MultiApps CF CLI plugin and validated
2.  Transmitted securely to the SAP Cloud Deployment service over HTTPS using a special MTA extension description that is built in memory
3.  Encrypted for the duration of the deployment using a key stored in a Cloud Foundry user-provided service instance. The service instance is either persisted or deleted afterwards, depending on the chosen approach \(see [Encryption Key Handling](sensitive-data-handling-during-mta-deployment-4c40fda.md#loio4c40fdaa0795488d86f370e11866f2a6__deployment-modes)\).
4.  Decrypted only when needed during deployment
5.  Automatically excluded from all deployment logs and outputs

> ### Note:  
> -   The feature can be used only with the MultiApps CF CLI plugin and by the services and tools that utilize it, such as SAP Continuous Integration and Delivery. For more information, see [Multitarget Application Plugin for Cloud Foundry Command Line Interface](../50-administration-and-ops/multitarget-application-plugin-for-cloud-foundry-command-line-interface-e93b231.md).
> 
> -   Avoid using the command-line option `--keep-files` while using this feature, in order for file removal to take place after the process is finished.



<a name="loio4c40fdaa0795488d86f370e11866f2a6__deployment-modes"/>

## Encryption Key Handling

The key used for encrypting your sensitive data is stored in a Cloud Foundry user-provided service instance located in the current Cloud Foundry space of the customer. You can choose between using a persistent or disposable user-provided service instance approach:

**Persistent** \(default\): Uses a user-provided service instance that you create and manage manually. This service instance contains the encryption key and can persist across multiple deployments. You are responsible for creating, updating, and deleting the instance, as well as managing key rotation between deployments. For more information, see [Using a Persistent User-Provided Service Instance](using-a-persistent-user-provided-service-instance-33b5047.md).

> ### Note:  
> -   For each new deployment, we recommend creating a new user-provided service instance or updating the already existing one.
> -   If key rotation is mandatory, then it must be done between MTA deployments and not during an active MTA deployment. Before changing or deleting the encryption key, ensure that all processes using this key have finished completely.
> 
> Using a disposable user-provided service instance is recommended in this case, as it allows automatic key rotation \(a new key is generated for each deployment\).

**Disposable**: Uses a user-provided service instance with a randomly generated encryption key that is automatically created at the start of each deployment and deleted when the operation completes. This mode is activated with the `--disposable-user-provided-service` flag and provides automatic key rotation per deployment. For more information, see [Using a Disposable User-Provided Service Instance](using-a-disposable-user-provided-service-instance-2e50c4e.md).

**Related Information**  


[Using a Persistent User-Provided Service Instance](using-a-persistent-user-provided-service-instance-33b5047.md "Pass sensitive values during MTA deployment by creating or using a persistent user-provided service instance.")

[Using a Disposable User-Provided Service Instance](using-a-disposable-user-provided-service-instance-2e50c4e.md "Pass sensitive values during MTA deployment by using a disposable user-provided service instance.")

[Environment Variables and User-Provided Service Instance Specifics](environment-variables-and-user-provided-service-instance-specifics-1b8cb82.md "Naming conventions and other specifics regarding the environment variables and user-provided service instances used for sensitive data handling during MTA deployment.")

