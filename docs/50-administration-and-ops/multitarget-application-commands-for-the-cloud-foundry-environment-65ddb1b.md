<!-- loio65ddb1b51a0642148c6b468a759a8a2e -->

# Multitarget Application Commands for the Cloud Foundry Environment

A list of additional commands to deploy multitarget applications \(MTA\) to the Cloud Foundry environment.



> ### Note:  
> The expiration time for all MTA operations in Cloud Foundry is 3 days. If an operation is still active when time limit is reached, it is automatically aborted.

> ### Caution:  
> Due to the missing shared domains in certain regions, as China \(Shanghai\), the URL of the SAP Cloud Deployment service should be specified by each multitarget application developer who uses MultiApps CF CLI plugin older that 3.0.0. If you are using MultiApps CF CLI plugin newer than 3.0.0, you do not need additional settings. You can do this by using the environment variable `MULTIAPPS_CONTROLLER_URL`, or the `-u` option specified in the commands listed below.
> 
> The URL of the deploy-service that needs to be set is in the following format: `deploy-service.cf.<domain>` The domain is derived from the Cloud Foundry API endpoint that you can find in the SAP BTP Cockpit in the Overview of your subaccount. For more information, see Deploying Applications in[Regions](../10-concepts/regions-350356d.md) and [Regions and API Endpoints Available for the Cloud Foundry Environment](../10-concepts/regions-and-api-endpoints-available-for-the-cloud-foundry-environment-f344a57.md).
> 
> If you are using the `-u` option, make sure you have the MultiApps CLI Plugin version 2.1.3 or higher
> 
> If you are using region CN40 with API Endpoint api.cf.cn40.platform.sapcloud.cn, you need to specify the URL as follows: `export MULTIAPPS_CONTROLLER_URL=deploy-service.cf.cn40.platform.sapcloud.cn`

**Commands for the Cloud Foundry Environment Overview**


<table>
<tr>
<th valign="top">

Command

</th>
<th valign="top">

Alias

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

