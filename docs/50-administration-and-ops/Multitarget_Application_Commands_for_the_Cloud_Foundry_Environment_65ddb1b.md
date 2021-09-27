<!-- loio65ddb1b51a0642148c6b468a759a8a2e -->

# Multitarget Application Commands for the Cloud Foundry Environment

A list of additional commands to install archives and deploy multitarget applications \(MTA\) to the Cloud Foundry environment.



> ### Note:  
> The expiration time for all Cloud Foundry operations is 3 days. If an operation is still active when time limit is reached, it is automatically aborted.

> ### Caution:  
> Due to the deprecation of the shared domains, the URL of the SAP Cloud Deployment service should be specified by each multitarget application developer. You can do this by using the environment variable `MULTIAPPS_CONTROLLER_URL`, or the `-u` option specified in the commands listed below.
> 
> The URL of the deploy-service that needs to be set is in the following format: `deploy-service.cfapps.<landscape-domain>`
> 
> If you are using the `-u` option, make sure you have the MultiApps CLI Plugin version 2.1.3 or higher

<a name="loio65ddb1b51a0642148c6b468a759a8a2e__table_ph4_5yb_zs"/>Commands for the Cloud Foundry Environment Overview


<table>
<tr>
<th>

Command



</th>
<th>

Alias



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

