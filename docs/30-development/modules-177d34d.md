<!-- loio177d34d45e3d4fd99f4eeeffc5814cf1 -->

# Modules

The `modules` section of the deployment descriptor lists the deployable parts contained in the MTA deployment archive.

The following elements are mandatory:

-   `name` - must be unique within the MTA it identifies

-   `type` - defines which deployment mechanism to be used for this module

Optional module attributes include:

-   `path` - the file-system path relative to the root of the MTA directory. The content of the file is used to create or update the CF app or content, depending on the module target. The `path` is used only during MTA build. In an already built MTA archive \(MTAR\), path is ignored and only corresponding entry in `MANIFEST.MF` for the module is processed.

    The path is applicable only when MTA is assembled based on deployment descriptor \(mtad.yaml\), and not on development descriptor \(mta.yaml\)

-   `description` - non-translatable, free-text string; the string is not meant to be presented on application user interfaces \(UI\)
-   `properties` - a structured set of name-value pairs; if a module, which requires the resource, represents a CF application, the resource properties are injected into the environment of the application
-   `parameters` - reserved variables that affect the behavior of the MTA-aware tools, such as the deployer
-   `deployed-after` - the attribute is used to create an order, in which modules should be processed. If a module has this attribute, it will be processed after the other modules in a higher position are processed. The attribute value is a structured set of a list comprised of other module names of the same MTA.
-   `requires` - specifies the names of `requires` sections provided in `resource` that have been declared for the same MTA. Tools check if all required names are provided within the MTA.
-   `provides` - specifies the names of `provides` sections, each containing configuration data; the data provided can be `required` by other `modules` in the same MTA

> ### Tip:  
> Modules can be deployed in parallel. See [Parallel Module Deployment](parallel-module-deployment-0384158.md).



<a name="loio177d34d45e3d4fd99f4eeeffc5814cf1__section_mtaModuleTypes"/>

## MTA Module Types

Modify the following MTA module types by providing specific properties or parameters in the MTA deployment descriptor \(`mtad.yaml`\).

**MTA Default Modules Types**


<table>
<tr>
<th valign="top">

Module Type

</th>
<th valign="top">

Default Parameter Values and Description

</th>
<th valign="top">

Module Properties

</th>
<th valign="top">

Result

</th>
</tr>
<tr>
<td valign="top">

`javascript.nodejs`

</td>
<td valign="top">

No default parameter.

> ### Note:  
> We strongly recommend that you specify the appropriate buildpack for your application.modules: parameters: buildpack: binary\_buildpack To do so, use the `buildpack` - name: my-binary-app module parameter.



</td>
<td valign="top">

None

</td>
<td valign="top">

CF application with automatic buildpack detection

</td>
</tr>
<tr>
<td valign="top">

`nodejs`

</td>
<td valign="top">

`buildpack`\(`nodejs_buildpack`\)

</td>
<td valign="top">

None

</td>
<td valign="top">

CF application with Node.js runtime

</td>
</tr>
<tr>
<td valign="top">

`custom`

</td>
<td valign="top">

No default parameter.

> ### Note:  
> We strongly recommend that you specify the appropriate buildpack for your application. To do so, use the `buildpack` module parameter.



</td>
<td valign="top">

None

</td>
<td valign="top">

CF application with automatic buildpack detection

</td>
</tr>
<tr>
<td valign="top">

`application`

</td>
<td valign="top">

No default parameter.

> ### Note:  
> We strongly recommend that you specify the appropriate buildpack for your application. To do so, use the `buildpack` module parameter.



</td>
<td valign="top">

None

</td>
<td valign="top">

CF application with automatic buildpack detection

</td>
</tr>
<tr>
<td valign="top">

`java`

</td>
<td valign="top">

`buildpack` \(`sap_java_buildpack_jakarta`\)

</td>
<td valign="top">

None

</td>
<td valign="top">

CF application with Automatic runtime detection by `sap_java_buildpack_jakarta`

</td>
</tr>
<tr>
<td valign="top">

`java.tomcat`

</td>
<td valign="top">

`buildpack` \(`sap_java_buildpack_jakarta`\)

</td>
<td valign="top">

None

</td>
<td valign="top">

CF application with Tomcat runtime of `sap_java_buildpack_jakarta`

</td>
</tr>
<tr>
<td valign="top">

`java.tomee`

</td>
<td valign="top">

`buildpack` \(`sap_java_buildpack_jakarta`\)

</td>
<td valign="top">

None

</td>
<td valign="top">

CF application with Automatic runtime detection by `sap_java_buildpack_jakarta`

</td>
</tr>
<tr>
<td valign="top">

`com.sap.xs.hdi`

</td>
<td valign="top">

-   `no-route` \(`true`\)

    Do not assign a route to the application.

-   `memory` \(`256MB`\)
-   `health-check-type` - \(`none`\)
-   `no-start (true)`
-   `cf-task`
-   `command (npm start)`
-   `memory (256MB)`
-   `name (deploy)`
-   `dependency-type` \(`hard`\)

    In circular module-dependencies, deploy modules with dependency type “hard” first

-   `buildpack``(nodejs_buildpack)`



</td>
<td valign="top">

`EXIT (1)`

</td>
<td valign="top">

CF application with HDI content activation

