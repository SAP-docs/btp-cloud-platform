<!-- loio2e4dfeded960446da4aa1c0b734fc81b -->

# \(Experimental\) Incremental Blue-Green Deployment Strategy

Use the incremental blue-green deployment strategy to save resources by incrementally deploying the new version of your Multitarget application.



<a name="loio2e4dfeded960446da4aa1c0b734fc81b__section_ihx_1vm_zcc"/>

## General Information

> ### Restriction:  
> Blue-green deployment is supported only for Cloud Foundry applications. It is not supported for bound services, such as service instances and their configuration, workflow content, and HTML5 repository content, among others. Live and idle applications are bound to the same service instances.

During the incremental blue-green deployment, one instance of the live application is stopped and one new instance of the new application is started at a time, until the new application is started on all instances. This strategy ensures a smooth transition between the old and new versions of an application. The process consists of the following steps:

1.  **Initial Setup**: The new version of the application is deployed to only one instance.

2.  **Testing Phase**: The deployment process enters the validation phase, where users or automated systems can test the new application.

3.  **User Acceptance**: Customers or designated testers evaluate the new application.

4.  **Deployment Continuation**: Once testing results are satisfactory, the deployment process resumes.

5.  **Incremental Scaling**:

    -   One instance of the old application is stopped.

    -   One instance of the new application is started.


    This step is repeated until the new application reaches the desired number of instances.

    > ### Note:  
    > During the incremental blue-green deployment, the total number of instances \(old + new\) will not exceed **N + 1**, where **N** is the desired instance count for the new application.

    If an instance crashes during this step, a "rollback" procedure is initiated:

    -   The old application is scaled back up to its initial instance count.

    -   The new application is scaled down to one instance.


    This rollback ensures system stability by restoring the previous state of the applications.

6.  **Completion**: After the new application is fully scaled up, the remaining instances of the old application are stopped and removed.


> ### Note:  
> If you are using the [Application Autoscaler](https://help.sap.com/docs/application-autoscaler/application-autoscaler/what-is-application-autoscaler) service, note the following:
> 
> -   The new application will not be autoscaled during the incremental blue-green deployment process. The autoscaling will start after the deployment process completes.
> 
> -   Once the deployment process resumes and enters the **Incremental Scaling** phase, autoscaling will also be disabled for the live application.
> 
> 
> This ensures that neither the idle nor the live applications are rescaled by the Autoscaler, preventing potential inconsistencies.

The incremental blue-green deployment has the following advantages and disadvantages:


<table>
<tr>
<th valign="top">

Pros

</th>
<th valign="top">

Cons

</th>
</tr>
<tr>
<td valign="top">

The incremental blue-green deployment requires less memory resource than the standard blue-green deployment, which means that it could save memory quota and reduce costs.

In certain scenarios, services may calculate monthly costs based on the maximum number of instances associated with an application. In a standard blue-green deployment, where both versions of the application run simultaneously, this can temporarily double the number of instances, potentially leading to higher charges.

It is advisable to consult with the service provider, to understand the specific pricing implications for end customers.

</td>
<td valign="top">

The incremental blue-green deployment requires more time to complete than the normal blue-green deployment, as the new application instances are started sequentially, which means that it waits for every new instance to completely start before starting the next one.

</td>
</tr>
</table>

To perform an incremental blue-green deployment, follow the steps in the sections below.



<a name="loio2e4dfeded960446da4aa1c0b734fc81b__section_qg3_v5m_zcc"/>

## Prerequisites

-   You have a previously deployed MTA, with functional productive applications and routes:

    ![](images/Blue_Application_Version_of_an_MTA_NEW_8d66427.png)

-   You have ensured that the changes in the new version of the application are compatible with the old version. This includes changes in the database tables, UAA configurations, and so on.




<a name="loio2e4dfeded960446da4aa1c0b734fc81b__section_acp_2zt_zcc"/>

## Context

If you have already executed successful deployments using the [Blue-Green Deployment Strategy](blue-green-deployment-strategy-7c83810.md) \(`cf deploy --strategy blue-green`\), you should have no problems when executing deployments with the incremental blue-green deployment strategy \(`cf deploy --strategy incremental-blue-green`\). This also applies if you decide to go back to the blue-green deployment strategy.

However, this does not apply for the [Legacy Blue-Green Deployment](legacy-blue-green-deployment-764308c.md) \(`cf bg-deploy`\). It is not recommended to go back to this deployment method.

> ### Caution:  
> Do not begin a blue-green deployment using '`cf bg-deploy`' and continue with '`cf deploy --strategy blue-green / incremental-blue-green`', or vice versa, as this might result in downtime.



<a name="loio2e4dfeded960446da4aa1c0b734fc81b__section_qrf_kzt_zcc"/>

## Procedure

1.  Deploy your updated MTA in idle state by executing the command `cf deploy <your-mta-archive-v2> --strategy incremental-blue-green`.

    The first action is that all MTA services are updated.

    This creates:

    -   one instance of the new application with the suffix “idle” added to the original application name

    -   temporary routes to this idle application instance

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

    > ### Tip:  
    > You can skip this step by using one of the following command line options:
    > 
    > -   `--skip-testing-phase` - this option will not wait for user confirmation after testing.
    > 
    > -   `--skip-idle-start` - this option will also skip the start of the newly deployed application on idle routes and will not wait for user confirmation.

3.  If you do not want to make the “idle” version available, abort the process by using `cf deploy -i <operation ID> -a abort`.

    > ### Note:  
    > This action does not perform a rollback and the state of apps, routes, and services remains unchanged. Depending on your needs, you might want to remove the new app versions and the temporary routes.

4.  If you want to make the “idle” version productive, manually resume the process by using `cf deploy -i <operation ID> -a resume`.

    This does the following:

    -   maps the productive routes to your idle application versions

    -   deletes the temporary routes of the idle application

    -   restarts idle apps with productive route configurations

    -   incrementally stops one instance of the live application and starts a new instance of the new application until it is started on all required instances

    -   deletes the live applications which were productive before


    ![](images/Green_Application_version_of_an_MTA_NEW_ec69fb7.png)




<a name="loio2e4dfeded960446da4aa1c0b734fc81b__section_c2v_kjc_bdc"/>

## Examples

For more detailed information and example results of the incremental blue-green deployment process, see [Blue-Green Deployment with incremental-blue-green strategy](https://github.com/SAP-samples/cf-mta-examples/tree/main/blue-green-deploy-strategy/incremental-blue-green-deploy#blue-green-deployment-with-incremental-blue-green-strategy).

**Related Information**  


[Blue-Green Deployment Strategy](blue-green-deployment-strategy-7c83810.md "Use the current blue-green deployment of Multitarget applications.")

[Legacy Blue-Green Deployment](legacy-blue-green-deployment-764308c.md "Use the legacy blue-green deployment strategy of Multitarget applications.")

[Multitarget Application Commands for the Cloud Foundry Environment](../50-administration-and-ops/multitarget-application-commands-for-the-cloud-foundry-environment-65ddb1b.md "A list of additional commands to deploy multitarget applications (MTA) to the Cloud Foundry environment.")