[`deploy`](Multitarget_Application_Commands_for_the_Cloud_Foundry_Environment_65ddb1b.md#loio65ddb1b51a0642148c6b468a759a8a2e__section_irt_3dc_zs)



</td>
<td>

 



</td>
<td>

Deploy a new Multitarget Application \(MTA\) or synchronize changes to an existing MTA



</td>
</tr>
<tr>
<td>

[`bg-deploy`](Multitarget_Application_Commands_for_the_Cloud_Foundry_Environment_65ddb1b.md#loio65ddb1b51a0642148c6b468a759a8a2e__section_lmg_5p4_kv)



</td>
<td>

 



</td>
<td>

Deploy a Multitarget Application using “blue-green” \(zero-downtime\) deployment



</td>
</tr>
<tr>
<td>

[`undeploy`](Multitarget_Application_Commands_for_the_Cloud_Foundry_Environment_65ddb1b.md#loio65ddb1b51a0642148c6b468a759a8a2e__section_axl_phv_kt)



</td>
<td>

 



</td>
<td>

Undeploy a Multitarget Application \(MTA\)



</td>
</tr>
<tr>
<td>

[`mta`](Multitarget_Application_Commands_for_the_Cloud_Foundry_Environment_65ddb1b.md#loio65ddb1b51a0642148c6b468a759a8a2e__section_hww_4hv_kt)



</td>
<td>

 



</td>
<td>

Display information about a deployed Multitarget Application \(MTA\)



</td>
</tr>
<tr>
<td>

[`mtas`](Multitarget_Application_Commands_for_the_Cloud_Foundry_Environment_65ddb1b.md#loio65ddb1b51a0642148c6b468a759a8a2e__section_x3p_4hv_kt)



</td>
<td>

 



</td>
<td>

List all deployed Multitarget Applications \(MTA\)



</td>
</tr>
<tr>
<td>

[`mta-ops`](Multitarget_Application_Commands_for_the_Cloud_Foundry_Environment_65ddb1b.md#loio65ddb1b51a0642148c6b468a759a8a2e__section_cpf_rkk_vt)



</td>
<td>

 



</td>
<td>

List all active operations for Multitarget Applications



</td>
</tr>
<tr>
<td>

[`download-mta-op-logs`](Multitarget_Application_Commands_for_the_Cloud_Foundry_Environment_65ddb1b.md#loio65ddb1b51a0642148c6b468a759a8a2e__section_fhv_fkk_vt)



</td>
<td>

`dmol`



</td>
<td>

Download the log files for one or more operations concerning Multitarget Applications



</td>
</tr>
<tr>
<td>

[`purge-mta-config`](Multitarget_Application_Commands_for_the_Cloud_Foundry_Environment_65ddb1b.md#loio65ddb1b51a0642148c6b468a759a8a2e__section_jxk_n4p_wx)



</td>
<td>

 



</td>
<td>

Purge all configuration entries and subscriptions, which are no longer valid



</td>
</tr>
</table>

> ### Note:  
> By default, large multitarget applications are not uploaded as a single unit, but are split up into smaller chunks of 45 MBs that are uploaded separately. Configure the chunk size as described in [Configuration](https://github.com/cloudfoundry-incubator/multiapps-cli-plugin#configuration).



<a name="loio65ddb1b51a0642148c6b468a759a8a2e__section_irt_3dc_zs"/>

## deploy

Deploy a new MTA or synchronize changes to an existing one. You have the following options for doing this:



### Usage

-   **Deployment using a path to a directory**

    You have the option to deploy or synchronize an MTA, the source of which is contained in a local directory:

    ```
    `cf deploy *<MTA\_ARCHIVE\>*|*<DIRECTORY\_PATH\>* [-e *<EXT\_DESCRIPTOR\_1\>*[,*<EXT\_DESCRIPTOR\_2\>*]] 
    [-u *<URL\>*] [-t *<TIMEOUT\>*] [-v *<VERSION\_RULE\>*]
    [--no-start] [--namespace]
    [--delete-services] [--delete-service-keys] [--delete-service-brokers] 
    [][--keep-files] [--no-restart-subscribed-apps] [--do-not-fail-on-missing-permissions]`
    ```

-   **Deployment using an URL to the MTA archive**

    You have the option to deploy or synchronize an MTA, the source of which is contained at a URL address.When you use this command, the request prompts the backend to download the archive and then dеploy it:

    ```
    `cf deploy *<URL to MTA archive\>* [-e *<EXT\_DESCRIPTOR\_1\>*[,*<EXT\_DESCRIPTOR\_2\>*]] 
    [-u *<MTA controller URL\>*] [-t *<TIMEOUT\>*] [-v *<VERSION\_RULE\>*]
    [--no-start] [--namespace]
    [--delete-services] [--delete-service-keys] [--delete-service-brokers] 
    [][--keep-files] [--no-restart-subscribed-apps] [--do-not-fail-on-missing-permissions]`
    ```

    > ### Note:  
    > -   The URL to the MTA archive must include the *<http://\>* or *<https://\>* prefixes.
    > -   You can use an locally present extension descriptor along with this deployment method.

    > ### Caution:  
    > There is no possibility for you to check if there are running ongoing operations on the MTA that you want to deploy using a URL.

-   **Deployment from your current directory**

    You have the option to deploy the content of the directory you are currently in. The MultiApps CLI plugin packages the content in accordance with the deployment descriptor definition, so that the Cloud Deployment service can then upload and deploy the MTA.

    ```
    `cf deploy [-e *<EXT\_DESCRIPTOR\_1\>*[,*<EXT\_DESCRIPTOR\_2\>*]] 
    [-u *<URL\>*] [-t *<TIMEOUT\>*] [-v *<VERSION\_RULE\>*]
    [--no-start] [--namespace]
    [--delete-services] [--delete-service-keys] [--delete-service-brokers] 
    [][--keep-files] [--no-restart-subscribed-apps] [--do-not-fail-on-missing-permissions]`
    ```


In additon to deployment, you can also interact with an active MTA deploy operation, for example, by performing an action:

```
`cf deploy  [-i *<OPERATION\_ID\>*] [-a *<ACTION\>*] `
```



### Arguments

The Cloud Deployment service uses the content of the mtad.yaml descriptor, and based its contained info assembles an MTA archive in that directory before deploying it.

<a name="loio65ddb1b51a0642148c6b468a759a8a2e__table_zkx_spb_zs"/>Command Arguments Overview


<table>
<tr>
<th>

Argument



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

*<MTA\_ARCHIVE\>*



</td>
<td>

The path to \(and name of\) the archive or the directory containing the Multitarget Application to deploy; the application archive must have the format \(and file extension\) `mtar`, for example, `MTApp1.mtar`. If the value of this argument is a directory, the checks if an mtad.yaml file exists in that directory, and based on it assembles an MTA archive before deploying it. If no argument exists, the current directory is used.



</td>
</tr>
<tr>
<td>

*<DIRECTORY\_PATH\>*



</td>
<td>

The Cloud Deployment service also accepts a path to a directory where an `mtad.yaml` is maintained with path elements, for example, `cf deploy ./`.



</td>
</tr>
</table>



### Options

<a name="loio65ddb1b51a0642148c6b468a759a8a2e__table_smw_5v2_ys"/>Command Options Overview


<table>
<tr>
<th>

Option



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

`*-e* *<EXT\_DESCRIPTOR\_1\>*[,*<EXT\_DESCRIPTOR\_2\>*]`



</td>
<td>

Define one or more extensions to the deployment descriptors; multiple extension descriptors must be separated by commas.



</td>
</tr>
<tr>
<td>

`*-u* *<URL\>*`



</td>
<td>

Specify the URL for the deployment-service end-point that is to be used for the deployment operation



</td>
</tr>
<tr>
<td>

`*-t* *<TIMEOUT\>*`



</td>
<td>

Specify the maximum amount of time \(in seconds\) that the service must wait for before starting the deployed application



</td>
</tr>
<tr>
<td>

`*-v* *<VERSION\_RULE\>*`



</td>
<td>

Specify the rule to apply to determine how the application version number is used to trigger an application-update deployment operation, for example: “`HIGHER`”, “`SAME_HIGHER`”, or “`ALL`”.



</td>
</tr>
<tr>
<td>

`*-i* *<OPERATION\_ID\>*`



</td>
<td>

Specify the ID of the deploy operation that you want to perform an action on



</td>
</tr>
<tr>
<td>

`*-a* *<ACTION\>*`



</td>
<td>

Specify the action to perform on the deploy operation, for example, “abort”, “retry”, or “monitor”, or “resume”



</td>
</tr>
<tr>
<td>

`*-f* `



</td>
<td>

Force deployment without requiring any confirmation about aborting any conflicting processes

> ### Note:  
> This option is not functional when deploying using a URL to an MTA archive.



</td>
</tr>
<tr>
<td>

`*--no-start*`



</td>
<td>

Do not start application after deployment



</td>
</tr>
<tr>
<td>

`*--delete-services*`



</td>
<td>

Re-create changed services and delete discontinued services



</td>
</tr>
<tr>
<td>

`*--delete-service-keys*`



</td>
<td>

Delete the existing service keys and apply the new ones



</td>
</tr>
<tr>
<td>

`*--delete-service-brokers*`



</td>
<td>

Delete discontinued service brokers



</td>
</tr>
<tr>
<td>

`*--keep-files*`



</td>
<td>

Keep the files used for deployment



</td>
</tr>
<tr>
<td>

`*--no-restart-subscribed-apps*`



</td>
<td>

Do not restart subscribed applications that are updated during the deployment



</td>
</tr>
<tr>
<td>

`*--do-not-fail-on-missing-permissions*`



</td>
<td>

Perform the deployment, even if required administrator permissions are missing for some operations \(for example, the creation of service brokers\).



</td>
</tr>
<tr>
<td>

`*--abort-on-error*`



</td>
<td>

If an operation fails, the corresponding process is automatically aborted and cannot be retried using the option *-a retry*. However, if you run a new operation for the same MTA, you will not receive an error message that there is an ongoing process for the MTA and ask you if you want to abort it.



</td>
</tr>
<tr>
<td>

`*-m <module name\>*`



</td>
<td>

Deploy only the module with the specified name.

> ### Note:  
> It can be used multiple times.



</td>
</tr>
<tr>
<td>

`*--all-modules*`



</td>
<td>

Deploy all modules.

> ### Note:  
> Any `-m` options are ignored.



</td>
</tr>
<tr>
<td>

`*-r <resource name\>*`



</td>
<td>

Deploy only the resource with the specified name

> ### Note:  
> It can be used multiple times.



</td>
</tr>
<tr>
<td>

`*--all-resources*`



</td>
<td>

Deploy all resources.

> ### Note:  
> Any `-r` options are ignored.



</td>
</tr>
<tr>
<td>

`*--verify-archive-signature*`



</td>
<td>

Check the archive signature by verifying that:

-   The archive is correctly signed with a Symantec certificate.
-   All files are signed correctly.
-   The certificate is valid.
-   The certificate subject is SAP.

> ### Example:  
> ***cf deploy <mtar\_name\> --verify-archive-signature***



</td>
</tr>
<tr>
<td>

`*--strategy*`

> ### Note:  
> This option is currently experimental.



</td>
<td>

Announce to the platform a special deployment approach, for example when performing a “blue-green” deployment. See [Blue-Green Deployment Strategy](../30-development/Blue-Green_Deployment_Strategy_7c83810.md).



</td>
</tr>
<tr>
<td>

`*--skip-testing-phase*`

> ### Note:  
> This option is currently experimental.



</td>
<td>

When using the *--strategy* option for “blue-green” deployment, you can choose to skip the phase for testing the correct operation of the application using productive data.



</td>
</tr>
<tr>
<td>

`*--namespace*`

> ### Note:  
> This option is currently experimental.



</td>
<td>

Namespace for the MTA. They are also applied to the application and service names. For more information, see [\(Experimental\) Namespaces](../30-development/(Experimental)_Namespaces_b28fd77.md).



</td>
</tr>
</table>

> ### Note:  
> -   If any of the options `-m`, `--all-modules`, `-r`, `--all-resource` is used, only the specified modules and resources will be deployed. Otherwise, everything will be deployed by default.
> -   If the options for the module deploying \( `-m`, `--all-modules`\) are used, the modules need to contain a `path` element on an MTA module level, which points to the content of the module. In case the module has some `requires` dependency section to a resource that needs a configuration file, then the `requires` section should have a `path` parameter, which points to the configuration file.
> -   If the options for the resource deploying \(`-r`, `--all-resource`\) are used, then any resources that have some configuration files need to contain a `path` parameter in their parameters section, which points to the configuration file.
> -   The `path` element or parameter value should be relative to the MTA directory.
> 
> An example of an MTA deployment descriptor, containing all variants of the `path` elements and parameters can be found at [Defining Multitarget Application Deployment Descriptors for Cloud Foundry](../30-development/Defining_Multitarget_Application_Deployment_Descriptors_for_Cloud_Foundry_f48880b.md).



<a name="loio65ddb1b51a0642148c6b468a759a8a2e__section_lmg_5p4_kv"/>

## bg-deploy

Deploy a new Multitarget Application \(MTA\) using “blue-green” \(zero-downtime\) deployment.

> ### Note:  
> You can also perform this deployment type using the `*deploy*` command by using the experimental `*--strategy blue-green*` flag. See above for details.

“Blue-green” deployment is a release technique that reduces application downtime and the resulting risk by running two identical target deployment environments called “blue” and “green”. Only one of the two target environments is “live” at any point in time and it is much easier to roll back to a previous version after a failed \(or undesired\) deployment.



### Usage

Deploy a new Multitarget Application using “blue-green” deployment:

```
`cf bg-deploy *<MTA\_ARCHIVE\>*  
[-e *<EXT\_DESCRIPTOR\_1\>*[,*<EXT\_DESCRIPTOR\_2\>*]] 
[-u *<URL\>*] [-t *<TIMEOUT\>*] [-v *<VERSION\_RULE\>*]
[--no-start] [--use-namespaces] [--no-namespaces-for-services]
[--delete-services] [--delete-service-keys] [--delete-service-brokers] 
[--keep-files] [--no-restart-subscribed-apps] [--no-confirm] [--do-not-fail-on-missing-permissions]`
```

Interact with an active MTA deploy operation, for example, by performing an action:

```
`cf bg-deploy  [-i *<OPERATION\_ID\>*] [-a *<ACTION\>*] `
```



### Arguments

<a name="loio65ddb1b51a0642148c6b468a759a8a2e__table_k23_rp4_kv"/>Command Arguments Overview


<table>
<tr>
<th>

Argument



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

*<MTA\_ARCHIVE\>*

or

*<DIRECTORY\_PATH\>*



</td>
<td>

The path to \(and name of\) the archive or the path to the directory containing the Multitarget Application to deploy. The application archive must have the format \(and file extension\) `mtar`, for example, `MTApp1.mtar`; the specified directory can be specified as a path \(for example, `myApp/` or `.` \(current directory\).



</td>
</tr>
</table>



### Options

<a name="loio65ddb1b51a0642148c6b468a759a8a2e__table_l23_rp4_kv"/>Command Options Overview


<table>
<tr>
<th>

Option



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

`*-e* *<EXT\_DESCRIPTOR\_1\>*[,*<EXT\_DESCRIPTOR\_2\>*]`



</td>
<td>

Define one or more extensions to the deployment descriptors; multiple extension descriptors must be separated by commas.



</td>
</tr>
<tr>
<td>

`*-u* *<URL\>*`



</td>
<td>

Specify the URL for the deployment-service end-point that is to be used for the deployment operation



</td>
</tr>
<tr>
<td>

`*-t* *<TIMEOUT\>*`



</td>
<td>

Specify the maximum amount of time \(in seconds\) that the service must wait for before starting the deployed application



</td>
</tr>
<tr>
<td>

`*-v* *<VERSION\_RULE\>*`



</td>
<td>

Specify the rule to apply to determine how the application version number is used to trigger an application-update deployment operation, for example: “`HIGHER`”, “`SAME_HIGHER`”, or “`ALL`”.



</td>
</tr>
<tr>
<td>

`*-i* *<OPERATION\_ID\>*`



</td>
<td>

Specify the ID of the deploy operation that you want to perform an action on



</td>
</tr>
<tr>
<td>

`*-a* *<ACTION\>*`



</td>
<td>

Specify the action to perform on the deploy operation, for example, “abort”, “retry”, or “monitor”, or “resume”



</td>
</tr>
<tr>
<td>

`*-f* `



</td>
<td>

Force deploy without requiring any confirmation for aborting any conflicting processes



</td>
</tr>
<tr>
<td>

`*--no-start*`



</td>
<td>

Do not start application after deployment



</td>
</tr>
<tr>
<td>

`*--use-namespaces*`



</td>
<td>

Use namespaces in application \(and service\) names during application deployment



</td>
</tr>
<tr>
<td>

`*--no-namespaces-for-services*`



</td>
<td>

Do not use namespaces in service names



</td>
</tr>
<tr>
<td>

`*--delete-services*`



</td>
<td>

Re-create changed services and delete discontinued services



</td>
</tr>
<tr>
<td>

`*--delete-service-keys*`



</td>
<td>

Delete the existing service keys and apply the new ones



</td>
</tr>
<tr>
<td>

`*--delete-service-brokers*`



</td>
<td>

Delete discontinued service brokers



</td>
</tr>
<tr>
<td>

`*--keep-files*`



</td>
<td>

Keep the files used for deployment



</td>
</tr>
<tr>
<td>

`*--no-restart-subscribed-apps*`



</td>
<td>

Do not restart subscribed applications that are updated during the deployment



</td>
</tr>
<tr>
<td>

`*--no-confirm*`



</td>
<td>

Use this option to turn off the manual confirmation for deleting the older version of the MTA applications. Thus the deployment process is performed from start to finish uninterrupted, and you are not prompted to confirm the switch of routes to the new version of the MTA applications.



</td>
</tr>
<tr>
<td>

`*--do-not-fail-on-missing-permissions*`



</td>
<td>

Perform the deployment, even if required administrator permissions are missing for some operations \(for example, the creation of service brokers\).



</td>
</tr>
<tr>
<td>

`*--abort-on-error*`



</td>
<td>

If an operation fails, the corresponding process is automatically aborted and cannot be retried using the option *-a retry*



</td>
</tr>
<tr>
<td>

`*-m <module name\>. However, if you run a new operation for the same MTA, you will not receive an error message that there is an ongoing process for the MTA and ask you if you want to abort it.*`



</td>
<td>

Deploy only the module with the specified name.

> ### Note:  
> It can be used multiple times.



</td>
</tr>
<tr>
<td>

`*--all-modules*`



</td>
<td>

Deploy all modules.

> ### Note:  
> Any `-m` options are ignored.



</td>
</tr>
<tr>
<td>

`*-r <resource name\>*`



</td>
<td>

Deploy only the resource with the specified name

> ### Note:  
> It can be used multiple times.



</td>
</tr>
<tr>
<td>

`*--all-resources*`



</td>
<td>

Deploy all resources.

> ### Note:  
> Any `-r` options are ignored.



</td>
</tr>
<tr>
<td>

`*--verify-archive-signature*`



</td>
<td>

Check the archive signature by verifying that:

-   . However, if you run a newThe archive is correctly signed with a Symantec certificate.
-   All files are signed correctly.
-   The certificate is valid.
-   The certificate subject is SAP.

> ### Example:  
> ***cf bg-deploy <mtar\_name\> --verify-archive-signature***



</td>
</tr>
</table>

> ### Note:  
> -   If any of the options `-m`, `--all-modules`, `-r`, `--all-resource` is used, only the specified modules and resources will be deployed. Otherwise, everything will be deployed by default.
> -   If the options for the module deploying \( `-m`, `--all-modules`\) are used, the modules need to contain a `path` element on an MTA module level, which points to the content of the module. In case the module has some `requires` dependency section to a resource that needs a configuration file, then the `requires` section should have a `path` parameter, which points to the configuration file.
> -   If the options for the resource deploying \(`-r`, `--all-resource`\) are used, then any resources that have some configuration files need to contain a `path` parameter in their parameters section, which points to the configuration file.
> -   The `path` element or parameter value should be relative to the MTA directory.
> 
> See the complete procedure in section [Legacy Blue-Green Deployment](../30-development/Legacy_Blue-Green_Deployment_764308c.md).
> 
> An example of an MTA deployment descriptor, containing all variants of the `path` elements and parameters can be found at [Defining Multitarget Application Deployment Descriptors for Cloud Foundry](../30-development/Defining_Multitarget_Application_Deployment_Descriptors_for_Cloud_Foundry_f48880b.md).



<a name="loio65ddb1b51a0642148c6b468a759a8a2e__section_axl_phv_kt"/>

## undeploy

Undeploy a Multitarget Application \(MTA\), or interact with an undeploy MTA operation.



### Usage

Undeploy an MTA.

```
`cf undeploy *<MTA\_ID\>*  
[-u *<URL\>*] [-f] 
[--delete-services] [--delete-service-keys] [--delete-service-brokers] [--no-restart-subscribed-apps] 
[--do-not-fail-on-missing-permissions]`
```

Interact with an undeploy MTA operation, for example, by performing an action.

```
`cf undeploy [-i *<UNDEPLOY\_ID\>*] [-a *<ACTION\>*]`
```



### Arguments

<a name="loio65ddb1b51a0642148c6b468a759a8a2e__table_lxc_zkv_kt"/>Command Arguments Overview


<table>
<tr>
<th>

Argument



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

*<MTA\_ID\>*



</td>
<td>

The ID of the MTA you want to undeploy



</td>
</tr>
</table>



### Options

<a name="loio65ddb1b51a0642148c6b468a759a8a2e__table_bzt_slv_kt"/>Command Options Overview


<table>
<tr>
<th>

Option



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

`*-u* *<URL\>*`



</td>
<td>

Specify the URL for the service end-point that is to be used for the undeployment operation



</td>
</tr>
<tr>
<td>

`*-i* *<OPERATION\_ID\>*`



</td>
<td>

Specify the ID of the undeploy operation that you want to perform an action on



</td>
</tr>
<tr>
<td>

`*-a* *<ACTION\>*`



</td>
<td>

Specify the action to perform on the undeploy operation, for example, “abort”, “retry”, or “monitor”



</td>
</tr>
<tr>
<td>

`*-f* `



</td>
<td>

Force completion of the undeploy operation without any system prompt or confirmation



</td>
</tr>
<tr>
<td>

`*--delete-services* `



</td>
<td>

Delete any related services



</td>
</tr>
<tr>
<td>

`*--delete-service-brokers* `



</td>
<td>

Delete discontinued service brokers



</td>
</tr>
<tr>
<td>

`*--no-restart-subscribed-apps*`



</td>
<td>

Do not restart subscribed applications that are updated during the deployment



</td>
</tr>
<tr>
<td>

`*--do-not-fail-on-missing-permissions*`



</td>
<td>

Perform the deployment, even if required administrator permissions are missing for some operations \(for example, the creation of service brokers\).



</td>
</tr>
<tr>
<td>

`*--abort-on-error*`



</td>
<td>

If an operation fails, the corresponding process is automatically aborted and cannot be retried using the option *-a retry*. However, if you run a new operation for the same MTA, you will not receive an error message that there is an ongoing process for the MTA and ask you if you want to abort it.



</td>
</tr>
<tr>
<td>

`*--delete-service-keys*`



</td>
<td>

Delete the existing service keys



</td>
</tr>
</table>



<a name="loio65ddb1b51a0642148c6b468a759a8a2e__section_hww_4hv_kt"/>

## mta

Display information about a Multitarget Application \(MTA\). The information displayed includes the requested state, the number of instances, information about allocated memory and disk space, as well as details regarding the bound service \(and service plan\).



### Usage

```
`cf mta MTA_ID  
[-u *<URL\>*]`
```



### Arguments

<a name="loio65ddb1b51a0642148c6b468a759a8a2e__table_egg_2nv_kt"/>Command Arguments Overview


<table>
<tr>
<th>

Argument



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

 *<MTA\_ID\>* 



</td>
<td>

The ID of the MTA whose details you want to display



</td>
</tr>
</table>



### Options

<a name="loio65ddb1b51a0642148c6b468a759a8a2e__table_lrg_2nv_kt"/>Command Options Overview


<table>
<tr>
<th>

Option



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

 `*-u* *<URL\>*` 



</td>
<td>

Specify the URL for the deployment-service end-point to use to obtain details of the selected MTA



</td>
</tr>
</table>



<a name="loio65ddb1b51a0642148c6b468a759a8a2e__section_x3p_4hv_kt"/>

## mtas

Display information about all available Multitarget Applications \(MTA\).



### Usage

```
`cf mtas [-u *<URL\>*]`
```



### Options

<a name="loio65ddb1b51a0642148c6b468a759a8a2e__table_wgx_qnv_kt"/>Command Options Overview


<table>
<tr>
<th>

Option



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

 `*-u* *<URL\>*` 



</td>
<td>

Specify the URL for the deployment-service end-point to use to obtain details of the selected MTA



</td>
</tr>
</table>



<a name="loio65ddb1b51a0642148c6b468a759a8a2e__section_cpf_rkk_vt"/>

## mta-ops

Display information about all **active** operations for Multitarget Applications \(MTA\). The information includes the ID, type, status, the time the MTA-related operation started, as well as the name of the user that started the operation.



### Usage

```
cf mta-ops [--mta *<MTA\>*] [-u *<URL\>*] [--last *<NUM\>*] [--all]
```



### Options

<a name="loio65ddb1b51a0642148c6b468a759a8a2e__table_fty_thk_vt"/>Command Options Overview


<table>
<tr>
<th>

Option



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

`*-u* *<URL\>*`



</td>
<td>

Specify the URL for the deployment-service end-point to use to obtain details of the selected MTA operations



</td>
</tr>
<tr>
<td>

`*--last* *<NUM\>*`



</td>
<td>

List the last *<NUM\>* active MTA operations



</td>
</tr>
<tr>
<td>

`*--all*`



</td>
<td>

List all active MTA operations



</td>
</tr>
<tr>
<td>

`*– mta <MTA\>*`



</td>
<td>

Specify the MTA whose operations you want to list.



</td>
</tr>
</table>



<a name="loio65ddb1b51a0642148c6b468a759a8a2e__section_fhv_fkk_vt"/>

## download-mta-op-logs

Download the log files for one or more operations concerning Multitarget Applications.



### Usage

You have the following usage options:

-   ```
`cf download-mta-op-logs -i *<OPERATION\_ID\>* [-u *<URL\>*] [-d *<DIRECTORY\>*]`
```

-   ```
cf download-mta-op-logs --mta <MTA> [ --last *<NUM\>*] [ -u *<URL\>*] [ -d *<DIRECTORY\>*]
```


> ### Tip:  
> You can use the alias `dmol` in place of the `download-mta-op-logs` command.



### Options

<a name="loio65ddb1b51a0642148c6b468a759a8a2e__table_wnd_33k_vt"/>Command Options Overview


<table>
<tr>
<th>

Option



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

`*-u* *<URL\>*`



</td>
<td>

Specify the URL for the deployment-service end-point to use to obtain details of the selected MTA operations



</td>
</tr>
<tr>
<td>

`*-i* *<OPERATION\_ID\>*`



</td>
<td>

Specify the identity \(ID\) of the MTA operation whose logs you want to download



</td>
</tr>
<tr>
<td>

`*-d* *<DIRECTORY\>*`



</td>
<td>

Specify the path to the location where you want to save the downloaded MTA operation logs; by default, the location is `./mta-op-*<OPERATION\_ID\>*/`



</td>
</tr>
<tr>
<td>

`*--mta**<MTA\>*`



</td>
<td>

Specify the MTA whose logs you want to download.

> ### Note:  
> This option is not compatible with the *-i* option.



</td>
</tr>
<tr>
<td>

`*--last**<NUM\>*`



</td>
<td>

Download the last <NUM\> logs for the specified MTA.



</td>
</tr>
</table>



<a name="loio65ddb1b51a0642148c6b468a759a8a2e__section_jxk_n4p_wx"/>

## purge-mta-config

Purge all configuration entries and subscriptions, which are no longer valid.



### Usage

```
`cf purge-mta-config   
[-u *<URL\>*]`
```

Invalid configuration entries are often produced when the application that is providing configuration entries is deleted by the user without using the deploy-service, for example, the `cf delete` command . In this case, the configuration remains in the deploy-service database even though the corresponding application is no longer available. This could lead to a failure during subsequent attempts to resolve the configuration entries.



### Options

<a name="loio65ddb1b51a0642148c6b468a759a8a2e__table_fbf_cqp_wx"/>Command Options Overview


<table>
<tr>
<th>

Option



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

 `*-u* *<URL\>*` 



</td>
<td>

The URL of the deploy service



</td>
</tr>
</table>

-   **[Application Versions and Deployment Consistency](Application_Versions_and_Deployment_Consistency_e366d0d.md)**  


**Related Information**  


[MultiApps CLI plugin](https://github.com/cloudfoundry-incubator/multiapps-cli-plugin)

[Cloud Foundry multitarget аpplication еxamples repository](https://github.com/SAP-samples/cf-mta-examples)

[Deploy an MTA archive referenced by a remote URL](https://github.com/SAP-samples/cf-mta-examples/tree/master/deploy-with-url)