</td>
</tr>
<tr>
<td valign="top">

`com.sap.xs.hdi-dynamic`

</td>
<td valign="top">

`buildpack`\(`nodejs_buildpack`\)

</td>
<td valign="top">

None

</td>
<td valign="top">

CF application with Node.js runtime

</td>
</tr>
<tr>
<td valign="top">

`com.sap.portal.content`

</td>
<td valign="top">

> ### Note:  
> Before using this module type, update the content deployer applications to their latest version.

-   `no-route` \(`true`\). Defines if a route should be assigned to the application.
-   `no-start` - \(`true`\). Only the one-off tasks will be executed, that is, without triggering the start of the application.
-   `memory` \(`256M`\). Defines the memory allocated to the application.
-   `tasks` \(`name:deploy, memory:256M, command:npm start)`

    For more information, see [Tasks](tasks-a1c184c.md).

-   `dependency-type`\(`hard`\). Defines if this module should be deployed first, if it takes part in circular module dependency cycles. If `hard` means that this module is deployed first.
-   `buildpack``(nodejs_buildpack)`



</td>
<td valign="top">

None

</td>
<td valign="top">

CF application with SAP Fiori launchpad content

</td>
</tr>
<tr>
<td valign="top">

`com.sap.portal.site-content`

</td>
<td valign="top">

> ### Note:  
> This module type is **deprecated**.
> 
> You have to use `com.sap.portal.content` instead.



</td>
<td valign="top">

None

</td>
<td valign="top">

CF application with SAP Fiori launchpad content

</td>
</tr>
<tr>
<td valign="top">

`com.sap.application.content`

</td>
<td valign="top">

Required dependency parameters:

-   `content-target(false)`

    Specify that the resource would be used as a target for the module content deployment.




</td>
<td valign="top">

None

</td>
<td valign="top">

Direct content deployment to backing services

</td>
</tr>
<tr>
<td valign="top">

`com.sap.html5.application-content`

</td>
<td valign="top">

> ### Note:  
> This module type is **deprecated**. Please use `com.sap.html5.application.content` instead.

> ### Note:  
> Keep the dependency to `@sap/html5-app-deployer` updated to the latest version. If you are using an older version, you might encounter some issues.

-   `no-route` \(`true`\). Defines if a route should be assigned to the application.
-   `memory` \(`256M`\). Defines the memory allocated to the application.
-   `execute-app` - \(`true`\). Defines whether the application is executed. If yes, the application performs certain amount of work and upon completion sets a `success-marker` or `failure-marker` by means of a log message.
-   `success-marker` \(`STDOUT:The deployment of html5 application content done.*)`
-   `failure-marker`\(`STDERR:The deployment of html5 application content failed.*`\)
-   `stop-app` \(`true`\). Defines if the application should be stopped after execution.
-   `check-deploy-id` \(`true`\) - Defines if the deployment \(process\) ID should also be checked when checking the application execution status.
-   `dependency-type`\(`hard`\). Defines if this module should be deployed first, if it takes part in circular module dependency cycles. If `hard` means that this module is deployed first.
-   `health-check-type`\(none\). Defines if the module should be monitored for availability.
-   `buildpack``(nodejs_buildpack)`



</td>
<td valign="top">

None

</td>
<td valign="top">

Deploys a content deployment application, and creates a task that performs the content deployment.

</td>
</tr>
<tr>
<td valign="top">

`com.sap.html5.application.content`

</td>
<td valign="top">

> ### Note:  
> Keep the dependency to `@sap/html5-app-deployer` updated to the latest version. If you are using an older version, you might encounter some issues.

-   `no-route` \(`true`\). Defines if a route should be assigned to the application.
-   `no-start` - \(`true`\). Only the one-off tasks will be executed, that is, without triggering the start of the application.
-   `memory` \(`256M`\). Defines the memory allocated to the application.
-   `tasks` \(`name:deploy, memory:256M, command:npm start)`

    For more information, see [Tasks](tasks-a1c184c.md).

-   `dependency-type`\(`hard`\). Defines if this module should be deployed first, if it takes part in circular module dependency cycles. If `hard` means that this module is deployed first.
-   `buildpack``(nodejs_buildpack)`



</td>
<td valign="top">

`EXIT (1)`

</td>
<td valign="top">

CF application with SAP HTML5 content

</td>
</tr>
<tr>
<td valign="top">

`staticfile`

</td>
<td valign="top">

`buildpack` \(`staticfile_buildpack`\)

</td>
<td valign="top">

None

</td>
<td valign="top">

CF application with static file runtime

</td>
</tr>
<tr>
<td valign="top">

`go`

</td>
<td valign="top">

`buildpack`\(`go_buildpack`\)

</td>
<td valign="top">

None

</td>
<td valign="top">

CF application with Go runtime

</td>
</tr>
<tr>
<td valign="top">

`python`

</td>
<td valign="top">

`buildpack`\(`python_buildpack`\)

</td>
<td valign="top">

None

</td>
<td valign="top">

CF application with Python runtime

</td>
</tr>
<tr>
<td valign="top">

`php`

</td>
<td valign="top">

`buildpack`\(`php_buildpack`\)

</td>
<td valign="top">

None

</td>
<td valign="top">

CF application with PHP runtime

</td>
</tr>
<tr>
<td valign="top">

`binary`

</td>
<td valign="top">

`buildpack`\(`binary_buildpack`\)

</td>
<td valign="top">

None

</td>
<td valign="top">

CF application with Binary runtime

</td>
</tr>
</table>

To choose a `binary_buildpack`, define it by using the following:

> ### Sample Code:  
> ```
> modules:
>   - name: my-binary-app
>     type: custom
>     parameters:
>       buildpack: binary_buildpack
> ```



<a name="loio177d34d45e3d4fd99f4eeeffc5814cf1__section_moduleSpecificParameters"/>

## Module-Specific Parameters

Module parameters have platform-specific semantics. To reference a parameter value, use the placeholder notation <code>${<i class="varname">&lt;parameter&gt;</i>}</code>, for example, `${default-host}`.

> ### Tip:  
> It is also possible to declare metadata for parameters and properties defined in the MTA deployment description; the mapping is based on the parameter or property keys. For example, you can specify if a parameter is **required** \(`optional: false`\) or can be modified `overwritable: true`.

The following parameters are supported:

> ### Note:  
> If you can't find a specific parameter from the native Cloud Foundry manifest here, refer to [Prerequisites and Restrictions](multitarget-applications-in-the-cloud-foundry-environment-d04fc0e.md#loiod04fc0e2ad894545aebfd7126384307c__section_ph2_r5h_1cb) to see which Cloud Foundry features are currently not supported.

**MTA Development and Deployment Module Parameters**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Read-Only \(System\)

</th>
<th valign="top">

Description

</th>
<th valign="top">

Default Value

</th>
<th valign="top">

Example

</th>
</tr>
<tr>
<td valign="top">

`app-name`

</td>
<td valign="top">

 

</td>
<td valign="top">

The name of the application in the Cloud Foundry environment to be deployed for this module, based on the module name

</td>
<td valign="top">

`${default-app-name}`

</td>
<td valign="top">

`node-hello-world`

`com.sap.xs2.samples.xsjshelloworld.node-hello-world`

</td>
</tr>
<tr>
<td valign="top">

`apply-namespace`

</td>
<td valign="top">

Write

</td>
<td valign="top">

Applies namespace to the application name. When you set `apply-namespace` to the application name and do not specify `apply-namespace` for its route, the namespace is applied to both the application name and its route. If the `namespace` value is not provided in the CLI options, it is not applied. For more information, see [Fine-Grained Configuration](experimental-namespaces-b28fd77.md#loiob28fd77836d44bde8c404618bf0f1228__section_hmf_khn_xcc).

</td>
<td valign="top">

 

</td>
<td valign="top">

```
modules:
- name: java
     ...
  parameters:
	apply-namespace: true 
   
```



</td>
</tr>
<tr>
<td valign="top">

`buildpack`

</td>
<td valign="top">

 

</td>
<td valign="top">

The name or the URL of a custom buildpack required by the application

</td>
<td valign="top">

Empty, or as specified in the deploy service configuration

</td>
<td valign="top">

`buildpack: git://github.acme.com/xs2-java/xs2javabuildpack` 

</td>
</tr>
<tr>
<td valign="top">

`buildpacks`

</td>
<td valign="top">

 

</td>
<td valign="top">

An array of buildpacks. If a buildpack parameter already exists, it will be overwritten by the buildpacks listed in the buildpacks parameter, so that you have to include it in the array.

</td>
<td valign="top">

Empty, or as specified in the deploy service configuration

</td>
<td valign="top">

`buildpacks: [java_buildpack, nodejs_buildpack, staticfile_buildpack]` 

</td>
</tr>
<tr>
<td valign="top">

`command`

</td>
<td valign="top">

 

</td>
<td valign="top">

A custom command required to start the application

</td>
<td valign="top">

Empty, or as specified in the deploy service configuration

</td>
<td valign="top">

`command: node index.js` 

</td>
</tr>
<tr>
<td valign="top">

`create-service-broker`

</td>
<td valign="top">

 

</td>
<td valign="top">

Specifies whether \[true|false\] a service broker should be registered for the application module

</td>
<td valign="top">

`false`

</td>
<td valign="top">

`create-service-broker: true`

</td>
</tr>
<tr>
<td valign="top">

`default-app-name`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

The name of the application in the Cloud Foundry environment to be deployed for this module, based on the module name

</td>
<td valign="top">

The module name with or without a namespace prefix

</td>
<td valign="top">

`node-hello-world`

`com.sap.xs2.samples.xsjshelloworld.node-hello-world`

</td>
</tr>
<tr>
<td valign="top">

`default-host`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

The default host name, which is composed based on the module name to ensure uniqueness. Used with host-based routing to compose the default URI, see below. It follows the convention `${org}-${space}-<module_name>`.

> ### Tip:  
> We recommend you explicitly use the `routes` parameter. See [Routes](routes-53daaaf.md).

> ### Note:  
> Host names that do not comply with the Cloud Foundry naming limitations are automatically corrected:
> 
> -   Any characters that are not within the allowed `a-z` and `0-9` ranges are replaced by dashes \(-\) to prevent deployment issues.
> -   If the host name length exceeds 63 symbols, the name is shortened and its end is replaced with a hash code.

> ### Note:  
> When used in blue-green deployment the value is resolved depending on the phase. During the testing phase the "idle" suffix will be appended to the host. If you want to use the live version only, refer to `${default-live-host}`.



</td>
<td valign="top">

Generated as described in the description

</td>
<td valign="top">

`trial-a007007-node-hello-world`

</td>
</tr>
<tr>
<td valign="top">

`default-instances`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

The number of application instances that are started during the deployment

</td>
<td valign="top">

1

</td>
<td valign="top">

`default-instances: 1`

</td>
</tr>
<tr>
<td valign="top">

`default-live-app-name`

</td>
<td valign="top">

 

</td>
<td valign="top">

Valid for blue-green deployment. Specify this parameter if you want the name of the Cloud Foundry application that is to be deployed with this module to be based on the name of the module. For standard deployment the parameter will be the same as `default-app-name` regardless the phase.

</td>
<td valign="top">

The module name with or without a namespace prefix

</td>
<td valign="top">

`node-hello-world`

</td>
</tr>
<tr>
<td valign="top">

`default-live-domain`

</td>
<td valign="top">

 

</td>
<td valign="top">

Valid for blue-green deployment. The value of this parameter is the default domain for the current organization.

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

`default-live-host`

</td>
<td valign="top">

 

</td>
<td valign="top">

Valid for blue-green deployment. Specify this parameter if you want to use `${default-host}` without the “idle” suffix during the testing phase of the blue-green deployment.

</td>
<td valign="top">

Generated as described in the description

</td>
<td valign="top">

`trial-a007007-node-hello-world`

</td>
</tr>
<tr>
<td valign="top">

`default-live-uri`

</td>
<td valign="top">

 

</td>
<td valign="top">

Valid for blue-green deployment. Specify this parameter if you want to use `${default-uri}` without the “idle” suffix during the testing phase of the blue-green deployment.

</td>
<td valign="top">

Generated as described in the description

</td>
<td valign="top">

`trial-a007007-node-hello-world.cfapps.acme.ondemand.com`

</td>
</tr>
<tr>
<td valign="top">

`default-live-url`

</td>
<td valign="top">

 

</td>
<td valign="top">

Valid for blue-green deployment. Specify this parameter if you want to use `${default-url}` without the “idle” suffix during the testing phase of the blue-green deployment.

</td>
<td valign="top">

Generated as described in the description

</td>
<td valign="top">

`${protocol}://${default-live-uri}`

</td>
</tr>
<tr>
<td valign="top">

`default-uri`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

The default URI, composed as `${host}.${domain}` \(host-based routing\). Note that `${host}` will be the same as `${default-host}`, unless specified explicitly as a parameter. Similarly, `${domain}` would be the same as `${default-domain}`, unless specified explicitly.

> ### Note:  
> When used in blue-green deployment the value is resolved depending on the phase. During the testing phase the "idle" suffix will be appended to the host of the URI. If you want to use the live version only, refer to `${default-live-uri}`.



</td>
<td valign="top">

Generated as described in the description.

</td>
<td valign="top">

`trial-a007007-node-hello-world.cfapps.acme.ondemand.com`

</td>
</tr>
<tr>
<td valign="top">

`default-url`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

The default URL, composed as `${protocol}://${default-uri}`. Note that the `${default-uri}` placeholder is resolved as `${host}.${domain}` \(host-based routing\)

> ### Note:  
> When used in blue-green deployment the value is resolved depending on the phase. During the testing phase the "idle" suffix will be appended to the host of the URL. If you want to use the live version only, refer to `${default-live-url}`.



</td>
<td valign="top">

Generated as described in the description.

</td>
<td valign="top">

`${protocol}://${default-uri}`

</td>
</tr>
<tr>
<td valign="top">

`dependency-type`

</td>
<td valign="top">

 

</td>
<td valign="top">

Deployment order of modules with circular dependencies

</td>
<td valign="top">

soft

</td>
<td valign="top">

`dependency-type: hard`

`dependency-type: soft`

</td>
</tr>
<tr>
<td valign="top">

`disk-quota`

</td>
<td valign="top">

 

</td>
<td valign="top">

The disk space that will be available to the application. This parameter requires a unit of measurement M, MB, G, or GB in upper or lower case.

</td>
<td valign="top">

1, or as specified in module-type

</td>
<td valign="top">

`disk-quota: 1G`

</td>
</tr>
<tr>
<td valign="top">

`docker`

</td>
<td valign="top">

Write

</td>
<td valign="top">

Creates a module from a docker image. When using a docker image parameter, we do not need to specify the module in the `MANIFEST.mf` file. An image parameter is a docker image from the Docker Hub or somewhere else. The username and the password are optional, but if a Docker image from a private repository is uploaded, then they are mandatory.

When uploading a docker image, the content of a module is not needed.

</td>
<td valign="top">

n/a

</td>
<td valign="top">

> ### Sample Code:  
> ```
> modules:
>   name: foo
>   type: application
>     parameters:
>       docker:
>         image: cloudfoundry/test-app
>         username: <optional username>
>         password: <optional password>
> ```



</td>
</tr>
<tr>
<td valign="top">

`domain`

</td>
<td valign="top">

 

</td>
<td valign="top">

The domain on which the application is available later

</td>
<td valign="top">

`${default-domain}`

</td>
<td valign="top">

`domain: ${default-domain}.acme.com`

</td>
</tr>
<tr>
<td valign="top">

`domains`

</td>
<td valign="top">

 

</td>
<td valign="top">

The domains on which the application is available later. The resulting application routes are the Cartesian product of the domains and hosts. That is, a separate route for each host is constructed on each domain.

</td>
<td valign="top">

`domains: - ${default}`

</td>
<td valign="top">

`domains: - ${default-domain}.acme.com - test-${default-domain}.acme.com`

</td>
</tr>
<tr>
<td valign="top">

`default-domain`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

The value of this parameter is the default domain for the current organization.

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

`enable-ssh`

</td>
<td valign="top">

 

</td>
<td valign="top">

Enables use of SSH within an application. Supported for the Diego container runtime environment only.

</td>
<td valign="top">

n/a

</td>
<td valign="top">

`"enable-ssh": true`

`"enable-ssh": false`

</td>
</tr>
<tr>
<td valign="top">

`enable-parallel-service-bindings`

</td>
<td valign="top">

 

</td>
<td valign="top">

Enables or disables the parallel binding or unbinding of services during deployment. If disabled, the services are bound and unbound sequentially in the order provided in the deployment descriptor.

</td>
<td valign="top">

`true`

</td>
<td valign="top">

> ### Sample Code:  
> ```
> - name: <module name>
>   type: <module type>
>   parameters:
>     enable-parallel-service-bindings: false
> 
> ```



</td>
</tr>
<tr>
<td valign="top">

`health-check-http-endpoint`

</td>
<td valign="top">

 

</td>
<td valign="top">

If the `health-check-type` parameter is set to `http`, the controller will do a `GET` request to this endpoint. The application will be considered as healthy if the response is 200 OK.

</td>
<td valign="top">

If `health-check-type` is set to `http`, the default value is `/`, otherwise there is no default value.

</td>
<td valign="top">

`health-check-type: http`

`health-check-http-endpoint: /health`

</td>
</tr>
<tr>
<td valign="top">

`health-check-timeout`

</td>
<td valign="top">

 

</td>
<td valign="top">

The application health check timeout in seconds

</td>
<td valign="top">

n/a

</td>
<td valign="top">

`health-check-timeout:120`

</td>
</tr>
<tr>
<td valign="top">

`health-check-invocation-timeout`

</td>
<td valign="top">

 

</td>
<td valign="top">

The time period in seconds, within which the application health check should be automatically started. If the health check does not start within the defined time period, it is omitted, and the deployment process continues.

</td>
<td valign="top">

n/a

</td>
<td valign="top">

`health-check-invocation-timeout:16`

</td>
</tr>
<tr>
<td valign="top">

`health-check-type`

</td>
<td valign="top">

 

</td>
<td valign="top">

The application health check type

</td>
<td valign="top">

`port`

</td>
<td valign="top">

`health-check-type: port`

`health-check-type: http`

`health-check-type: process`

</td>
</tr>
<tr>
<td valign="top">

`host`

</td>
<td valign="top">

 

</td>
<td valign="top">

The hostname or subdomain where an application is available later.

If you want to create a wildcard hostname, use an asterisk in quotes \("\*"\).

</td>
<td valign="top">

`${default-host}`

</td>
<td valign="top">

`host: ${space}-node-hello-world`

`host: "*"`

</td>
</tr>
<tr>
<td valign="top">

`hosts`

</td>
<td valign="top">

 

</td>
<td valign="top">

The hostnames or subdomain where an application is available later.

If you want to create a wildcard hostname, use an asterisk in quotes \("\*"\).

</td>
<td valign="top">

`hosts: - ${host}`

</td>
<td valign="top">

```
modules:
- name: my-app
  type: application
  parameters:
	hosts:
  	- ${space}-node-hello-world 
       - "*" 
   
```



</td>
</tr>
<tr>
<td valign="top">

`idle-domain`

</td>
<td valign="top">

 

</td>
<td valign="top">

Valid for a blue-green deployment when a new application version is started on a temporary route.

Specify this parameter if you want to use another domain for temporary routes.

</td>
<td valign="top">

`${default-domain}`

</td>
<td valign="top">

```
modules:
  - name: app
    type: nodejs
    parameters:
        idle-domain: "<some.domain>"
```



</td>
</tr>
<tr>
<td valign="top">

`idle-domains`

</td>
<td valign="top">

 

</td>
<td valign="top">

Valid for a blue-green deployment when a new application version is started on several temporary routes.

Specify this parameter if you want to use other domains for temporary routes by listing them in an array.

</td>
<td valign="top">

`${default-domain}`

</td>
<td valign="top">

```
modules:
  - name: app
    type: nodejs
    parameters:
        idle-domains: ["<some.domain>", "<some.other.domain>"]
```



</td>
</tr>
<tr>
<td valign="top">

`idle-host`

</td>
<td valign="top">

 

</td>
<td valign="top">

Valid for a blue-green deployment when a new application version is started on a temporary route.

Specify this parameter if you want to use another host for a temporary route.

> ### Note:  
> The new application will start on a route comprised of the specified host and the default domain.



</td>
<td valign="top">

`${default-host}-idle`

</td>
<td valign="top">

```
modules:
  - name: app
    type: nodejs
    parameters:
        idle-host: "<some-hostname>"
```



</td>
</tr>
<tr>
<td valign="top">

`idle-hosts`

</td>
<td valign="top">

 

</td>
<td valign="top">

Valid for a blue-green deployment when a new application version is started on temporary routes.

Specify this parameter if you want to use other hosts for temporary routes by listing them in an array.

> ### Note:  
> The new application will start on routes comprised of the specified hosts and default domain.



</td>
<td valign="top">

`${default-host}-idle`

</td>
<td valign="top">

```
modules:
  - name: app
    type: nodejs
    parameters:
        idle-hosts: ["<some-hostname>", "<some-other-hostname>"]
```



</td>
</tr>
<tr>
<td valign="top">

`idle-routes`

</td>
<td valign="top">

 

</td>
<td valign="top">

Valid for a blue-green deployment when a new application version is started on temporary routes.

Specify this parameter if you want to use other routes for the application.

</td>
<td valign="top">

`${default-uri}-idle`

</td>
<td valign="top">

```
modules:
- name: app
  parameters:
    idle-routes: 
     - idle-route: "<your-first-idle-hostname.your.first.idle.domain>" 
     - idle-route: "<your-second-idle-hostname.your.second.idle.domain>"
```



</td>
</tr>
<tr>
<td valign="top">

`instances`

</td>
<td valign="top">

 

</td>
<td valign="top">

The number of application instances that will be started during the deployment

</td>
<td valign="top">

`${default-instances}`

</td>
<td valign="top">

`instances: 2`

</td>
</tr>
<tr>
<td valign="top">

`keep-existing`

</td>
<td valign="top">

 

</td>
<td valign="top">

Defines the application attributes which will be kept after the deployment or blue-green deployment has finished. The supported attributes which could be kept are application environment, application bindings and application routes. If not specified, the default values are false, which indicates that each application attribute will be updated with the new values presented in the deployment descriptor.

</td>
<td valign="top">

`false`

</td>
<td valign="top">

> ### Sample Code:  
> ```
> keep-existing:
>   env: true
>   service-bindings: true
>   routes: false
> ```



</td>
</tr>
<tr>
<td valign="top">

`keep-existing-routes`

</td>
<td valign="top">

Write

</td>
<td valign="top">

When specified on module level, it indicates if the existing routes of the module's corresponding application should be kept even if they are not defined within the deployment and/or extension descriptors.

When specified on global level, under the `parameters` section of the descriptor, it indicates if the existing routes of all applications within that MTA should be kept.

> ### Note:  
> -   The module-level variant of the parameter has priority over the global parameter.
> -   This parameter is typically used when users want to keep the routes they have mapped manually by using the `cf map-route` command. We discourage this approach, as manual operations could lead to inconsistent deployment results and difficult troubleshooting. We recommend you to define all routes in the deployment and/or extension descriptors, which allows for their automatic management.



</td>
<td valign="top">

`false`

</td>
<td valign="top">

> ### Sample Code:  
> ```
> parameters:
>   keep-existing-routes: true
> modules:
>     - name: foo
>     type: nodejs
>     parameters:
>       keep-existing-routes: false 
>     - name: bar
>     type: nodejs
>   - name: baz
>     type: nodejs
> ```



</td>
</tr>
<tr>
<td valign="top">

`memory`

</td>
<td valign="top">

 

</td>
<td valign="top">

The memory limit for all instances of an application. This parameter requires a unit of measurement M, MB, G, or GB in upper or lower case.

</td>
<td valign="top">

256M, or as specified in module-type

</td>
<td valign="top">

`memory: 128M`

</td>
</tr>
<tr>
<td valign="top">

`no-route`

</td>
<td valign="top">

Write

</td>
<td valign="top">

Configures the deployer to create or skip the creation of a route for the application described by the module

</td>
<td valign="top">

false

</td>
<td valign="top">

`no-route: true`

</td>
</tr>
<tr>
<td valign="top">

`no-start`

</td>
<td valign="top">

 

</td>
<td valign="top">

Start/do not start the application during deployment.

> ### Tip:  
> This parameter setting overrides the command-line option `--no-start`.

If you explicitly set the `no-start` to `false` for the module `foo` in the example provided, then the module `foo` **is** started on deployment, even if you also specify the command-line option `--no-start` with the `cf deploy` command.

</td>
<td valign="top">

Depends on the command line option `--no-start`

</td>
<td valign="top">

`no-start: true`

</td>
</tr>
<tr>
<td valign="top">

`restart-on-env-change`

</td>
<td valign="top">

Write

</td>
<td valign="top">

Specifies whether an application should be restarted if an environment variable has been changed in one of the following categories:

-   vcap-application
-   vcap-services
-   user-provided

> ### Note:  
> If you set these parameters to `false`, the changes in environment are not consumable by a running instances of the application. If your application depends on the latest environment, it might become outdated.



</td>
<td valign="top">

> ### Sample Code:  
> ```
> restart-on-env-change:
>   vcap-application: true
>   vcap-services: true
>   user-provided: true
> ```



</td>
<td valign="top">

> ### Sample Code:  
> ```
> restart-on-env-change:
>   vcap-application: false
>   vcap-services: true
>   user-provided: true
> ```



</td>
</tr>
<tr>
<td valign="top">

`routes`

</td>
<td valign="top">

 

</td>
<td valign="top">

A parameter that lists multiple HTTP routes. For more information, see [Routes](routes-53daaaf.md).

</td>
<td valign="top">

`${default-uri}`

</td>
<td valign="top">

> ### Sample Code:  
> ```
> modules:
> - name: my-app
>   type: application
>   parameters:
> 	routes:
>   	- route: "*foo.my.custom.domain/path"
>        - route: foo.my.custom.domain/path
>        - route: foo.${default-domain}/path
>    
> ```



</td>
</tr>
<tr>
<td valign="top">

`route-path`

</td>
<td valign="top">

 

</td>
<td valign="top">

The context “route-path” which is part of the application default URI. Context path routing is routing based not only on domain names \(host header\) but also the path specified in the URL.

</td>
<td valign="top">

n/a

</td>
<td valign="top">

`route-path: /myapp`

</td>
</tr>
<tr>
<td valign="top">

`service-broker-name`

</td>
<td valign="top">

 

</td>
<td valign="top">

The name of the service broker in the Cloud Foundry environment to be created and registered for the specified application module

</td>
<td valign="top">

`${app-name}`

</td>
<td valign="top">

`service-broker-name: jobscheduler`

`service-broker-name: ${app-name}`

</td>
</tr>
<tr>
<td valign="top">

`service-broker-password`

</td>
<td valign="top">

 

</td>
<td valign="top">

The password used for authentication by the XS controller at the service broker when performing service-related requests. The parameter is mandatory if `create-service-broker: true`.

</td>
<td valign="top">

 

</td>
<td valign="top">

`service-broker-password: ${generated-password}` 

</td>
</tr>
<tr>
<td valign="top">

`service-broker-space-scoped`

</td>
<td valign="top">

 

</td>
<td valign="top">

Makes the service plans of the broker visible only within the targeted space.

</td>
<td valign="top">

`false`

</td>
<td valign="top">

`service-broker-space-scoped: true`

</td>
</tr>
<tr>
<td valign="top">

`service-broker-url`

</td>
<td valign="top">

 

</td>
<td valign="top">

Specifies the value of the service broker universal resource locator \(URL\) to register; service requests are sent to this URL. The parameter is mandatory if `create-service-broker: true`.

</td>
<td valign="top">

 

</td>
<td valign="top">

`service-broker-url: ${default-url}`

</td>
</tr>
<tr>
<td valign="top">

`service-broker-user`

</td>
<td valign="top">

 

</td>
<td valign="top">

The name of the user required for authentication by the XS controller at the service broker when performing service-related requests. The parameter is mandatory if `create-service-broker: true`.

</td>
<td valign="top">

 

</td>
<td valign="top">

`service-broker-user: ${generated-user}` 

</td>
</tr>
<tr>
<td valign="top">

`skip-deploy`

</td>
<td valign="top">

 

</td>
<td valign="top">

Use this parameter to skip the deployment of a specified module even if it is present in the descriptor. If you add this parameter for an already deployed module, this module will be deleted in the next operation.

</td>
<td valign="top">

`false`

</td>
<td valign="top">

> ### Sample Code:  
> ```
> modules:
>   - name: foo
>     type: application
>     parameters:
>       skip-deploy: true
> 
> ```



</td>
</tr>
<tr>
<td valign="top">

`stack`

</td>
<td valign="top">

 

</td>
<td valign="top">

Use this parameter to define which prebuilt root file system \(`rootfs`\) you want to use.

</td>
<td valign="top">

n/a

</td>
<td valign="top">

> ### Sample Code:  
> ```
> modules:
>   - name: foo
>     type: application
>     parameters:
>       stack: cflinuxfs3
> 
> ```



</td>
</tr>
<tr>
<td valign="top">

`stage-timeout`

</td>
<td valign="top">

Write

</td>
<td valign="top">

Defines how long, in seconds, your application can take during staging before the MTA operation times out.

See [Application-Specific Timeouts](applications-0540211.md#loio05402110821742479725338cc8d7fe8c__section_qlj_kky_ncc).

</td>
<td valign="top">

1h

</td>
<td valign="top">

```
modules: 
   - name: java 
     …………….. 
     parameters: 
        stage-timeout: 100  
```



</td>
</tr>
<tr>
<td valign="top">

`start-timeout`

</td>
<td valign="top">

Write

</td>
<td valign="top">

Defines how long, in seconds, your application can take to start before the MTA operation times out.

See [Application-Specific Timeouts](applications-0540211.md#loio05402110821742479725338cc8d7fe8c__section_qlj_kky_ncc).

</td>
<td valign="top">

1h

</td>
<td valign="top">

```
modules: 
   - name: java 
     …………….. 
     parameters: 
        start-timeout: 100
```



</td>
</tr>
<tr>
<td valign="top">

`task-execution-timeout`

</td>
<td valign="top">

Write

</td>
<td valign="top">

Defines how long, in seconds, your application can take to execute a task before the MTA operation times out.

See [Application-Specific Timeouts](applications-0540211.md#loio05402110821742479725338cc8d7fe8c__section_qlj_kky_ncc).

</td>
<td valign="top">

12h

</td>
<td valign="top">

```
modules: 
   - name: java 
     …………….. 
     parameters: 
        task-execution-timeout: 100 
```



</td>
</tr>
<tr>
<td valign="top">

`tasks`

</td>
<td valign="top">

 

</td>
<td valign="top">

Specify tasks, which are available for execution in the current droplet of the application. Also provide use of environment variables which are specified with the `env` scope.

</td>
<td valign="top">

n/a

</td>
<td valign="top">

```
tasks: 
 - name: task-1 
command: some-script.sh 
env: 
  env1: value1 
  env2: value2 
```



</td>
</tr>
<tr>
<td valign="top">

`tcp`

</td>
<td valign="top">

 

</td>
<td valign="top">

Specifies whether the application should have `TCP` type routes.

</td>
<td valign="top">

`false`

</td>
<td valign="top">

`tcp:true`

</td>
</tr>
<tr>
<td valign="top">

`tcps`

</td>
<td valign="top">

 

</td>
<td valign="top">

Specifies whether the application should have `TCPS` type routes.

</td>
<td valign="top">

`false`

</td>
<td valign="top">

`tcps:true`

</td>
</tr>
<tr>
<td valign="top">

`upload-timeout`

</td>
<td valign="top">

Write

</td>
<td valign="top">

Defines how long, in seconds, you can upload your application binary before the MTA operation times out.

See [Application-Specific Timeouts](applications-0540211.md#loio05402110821742479725338cc8d7fe8c__section_qlj_kky_ncc) .

</td>
<td valign="top">

1h

</td>
<td valign="top">

```
modules: 
   - name: java 
     .......... 
     parameters: 
        upload-timeout: 100 
```



</td>
</tr>
<tr>
<td valign="top">

`timestamp`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Current timestamp in milliseconds

</td>
<td valign="top">

Generated as described in the description.

</td>
<td valign="top">

 

</td>
</tr>
</table>



<a name="loio177d34d45e3d4fd99f4eeeffc5814cf1__section_xph_1v3_25b"/>

## Module-Specific Properties

The following properties are supported:

**MTA Development and Deployment Module Properties**


<table>
<tr>
<th valign="top">

Property

</th>
<th valign="top">

Description

</th>
<th valign="top">

Default Value

</th>
<th valign="top">

Example

</th>
</tr>
<tr>
<td valign="top">

`MTA_WAIT_AFTER_APP_STOP`

</td>
<td valign="top">

Adds configurable delay in seconds, after stopping the application.

> ### Note:  
> Reserved environment variable for subsequent MTA operations, which is used in blue-green deployment and undeployment.

> ### Tip:  
> Can be used to introduce a faux delay between stopping an application and unbinding its services, in order to avoid errors when unbinding from an application that is still in the process of stopping.



</td>
<td valign="top">

n/a

</td>
<td valign="top">

> ### Sample Code:  
> ```
> modules:
> - name: my-app
>   type: application
>   properties:
>      MTA_WAIT_AFTER_APP_STOP: 30
> 
> ```



</td>
</tr>
</table>



<a name="loio177d34d45e3d4fd99f4eeeffc5814cf1__section_sharedModuleBinaries"/>

## Shared Module Binaries

By default every module has its own binary that is uploaded and deployed in specific manner. It is possible for multiple MTA modules to reference a single deployable binary, for example, an application archive. This means that during deployment, the same application archive is executed separately in multiple applications or application instances, but with different parameters and properties. This results in multiple running applications based on the same source code, which have different configurations and setup. A development project can have one source folder, which is referenced by multiple module entries in the MTA deployment descriptor `mtad.yaml`, as illustrated in the following example:

> ### Sample Code:  
> Multiple MTA Module Entries in the Deployment Descriptor \(`mtad.yaml`\)
> 
> ```
> 
> _schema-version: "3.1.0"
> ID: hello
> version: 0.1.0
> 
> modules:
>    - name: hello-router
>      type: java.tomee
>      path: web/router.war
>      requires:
>      - name: backend
>        properties:
>          backend: ~{url}/content
>          name: backend
>          url: ~{url}
>         
>    - name: hello-backend
>      type: java.tomee
>      path: web/router.war
>      provides:
>        - name: backend
>          properties:
>            url: "${default-url}"
> 
> ```

If deployment is based on an MTA archive, it is not necessary to duplicate the code to have two different deployable modules; the specification for the MTA-module entry in `MANIFEST.MF` is extended, instead. The following \(incomplete\) example of a `MANIFEST.MF` shows how to use a comma-separated list of module names to associate one set of deployment artifacts with all listed modules:

> ### Code Syntax:  
> Multiple MTA Modules Listed in the `MANIFEST.MF` Deployment Manifest
> 
> ```
> Name: web/router.war
> MTA-Module: hello-router,hello-backend
> Content-Type: application/zip
> 
> ```

**Related Information**  


[Managing Service Brokers](https://docs.cloudfoundry.org/services/managing-service-brokers.html)

[Parameters and Properties](parameters-and-properties-490c8f7.md)

[Metadata for Properties and Parameters](metadata-for-properties-and-parameters-fca2ced.md "It is possible to declare metadata for parameters and properties defined in the MTA deployment description, for example, using the “parameters-metadata:” or “properties-metadata:” keys, respectively; the mapping is based on the keys defined for a parameter or property.")