[`deploy`](multitarget-application-commands-for-the-cloud-foundry-environment-65ddb1b.md#loio65ddb1b51a0642148c6b468a759a8a2e__section_irt_3dc_zs)

</td>
<td valign="top">

 

</td>
<td valign="top">

Deploy a new Multitarget Application \(MTA\) or synchronize changes to an existing MTA

</td>
</tr>
<tr>
<td valign="top">

[`bg-deploy`](multitarget-application-commands-for-the-cloud-foundry-environment-65ddb1b.md#loio65ddb1b51a0642148c6b468a759a8a2e__section_lmg_5p4_kv)

</td>
<td valign="top">

 

</td>
<td valign="top">

Deploy a Multitarget Application using “blue-green” \(zero-downtime\) deployment

</td>
</tr>
<tr>
<td valign="top">

[`undeploy`](multitarget-application-commands-for-the-cloud-foundry-environment-65ddb1b.md#loio65ddb1b51a0642148c6b468a759a8a2e__section_axl_phv_kt)

</td>
<td valign="top">

 

</td>
<td valign="top">

Undeploy a Multitarget Application \(MTA\)

</td>
</tr>
<tr>
<td valign="top">

[`mta`](multitarget-application-commands-for-the-cloud-foundry-environment-65ddb1b.md#loio65ddb1b51a0642148c6b468a759a8a2e__section_hww_4hv_kt)

</td>
<td valign="top">

 

</td>
<td valign="top">

Display information about a deployed Multitarget Application \(MTA\)

</td>
</tr>
<tr>
<td valign="top">

[`mtas`](multitarget-application-commands-for-the-cloud-foundry-environment-65ddb1b.md#loio65ddb1b51a0642148c6b468a759a8a2e__section_x3p_4hv_kt)

</td>
<td valign="top">

 

</td>
<td valign="top">

List all deployed Multitarget Applications \(MTA\)

</td>
</tr>
<tr>
<td valign="top">

[`mta-ops`](multitarget-application-commands-for-the-cloud-foundry-environment-65ddb1b.md#loio65ddb1b51a0642148c6b468a759a8a2e__section_cpf_rkk_vt)

</td>
<td valign="top">

 

</td>
<td valign="top">

List all active operations for Multitarget Applications

</td>
</tr>
<tr>
<td valign="top">

[`download-mta-op-logs`](multitarget-application-commands-for-the-cloud-foundry-environment-65ddb1b.md#loio65ddb1b51a0642148c6b468a759a8a2e__section_fhv_fkk_vt)

</td>
<td valign="top">

`dmol`

</td>
<td valign="top">

Download the log files for one or more operations concerning Multitarget Applications

</td>
</tr>
<tr>
<td valign="top">

[`purge-mta-config`](multitarget-application-commands-for-the-cloud-foundry-environment-65ddb1b.md#loio65ddb1b51a0642148c6b468a759a8a2e__section_jxk_n4p_wx)

</td>
<td valign="top">

 

</td>
<td valign="top">

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
    cf deploy MTA_ARCHIVE | DIRECTORY_PATH [-e EXT_DESCRIPTOR[,...]] [-t TIMEOUT] 
    [--version-rule VERSION_RULE] [-u URL] [-f] [--retries RETRIES] [--no-start] [--namespace NAMESPACE] 
    [--apply-namespace-app-names true/false] [--apply-namespace-service-names true/false] 
    [--apply-namespace-app-routes true/false] [--apply-namespace-as-suffix true/false ] 
    [--delete-services] [--delete-service-keys] [--delete-service-brokers] [--keep-files] 
    [--no-restart-subscribed-apps] [--do-not-fail-on-missing-permissions] [--abort-on-error] 
    [--strategy STRATEGY] [--skip-testing-phase] [--skip-idle-start] [--apps-start-timeout TIMEOUT] 
    [--apps-stage-timeout TIMEOUT] [--apps-upload-timeout TIMEOUT] [--apps-task-execution-timeout TIMEOUT]
    ```

-   **Deployment using a URL to the MTA archive**

    You have the option to deploy or synchronize an MTA, the source of which is contained at a URL address.When you use this command, the request prompts the backend to download the archive and then dеploy it:

    > ### Caution:  
    > This option is currently experimental.

    ```
    <write MTA archive URL to STDOUT> | cf deploy [-e EXT_DESCRIPTOR[,...]] 
    [-t TIMEOUT] [--version-rule VERSION_RULE] [-u MTA_CONTROLLER_URL] [--retries RETRIES] [--no-start] 
    [--namespace NAMESPACE] [--apply-namespace-app-names true/false] [--apply-namespace-service-names true/false] 
    [--apply-namespace-app-routes true/false] [--apply-namespace-as-suffix true/false ] [--delete-services] 
    [--delete-service-keys] [--delete-service-brokers] [--keep-files] [--no-restart-subscribed-apps] 
    [--do-not-fail-on-missing-permissions] [--abort-on-error] [--strategy STRATEGY] [--skip-testing-phase] 
    [--skip-idle-start] [--apps-start-timeout TIMEOUT] [--apps-stage-timeout TIMEOUT] 
    [--apps-upload-timeout TIMEOUT] [--apps-task-execution-timeout TIMEOUT]
    ```

    > ### Caution:  
    > There is no possibility for you to check if there are running ongoing operations on the MTA that you want to deploy using a URL.

    > ### Note:  
    > -   The URL to the MTA archive must include the *<https://\>* prefix.
    > -   You can use an locally present extension descriptor along with this deployment method.

-   **Deployment from your current directory**

    You have the option to deploy the content of the directory you are currently in. The MultiApps CLI plugin packages the content in accordance with the deployment descriptor definition, so that the Cloud Deployment service can then upload and deploy the MTA.

    ```
    cf deploy [-e <EXT_DESCRIPTOR_1>[,<EXT_DESCRIPTOR_2>]] 
    [-u <URL>] [-t <TIMEOUT>] [-v <VERSION_RULE>]
    [--no-start] [--namespace]
    [--delete-services] [--delete-service-keys] [--delete-service-brokers] 
    [][--keep-files] [--no-restart-subscribed-apps] [--do-not-fail-on-missing-permissions] [--skip-idle-start]
    cf deploy ...[--retries <RETRIES>]
    ```


In additon to deployment, you can also interact with an active MTA deploy operation, for example, by performing an action:

```
cf deploy  [-i <OPERATION_ID>] [-a <ACTION>] 
```



### Arguments

The Cloud Deployment service uses the content of the mtad.yaml descriptor, and based its contained info assembles an MTA archive in that directory before deploying it.

**Command Arguments Overview**


<table>
<tr>
<th valign="top">

Argument

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

*<MTA\_ARCHIVE\>*

</td>
<td valign="top">

The path to \(and name of\) the archive or the directory containing the Multitarget Application to deploy; the application archive must have the format \(and file extension\) `mtar`, for example, `MTApp1.mtar`. If the value of this argument is a directory, the checks if an mtad.yaml file exists in that directory, and based on it assembles an MTA archive before deploying it. If no argument exists, the current directory is used.

</td>
</tr>
<tr>
<td valign="top">

*<DIRECTORY\_PATH\>*

</td>
<td valign="top">

The Cloud Deployment service also accepts a path to a directory where an `mtad.yaml` is maintained with path elements, for example, `cf deploy ./`.

</td>
</tr>
<tr>
<td valign="top">

*<--retries\>*

</td>
<td valign="top">

Retry the operation specified number of times in case a non-content error \(default 3\).

</td>
</tr>
</table>



### Options

**Command Options Overview**


<table>
<tr>
<th valign="top">

Option

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

<code><i>-e</i> <i class="varname">&lt;EXT_DESCRIPTOR_1&gt;</i>[,<i class="varname">&lt;EXT_DESCRIPTOR_2&gt;</i>]</code>

</td>
<td valign="top">

Define one or more extensions to the deployment descriptors; multiple extension descriptors must be separated by commas.

</td>
</tr>
<tr>
<td valign="top">

<code><i>-u</i> <i class="varname">&lt;URL&gt;</i></code>

</td>
<td valign="top">

Specify the URL for the deployment-service end-point that is to be used for the deployment operation

</td>
</tr>
<tr>
<td valign="top">

<code><i>-t</i> <i class="varname">&lt;TIMEOUT&gt;</i></code>

</td>
<td valign="top">

Specify the maximum amount of time \(in seconds\) that the service must wait for before starting the deployed application

</td>
</tr>
<tr>
<td valign="top">

<code><i>-v</i> <i class="varname">&lt;VERSION_RULE&gt;</i></code>

</td>
<td valign="top">

Specify the rule to apply to determine how the application version number is used to trigger an application-update deployment operation, for example: “`HIGHER`”, “`SAME_HIGHER`”, or “`ALL`”.

</td>
</tr>
<tr>
<td valign="top">

<code><i>-i</i> <i class="varname">&lt;OPERATION_ID&gt;</i></code>

</td>
<td valign="top">

Specify the ID of the deploy operation that you want to perform an action on

</td>
</tr>
<tr>
<td valign="top">

<code><i>-a</i> <i class="varname">&lt;ACTION&gt;</i></code>

</td>
<td valign="top">

Specify the action to perform on the deploy operation, for example, “abort”, “retry”, or “monitor”, or “resume”

</td>
</tr>
<tr>
<td valign="top">

<code><i>-f</i> </code>

</td>
<td valign="top">

Force deployment without requiring any confirmation about aborting any conflicting processes

</td>
</tr>
<tr>
<td valign="top">

<code><i>--no-start</i></code>

</td>
<td valign="top">

Do not start application after deployment

</td>
</tr>
<tr>
<td valign="top">

<code><i>--apps-upload-timeout &lt;TIMEOUT&gt;</i></code>

</td>
<td valign="top">

Defines how long, in seconds, you can upload your application binary before the MTA operation times out.

See [Application-Specific Timeouts](../30-development/applications-0540211.md#loio05402110821742479725338cc8d7fe8c__section_qlj_kky_ncc) .

> ### Note:  
> This applies to all applications.



</td>
</tr>
<tr>
<td valign="top">

<code><i>--apps-stage-timeout &lt;TIMEOUT&gt;</i></code>

</td>
<td valign="top">

Defines how long, in seconds, your application can take during staging before the MTA operation times out.

See [Application-Specific Timeouts](../30-development/applications-0540211.md#loio05402110821742479725338cc8d7fe8c__section_qlj_kky_ncc) .

> ### Note:  
> This applies to all applications.



</td>
</tr>
<tr>
<td valign="top">

<code><i>--apps-start-timeout &lt;TIMEOUT&gt;</i></code>

</td>
<td valign="top">

Defines how long, in seconds, your application can take to start before the MTA operation times out.

See [Application-Specific Timeouts](../30-development/applications-0540211.md#loio05402110821742479725338cc8d7fe8c__section_qlj_kky_ncc) .

> ### Note:  
> This applies to all applications.



</td>
</tr>
<tr>
<td valign="top">

<code><i>--apps-task-execution-timeout &lt;TIMEOUT&gt;</i></code>

</td>
<td valign="top">

Defines how long, in seconds, your application can take to execute a task before the MTA operation times out.

See [Application-Specific Timeouts](../30-development/applications-0540211.md#loio05402110821742479725338cc8d7fe8c__section_qlj_kky_ncc) .

> ### Note:  
> This applies to all applications.



</td>
</tr>
<tr>
<td valign="top">

<code><i>--delete-services</i></code>

</td>
<td valign="top">

Re-create changed services and delete discontinued services

</td>
</tr>
<tr>
<td valign="top">

<code><i>--delete-service-keys</i></code>

</td>
<td valign="top">

Delete the existing service keys and apply the new ones

</td>
</tr>
<tr>
<td valign="top">

<code><i>--delete-service-brokers</i></code>

</td>
<td valign="top">

Delete discontinued service brokers

</td>
</tr>
<tr>
<td valign="top">

<code><i>--keep-files</i></code>

</td>
<td valign="top">

Keep the files used for deployment

</td>
</tr>
<tr>
<td valign="top">

<code><i>--no-restart-subscribed-apps</i></code>

</td>
<td valign="top">

Do not restart subscribed applications that are updated during the deployment

</td>
</tr>
<tr>
<td valign="top">

<code><i>--do-not-fail-on-missing-permissions</i></code>

</td>
<td valign="top">

Perform the deployment, even if required administrator permissions are missing for some operations \(for example, the creation of service brokers\).

</td>
</tr>
<tr>
<td valign="top">

<code><i>--abort-on-error</i></code>

</td>
<td valign="top">

If an operation fails, the corresponding process is automatically aborted and cannot be retried using the option *\-a retry*. However, if you run a new operation for the same MTA, you will not receive an error message that there is an ongoing process for the MTA and ask you if you want to abort it.

</td>
</tr>
<tr>
<td valign="top">

<code><i>-m &lt;module name&gt;</i></code>

</td>
<td valign="top">

Deploy only the module with the specified name.

> ### Note:  
> It can be used multiple times.



</td>
</tr>
<tr>
<td valign="top">

<code><i>--all-modules</i></code>

</td>
<td valign="top">

Deploy all modules.

> ### Note:  
> Any `-m` options are ignored.



</td>
</tr>
<tr>
<td valign="top">

<code><i>-r &lt;resource name&gt;</i></code>

</td>
<td valign="top">

Deploy only the resource with the specified name

> ### Note:  
> It can be used multiple times.



</td>
</tr>
<tr>
<td valign="top">

<code><i>--all-resources</i></code>

</td>
<td valign="top">

Deploy all resources.

> ### Note:  
> Any `-r` options are ignored.



</td>
</tr>
<tr>
<td valign="top">

<code><i>--strategy</i></code>

</td>
<td valign="top">

Announce to the platform a special deployment approach, for example when performing a “blue-green” deployment. See [Blue-Green Deployment Strategy](../30-development/blue-green-deployment-strategy-7c83810.md).

Using this option, you will not be asked to manually confirm the deletion of the older version of the MTA applications. This means that the deployment process is performed without any interruptions and you are not prompted to confirm the switch of routes to the new version of the MTA applications.

</td>
</tr>
<tr>
<td valign="top">

<code><i>--skip-testing-phase</i></code>

</td>
<td valign="top">

When using the *\--strategy* option for “blue-green”, you can choose to skip the phase for testing and you will not be asked to manually confirm the deletion of the older version of the MTA applications. The deployment process is performed without any interruptions and you are not prompted to confirm the switch of routes to the new version of the MTA applications.

> ### Note:  
> This option is equivalent to *\--no-confirm* from “bg-deploy”.



</td>
</tr>
<tr>
<td valign="top">

<code><i>--namespace</i></code>

> ### Note:  
> This option is currently experimental.



</td>
<td valign="top">

Namespace for the MTA. They are also applied to the application and service names. For more information, see [\(Experimental\) Namespaces](../30-development/experimental-namespaces-b28fd77.md).

</td>
</tr>
<tr>
<td valign="top">

<code><i>--apply-namespace-app-names true/false</i></code>

> ### Note:  
> This option is currently experimental.



</td>
<td valign="top">

Apply namespace to application names. If the namespace value is not provided in the CLI options, it is not applied.

> ### Note:  
> This is applied on all applications.



</td>
</tr>
<tr>
<td valign="top">

<code><i>--apply-namespace-service-names true/false</i></code>

> ### Note:  
> This option is currently experimental.



</td>
<td valign="top">

Apply namespace to service names. If the namespace value is not provided in the CLI options, it is not applied.

> ### Note:  
> This is applied on all services.



</td>
</tr>
<tr>
<td valign="top">

<code><i>--apply-namespace-app-routes true/false</i></code>

> ### Note:  
> This option is currently experimental.



</td>
<td valign="top">

Apply namespace to application routes. If the namespace value is not provided in the CLI options, it is not applied.

> ### Note:  
> This is applied on all application routes.



</td>
</tr>
<tr>
<td valign="top">

<code><i>--apply-namespace-as-suffix true/false</i></code>

> ### Note:  
> This option is currently experimental.



</td>
<td valign="top">

Apply namespace as suffix. If the namespace value is not provided in the CLI options, it is not applied.

> ### Note:  
> This is applied on all applications, services, and application routes.



</td>
</tr>
<tr>
<td valign="top">

<code><i>--skip-idle-start</i></code>

> ### Note:  
> This option is currently experimental.



</td>
<td valign="top">

When using the *\--strategy* option for “blue-green”, you can choose to skip the starting of the newly deployed applications on idle routes. This means that the newly deployed applications will be mapped directly to live routes. Under the hood this option includes *\--skip-testing-phase*.

</td>
</tr>
</table>

> ### Note:  
> -   If any of the options `-m`, `--all-modules`, `-r`, `--all-resource` is used, only the specified modules and resources will be deployed. Otherwise, everything will be deployed by default.
> -   If the options for the module deploying \( `-m`, `--all-modules`\) are used, the modules need to contain a `path` element on an MTA module level, which points to the content of the module. In case the module has some `requires` dependency section to a resource that needs a configuration file, then the `requires` section should have a `path` parameter, which points to the configuration file.
> -   If the options for the resource deploying \(`-r`, `--all-resource`\) are used, then any resources that have some configuration files need to contain a `path` parameter in their parameters section, which points to the configuration file.
> -   The `path` element or parameter value should be relative to the MTA directory.
> 
> An example of an MTA deployment descriptor, containing all variants of the `path` elements and parameters can be found at [Defining Multitarget Application Deployment Descriptors for Cloud Foundry](../30-development/defining-multitarget-application-deployment-descriptors-for-cloud-foundry-f48880b.md).



<a name="loio65ddb1b51a0642148c6b468a759a8a2e__section_lmg_5p4_kv"/>

## bg-deploy

Deploy a new Multitarget Application \(MTA\) using “blue-green” \(zero-downtime\) deployment.

> ### Note:  
> You can also perform this deployment type using the <code><i>deploy</i></code> command by using the experimental <code><i>--strategy blue-green</i></code> flag. See above for details.

“Blue-green” deployment is a release technique that reduces application downtime and the resulting risk by running two identical target deployment environments called “blue” and “green”. Only one of the two target environments is “live” at any point in time and it is much easier to roll back to a previous version after a failed \(or undesired\) deployment.



### Usage

Deploy a new Multitarget Application using “blue-green” deployment:

```
cf bg-deploy <MTA_ARCHIVE>  
[-e <EXT_DESCRIPTOR_1>[,<EXT_DESCRIPTOR_2>]] 
[-u <URL>] [-t <TIMEOUT>] [-v <VERSION_RULE>]
[--no-start] [--use-namespaces] [--no-namespaces-for-services]
[--delete-services] [--delete-service-keys] [--delete-service-brokers] 
[--keep-files] [--no-restart-subscribed-apps] [--no-confirm] [--do-not-fail-on-missing-permissions][--skip-idle-start]
cf deploy ...[--retries <RETRIES>]
```

Interact with an active MTA deploy operation, for example, by performing an action:

```
cf bg-deploy  [-i <OPERATION_ID>] [-a <ACTION>] 
```



### Arguments

**Command Arguments Overview**


<table>
<tr>
<th valign="top">

Argument

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

*<MTA\_ARCHIVE\>*

or

*<DIRECTORY\_PATH\>*

</td>
<td valign="top">

The path to \(and name of\) the archive or the path to the directory containing the Multitarget Application to deploy. The application archive must have the format \(and file extension\) `mtar`, for example, `MTApp1.mtar`; the specified directory can be specified as a path \(for example, `myApp/` or `.` \(current directory\).

</td>
</tr>
<tr>
<td valign="top">

*<--retries\>*

</td>
<td valign="top">

Retry the operation specified number of times in case a non-content error \(default 3\).

</td>
</tr>
</table>



### Options

**Command Options Overview**


<table>
<tr>
<th valign="top">

Option

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

<code><i>-e</i> <i class="varname">&lt;EXT_DESCRIPTOR_1&gt;</i>[,<i class="varname">&lt;EXT_DESCRIPTOR_2&gt;</i>]</code>

</td>
<td valign="top">

Define one or more extensions to the deployment descriptors; multiple extension descriptors must be separated by commas.

</td>
</tr>
<tr>
<td valign="top">

<code><i>-u</i> <i class="varname">&lt;URL&gt;</i></code>

</td>
<td valign="top">

Specify the URL for the deployment-service end-point that is to be used for the deployment operation

</td>
</tr>
<tr>
<td valign="top">

<code><i>-t</i> <i class="varname">&lt;TIMEOUT&gt;</i></code>

</td>
<td valign="top">

Specify the maximum amount of time \(in seconds\) that the service must wait for before starting the deployed application

</td>
</tr>
<tr>
<td valign="top">

<code><i>-v</i> <i class="varname">&lt;VERSION_RULE&gt;</i></code>

</td>
<td valign="top">

Specify the rule to apply to determine how the application version number is used to trigger an application-update deployment operation, for example: “`HIGHER`”, “`SAME_HIGHER`”, or “`ALL`”.

</td>
</tr>
<tr>
<td valign="top">

<code><i>-i</i> <i class="varname">&lt;OPERATION_ID&gt;</i></code>

</td>
<td valign="top">

Specify the ID of the deploy operation that you want to perform an action on

</td>
</tr>
<tr>
<td valign="top">

<code><i>-a</i> <i class="varname">&lt;ACTION&gt;</i></code>

</td>
<td valign="top">

Specify the action to perform on the deploy operation, for example, “abort”, “retry”, or “monitor”, or “resume”

</td>
</tr>
<tr>
<td valign="top">

<code><i>-f</i> </code>

</td>
<td valign="top">

Force deploy without requiring any confirmation for aborting any conflicting processes

</td>
</tr>
<tr>
<td valign="top">

<code><i>--no-start</i></code>

</td>
<td valign="top">

Do not start application after deployment

</td>
</tr>
<tr>
<td valign="top">

<code><i>--use-namespaces</i></code>

</td>
<td valign="top">

Use namespaces in application \(and service\) names during application deployment

</td>
</tr>
<tr>
<td valign="top">

<code><i>--no-namespaces-for-services</i></code>

</td>
<td valign="top">

Do not use namespaces in service names

</td>
</tr>
<tr>
<td valign="top">

<code><i>--delete-services</i></code>

</td>
<td valign="top">

Re-create changed services and delete discontinued services

</td>
</tr>
<tr>
<td valign="top">

<code><i>--delete-service-keys</i></code>

</td>
<td valign="top">

Delete the existing service keys and apply the new ones

</td>
</tr>
<tr>
<td valign="top">

<code><i>--delete-service-brokers</i></code>

</td>
<td valign="top">

Delete discontinued service brokers

</td>
</tr>
<tr>
<td valign="top">

<code><i>--keep-files</i></code>

</td>
<td valign="top">

Keep the files used for deployment

</td>
</tr>
<tr>
<td valign="top">

<code><i>--no-restart-subscribed-apps</i></code>

</td>
<td valign="top">

Do not restart subscribed applications that are updated during the deployment

</td>
</tr>
<tr>
<td valign="top">

<code><i>--no-confirm</i></code>

</td>
<td valign="top">

Use this option to turn off the manual confirmation for deleting the older version of the MTA applications. Thus the deployment process is performed from start to finish uninterrupted, and you are not prompted to confirm the switch of routes to the new version of the MTA applications.

</td>
</tr>
<tr>
<td valign="top">

<code><i>--do-not-fail-on-missing-permissions</i></code>

</td>
<td valign="top">

Perform the deployment, even if required administrator permissions are missing for some operations \(for example, the creation of service brokers\).

</td>
</tr>
<tr>
<td valign="top">

<code><i>--abort-on-error</i></code>

</td>
<td valign="top">

If an operation fails, the corresponding process is automatically aborted and cannot be retried using the option *\-a retry*

</td>
</tr>
<tr>
<td valign="top">

<code><i>-m &lt;module name&gt;. However, if you run a new operation for the same MTA, you will not receive an error message that there is an ongoing process for the MTA and ask you if you want to abort it.</i></code>

</td>
<td valign="top">

Deploy only the module with the specified name.

> ### Note:  
> It can be used multiple times.



</td>
</tr>
<tr>
<td valign="top">

<code><i>--all-modules</i></code>

</td>
<td valign="top">

Deploy all modules.

> ### Note:  
> Any `-m` options are ignored.



</td>
</tr>
<tr>
<td valign="top">

<code><i>-r &lt;resource name&gt;</i></code>

</td>
<td valign="top">

Deploy only the resource with the specified name

> ### Note:  
> It can be used multiple times.



</td>
</tr>
<tr>
<td valign="top">

<code><i>--all-resources</i></code>

</td>
<td valign="top">

Deploy all resources.

> ### Note:  
> Any `-r` options are ignored.



</td>
</tr>
<tr>
<td valign="top">

*\--skip-idle-start*

> ### Note:  
> This option is currently experimental.



</td>
<td valign="top">

You can choose to skip the starting of the newly deployed applications on idle routes. This means that the newly deployed applications will be mapped directly to live routes. Under the hood this option includes *\--no-confirm*.

</td>
</tr>
</table>

> ### Note:  
> -   If any of the options `-m`, `--all-modules`, `-r`, `--all-resource` is used, only the specified modules and resources will be deployed. Otherwise, everything will be deployed by default.
> -   If the options for the module deploying \( `-m`, `--all-modules`\) are used, the modules need to contain a `path` element on an MTA module level, which points to the content of the module. In case the module has some `requires` dependency section to a resource that needs a configuration file, then the `requires` section should have a `path` parameter, which points to the configuration file.
> -   If the options for the resource deploying \(`-r`, `--all-resource`\) are used, then any resources that have some configuration files need to contain a `path` parameter in their parameters section, which points to the configuration file.
> -   The `path` element or parameter value should be relative to the MTA directory.
> 
> See the complete procedure in section [Legacy Blue-Green Deployment](../30-development/legacy-blue-green-deployment-764308c.md).
> 
> An example of an MTA deployment descriptor, containing all variants of the `path` elements and parameters can be found at [Defining Multitarget Application Deployment Descriptors for Cloud Foundry](../30-development/defining-multitarget-application-deployment-descriptors-for-cloud-foundry-f48880b.md).



<a name="loio65ddb1b51a0642148c6b468a759a8a2e__section_axl_phv_kt"/>

## undeploy

Undeploy a Multitarget Application \(MTA\), or interact with an undeploy MTA operation.



### Usage

Undeploy an MTA.

```
cf undeploy <MTA_ID>  
[-u <URL>] [-f] 
[--delete-services] [--delete-service-keys] [--delete-service-brokers] [--no-restart-subscribed-apps] 
[--do-not-fail-on-missing-permissions]
cf deploy ...[--retries <RETRIES>]
```

Interact with an undeploy MTA operation, for example, by performing an action.

```
cf undeploy [-i <UNDEPLOY_ID>] [-a <ACTION>]
```



### Arguments

**Command Arguments Overview**


<table>
<tr>
<th valign="top">

Argument

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

*<MTA\_ID\>*

</td>
<td valign="top">

The ID of the MTA you want to undeploy

</td>
</tr>
<tr>
<td valign="top">

*<--retries\>*

</td>
<td valign="top">

Retry the operation specified number of times in case a non-content error \(default 3\).

</td>
</tr>
</table>



### Options

**Command Options Overview**


<table>
<tr>
<th valign="top">

Option

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

<code><i>-u</i> <i class="varname">&lt;URL&gt;</i></code>

</td>
<td valign="top">

Specify the URL for the service end-point that is to be used for the undeployment operation

</td>
</tr>
<tr>
<td valign="top">

<code><i>-i</i> <i class="varname">&lt;OPERATION_ID&gt;</i></code>

</td>
<td valign="top">

Specify the ID of the undeploy operation that you want to perform an action on

</td>
</tr>
<tr>
<td valign="top">

<code><i>-a</i> <i class="varname">&lt;ACTION&gt;</i></code>

</td>
<td valign="top">

Specify the action to perform on the undeploy operation, for example, “abort”, “retry”, or “monitor”

</td>
</tr>
<tr>
<td valign="top">

<code><i>-f</i> </code>

</td>
<td valign="top">

Force completion of the undeploy operation without any system prompt or confirmation

</td>
</tr>
<tr>
<td valign="top">

<code><i>--delete-services</i> </code>

</td>
<td valign="top">

Delete any related services

</td>
</tr>
<tr>
<td valign="top">

<code><i>--delete-service-brokers</i> </code>

</td>
<td valign="top">

Delete discontinued service brokers

</td>
</tr>
<tr>
<td valign="top">

<code><i>--no-restart-subscribed-apps</i></code>

</td>
<td valign="top">

Do not restart subscribed applications that are updated during the deployment

</td>
</tr>
<tr>
<td valign="top">

<code><i>--do-not-fail-on-missing-permissions</i></code>

</td>
<td valign="top">

Perform the deployment, even if required administrator permissions are missing for some operations \(for example, the creation of service brokers\).

</td>
</tr>
<tr>
<td valign="top">

<code><i>--abort-on-error</i></code>

</td>
<td valign="top">

If an operation fails, the corresponding process is automatically aborted and cannot be retried using the option *\-a retry*. However, if you run a new operation for the same MTA, you will not receive an error message that there is an ongoing process for the MTA and ask you if you want to abort it.

</td>
</tr>
<tr>
<td valign="top">

<code><i>--delete-service-keys</i></code>

</td>
<td valign="top">

Delete the existing service keys

</td>
</tr>
</table>



<a name="loio65ddb1b51a0642148c6b468a759a8a2e__section_hww_4hv_kt"/>

## mta

Display information about a Multitarget Application \(MTA\). The information displayed includes the requested state, the number of instances, information about allocated memory and disk space, as well as details regarding the bound service \(and service plan\).



### Usage

```
cf mta MTA_ID  
[-u <URL>]
```



### Arguments

**Command Arguments Overview**


<table>
<tr>
<th valign="top">

Argument

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

*<MTA\_ID\>* 

</td>
<td valign="top">

The ID of the MTA whose details you want to display

</td>
</tr>
</table>



### Options

**Command Options Overview**


<table>
<tr>
<th valign="top">

Option

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

<code><i>-u</i> <i class="varname">&lt;URL&gt;</i></code> 

</td>
<td valign="top">

Specify the URL for the deployment-service end-point to use to obtain details of the selected MTA

</td>
</tr>
</table>



<a name="loio65ddb1b51a0642148c6b468a759a8a2e__section_x3p_4hv_kt"/>

## mtas

Display information about all available Multitarget Applications \(MTA\).



### Usage

```
cf mtas [-u <URL>]
```



### Options

**Command Options Overview**


<table>
<tr>
<th valign="top">

Option

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

<code><i>-u</i> <i class="varname">&lt;URL&gt;</i></code> 

</td>
<td valign="top">

Specify the URL for the deployment-service end-point to use to obtain details of the selected MTA

</td>
</tr>
</table>



<a name="loio65ddb1b51a0642148c6b468a759a8a2e__section_cpf_rkk_vt"/>

## mta-ops

Display information about all **active** operations for Multitarget Applications \(MTA\). The information includes the ID, type, status, the time the MTA-related operation started, as well as the name of the user that started the operation.



### Usage

```
cf mta-ops [--mta <MTA>] [-u <URL>] [--last <NUM>] [--all]
```



### Options

**Command Options Overview**


<table>
<tr>
<th valign="top">

Option

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

<code><i>-u</i> <i class="varname">&lt;URL&gt;</i></code>

</td>
<td valign="top">

Specify the URL for the deployment-service end-point to use to obtain details of the selected MTA operations

</td>
</tr>
<tr>
<td valign="top">

<code><i>--last</i> <i class="varname">&lt;NUM&gt;</i></code>

</td>
<td valign="top">

List the last *<NUM\>* active MTA operations

</td>
</tr>
<tr>
<td valign="top">

<code><i>--all</i></code>

</td>
<td valign="top">

List all active MTA operations

</td>
</tr>
<tr>
<td valign="top">

<code><i>– mta &lt;MTA&gt;</i></code>

</td>
<td valign="top">

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
cf download-mta-op-logs -i <OPERATION_ID> [-u <URL>] [-d <DIRECTORY>]
```

-   ```
cf download-mta-op-logs --mta <MTA> [ --last <NUM>] [ -u <URL>] [ -d <DIRECTORY>]
```


> ### Tip:  
> You can use the alias `dmol` in place of the `download-mta-op-logs` command.



### Options

**Command Options Overview**


<table>
<tr>
<th valign="top">

Option

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

<code><i>-u</i> <i class="varname">&lt;URL&gt;</i></code>

</td>
<td valign="top">

Specify the URL for the deployment-service end-point to use to obtain details of the selected MTA operations

</td>
</tr>
<tr>
<td valign="top">

<code><i>-i</i> <i class="varname">&lt;OPERATION_ID&gt;</i></code>

</td>
<td valign="top">

Specify the identity \(ID\) of the MTA operation whose logs you want to download

</td>
</tr>
<tr>
<td valign="top">

<code><i>-d</i> <i class="varname">&lt;DIRECTORY&gt;</i></code>

</td>
<td valign="top">

Specify the path to the location where you want to save the downloaded MTA operation logs; by default, the location is <code>./mta-op-<i class="varname">&lt;OPERATION_ID&gt;</i>/</code>

</td>
</tr>
<tr>
<td valign="top">

<code><i>--mta</i><i class="varname">&lt;MTA&gt;</i></code>

</td>
<td valign="top">

Specify the MTA whose logs you want to download.

> ### Note:  
> This option is not compatible with the *\-i* option.



</td>
</tr>
<tr>
<td valign="top">

<code><i>--last</i><i class="varname">&lt;NUM&gt;</i></code>

</td>
<td valign="top">

Download the last <NUM\> logs for the specified MTA.

</td>
</tr>
</table>



<a name="loio65ddb1b51a0642148c6b468a759a8a2e__section_jxk_n4p_wx"/>

## purge-mta-config

Purge all configuration entries and subscriptions, which are no longer valid.



### Usage

```
cf purge-mta-config   
[-u <URL>]
```

Invalid configuration entries are often produced when the application that is providing configuration entries is deleted by the user without using the deploy-service, for example, the `cf delete` command . In this case, the configuration remains in the deploy-service database even though the corresponding application is no longer available. This could lead to a failure during subsequent attempts to resolve the configuration entries.



### Options

**Command Options Overview**


<table>
<tr>
<th valign="top">

Option

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

<code><i>-u</i> <i class="varname">&lt;URL&gt;</i></code> 

</td>
<td valign="top">

The URL of the deploy service

</td>
</tr>
</table>

**Related Information**  


[MultiApps CLI plugin](https://github.com/cloudfoundry-incubator/multiapps-cli-plugin)

[Cloud Foundry multitarget аpplication еxamples repository](https://github.com/SAP-samples/cf-mta-examples)

[Deploy an MTA archive referenced by a remote URL](https://github.com/SAP-samples/cf-mta-examples/tree/master/deploy-with-url)

