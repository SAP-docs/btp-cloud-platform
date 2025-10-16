<!-- loio7c83810c31d842938cbc39c135a2d99f -->

# Blue-Green Deployment Strategy

Use the current blue-green deployment of multitarget applications.



<a name="loio7c83810c31d842938cbc39c135a2d99f__prereq_ssz_xnt_dlb"/>

## Prerequisites

> ### Restriction:  
> Blue-green deployment is supported only for Cloud Foundry applications. It is not supported for bound services, such as service instances and their configuration, workflow content, and HTML5 repository content, among others. Live and idle applications are bound to the same service instances.

-   You have a previously deployed MTA, with functional productive applications and routes:

    ![](images/Blue_Application_Version_of_an_MTA_NEW_8d66427.png)

-   You have ensured that the changes in the new version of the application are compatible with the old version. This includes changes in the database tables, UAA configurations, and so on.




<a name="loio7c83810c31d842938cbc39c135a2d99f__context_nvv_tfx_rcb"/>

## Context

If you have already executed successful deployments using the [Legacy Blue-Green Deployment](legacy-blue-green-deployment-764308c.md) method \('`cf bg-deploy`'\), you should have no problems when executing deployments with the blue-green deployment strategy \('`cf deploy --strategy blue-green`'\). However, this does not apply the other way around and it is generally not recommended to go back to the legacy blue-green deployment method.

> ### Caution:  
> Do not begin a blue-green deployment using '`cf bg-deploy`' and continue with '`cf deploy --strategy blue-green`', or vice versa, as this might result in downtime.



<a name="loio7c83810c31d842938cbc39c135a2d99f__steps_ryh_k2m_qcb"/>

## Procedure

1.  Deploy your updated MTA in idle state by executing the command `cf deploy <your-mta-archive-v2> --strategy blue-green`.

    > ### Note:  
    > If you want to have the opportunity to perform a rollback after the blue-green deployment, you need to back up your MTA by adding the command line option `--backup-previous-version`. For more information, see [\(Experimental\) Rollback of Multitarget Applications](experimental-rollback-of-multitarget-applications-d612be9.md).

    The first action is that all MTA services are updated.

    This creates:

    -   new applications adding “idle” to the original application names

        > ### Note:  
        > The new application version is launched on all instances defined in the MTA deployment descriptor. During the testing phase or when the deployment is paused for user verification, the application temporarily requires double the usual resources \(instances\). This is because both the old and the new versions of the application are running concurrently. If the testing phase is skipped or if the deployment continues without delay, the resource usage will be optimized sooner.
        > 
        > If you are looking for a more resource-efficient deployment approach, see [Incremental Blue-Green Deployment Strategy](incremental-blue-green-deployment-strategy-2e4dfed.md). However, keep in mind that this approach requires more time than the standard blue-green deployment strategy.

    -   temporary routes to the idle applications

        ![](images/Blue-Green_with_a_Temporatry_Route_NEW_2519972.png)

    -   an interrupt to the process showing a message similar to the following:

        > ### Output Code:  
        > ```
        > Process has entered testing phase. After testing your new deployment you can resume or abort the process.
        > Use "cf deploy -i 7e6233b9-6001-11ea-8959-eeee0a98a87d -a abort" to abort the process.
        > Use "cf deploy -i 7e6233b9-6001-11ea-8959-eeee0a98a87d -a resume" to resume the process.
        > Hint: Use the '--skip-testing-phase' option of the deploy command to skip this phase
        > ```


2.  Optionally, test the idle version of the application using the temporary routes.

    > ### Note:  
    > You can skip this step by using one of the following command line options:
    > 
    > -   *\--skip-testing-phase* - you have to use it when starting the process.
    > 
    > -   *\--skip-idle-start* - this option will also skip the start of the newly deployed applications on idle routes.

3.  If you do not want to make the “idle” version available, abort the process using cf deploy `-i <operation ID> -a abort`.

    > ### Note:  
    > This action does not perform a rollback and the state of apps, routes and services remains unchanged. Depending on your needs, you might want to remove the new app versions and the temporary routes.

4.  If you want to make the “idle” version productive, manually resume the process, using `cf deploy -i <operation ID> -a resume`.

    This does the following:

    -   maps the productive routes to your idle versions
    -   deletes the temporary routes
    -   restarts “idle” apps with productive route configurations
    -   deletes the “live” applications, which were productive before

        ![](images/Green_Application_version_of_an_MTA_NEW_ec69fb7.png)





<a name="loio7c83810c31d842938cbc39c135a2d99f__result_jz4_vwx_xkb"/>

## Results

For more detailed information and example results of the blue-green deployment process, see [Blue-Green Deployment](https://github.com/SAP-samples/cf-mta-examples/tree/main/blue-green-deploy-strategy).

**Related Information**  


[Blue-Green Deployment of Multitarget Applications](blue-green-deployment-of-multitarget-applications-772ab72.md "Use the blue-green deployment technique by running two identical production environments, allowing seamless updates without downtime for Cloud Foundry multitarget applications.")

[Legacy Blue-Green Deployment](legacy-blue-green-deployment-764308c.md "Use the legacy blue-green deployment strategy of multitarget applications.")

[Incremental Blue-Green Deployment Strategy](incremental-blue-green-deployment-strategy-2e4dfed.md "Use the incremental blue-green deployment strategy to save resources by incrementally deploying the new version of your multitarget application.")

[Multitarget Application Commands for the Cloud Foundry Environment](../50-administration-and-ops/multitarget-application-commands-for-the-cloud-foundry-environment-65ddb1b.md "A list of additional commands to deploy multitarget applications (MTA) to the Cloud Foundry environment.")

