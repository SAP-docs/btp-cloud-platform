<!-- loio177d34d45e3d4fd99f4eeeffc5814cf1 -->

# Modules

The `modules` section of the deployment descriptor lists the deployable parts contained in the MTA deployment archive.

The following elements are mandatory:

-   `name` - must be unique within the MTA it identifies

-   `type` - defines which deployment mechanism to be used for this module

Optional module attributes include: `path`, `description`, `properties`, and `parameters`, `deployed-after`, and in addition `requires` and `provides` lists.

> ### Tip:  
> Modules can be deployed in parallel. See [Parallel Module Deployment](Parallel_Module_Deployment_0384158.md).



<a name="loio177d34d45e3d4fd99f4eeeffc5814cf1__section_mtaModuleTypes"/>

## MTA Module Types

Modify the following MTA module types by providing specific properties or parameters in the MTA deployment descriptor \(`mtad.yaml`\).

<a name="loio177d34d45e3d4fd99f4eeeffc5814cf1__table_mtaModuleTypes"/>MTA Default Modules Types


<table>
<tr>
<th>

Module Type



</th>
<th>

Default Parameter Values and Description



</th>
<th>

Module Properties



</th>
<th>

Result



</th>
</tr>
<tr>
<td>

`javascript.nodejs`



</td>
<td>

No default parameter.

> ### Note:  
> We strongly recommend that you specify the appropriate buildpack for your application. To do so, use the `buildpack` module parameter.



</td>
<td>

None



</td>
<td>

CF application with automatic buildpack detection



</td>
</tr>
<tr>
<td>

`nodejs`



</td>
<td>

`buildpack`\(`nodejs_buildpack`\)



</td>
<td>

None



</td>
<td>

CF application with Node.js runtime



</td>
</tr>
<tr>
<td>

`custom`



</td>
<td>

No default parameter.

> ### Note:  
> We strongly recommend that you specify the appropriate buildpack for your application. To do so, use the `buildpack` module parameter.



</td>
<td>

None



</td>
<td>

CF application with automatic buildpack detection



</td>
</tr>
<tr>
<td>

`application`



</td>
<td>

No default parameter.

> ### Note:  
> We strongly recommend that you specify the appropriate buildpack for your application. To do so, use the `buildpack` module parameter.



</td>
<td>

None



</td>
<td>

CF application with automatic buildpack detection



</td>
</tr>
<tr>
<td>

`java`



</td>
<td>

`buildpack` \(`sap_java_buildpack`\)



</td>
<td>

None



</td>
<td>

CF application with Automatic runtime detection by `sap_java_buildpack`



</td>
</tr>
<tr>
<td>

`java.tomcat`



</td>
<td>

`buildpack` \(`sap_java_buildpack`\)



</td>
<td>

`TARGET_RUNTIME` \(tomcat\)



</td>
<td>

CF application with Tomcat runtime of sap\_java\_buildpack



</td>
</tr>
<tr>
<td>

`java.tomee`



</td>
<td>

`buildpack` \(`sap_java_buildpack`\)



</td>
<td>

`TARGET_RUNTIME` \(tomee\)



</td>
<td>

CF application with TomEE runtime of sap\_java\_buildpack



</td>
</tr>
<tr>
<td>

`com.sap.xs.hdi`



</td>
<td>

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




</td>
<td>

`EXIT (1)`



</td>
<td>

CF application with HDI content activation



</td>
</tr>
<tr>
<td>

`com.sap.xs.hdi-dynamic`



</td>
<td>

`buildpack`\(`nodejs_buildpack`\)



</td>
<td>

None



</td>
<td>

CF application with Node.js runtime



</td>
</tr>
<tr>
<td>

`com.sap.portal.content`



</td>
<td>

> ### Note:  
> Before using this module type, update the content deployer applications to their latest version.

-   `no-route` \(`true`\). Defines if a route should be assigned to the application.
-   `no-start` - \(`true`\). Only the one-off tasks will be executed, that is, without triggering the start of the application.
-   `memory` \(`256M`\). Defines the memory allocated to the application.
-   `tasks` \(`name:deploy, memory:256M, command:npm start)`

    For more information, see [Tasks](Tasks_a1c184c.md).

-   `dependency-type`\(`hard`\). Defines if this module should be deployed first, if it takes part in circular module dependency cycles. If `hard` means that this module is deployed first.



</td>
<td>

None



</td>
<td>

CF application with SAP Fiori launchpad content



</td>
</tr>
<tr>
<td>

`com.sap.portal.site-content`



</td>
<td>

This module type is **deprecated**.

You have to use `com.sap.portal.content` instead.



</td>
<td>

None



</td>
<td>

CF application with SAP Fiori launchpad content



</td>
</tr>
<tr>
<td>

`com.sap.application.content`



</td>
<td>

Required dependency parameters:

-   `content-target(false)`

    Specify that the resource would be used as a target for the module content deployment.




</td>
<td>

None



</td>
<td>

Direct content deployment to backing services



</td>
</tr>
<tr>
<td>

`com.sap.html5.application-content`



</td>
<td>

-   `no-route` \(`true`\). Defines if a route should be assigned to the application.
-   `memory` \(`256M`\). Defines the memory allocated to the application.
-   `execute-app` - \(`true`\). Defines whether the application is executed. If yes, the application performs certain amount of work and upon completion sets a `success-marker` or `failure-marker` by means of a log message.
-   `success-marker` \(`STDOUT:The deployment of html5 application content done.*)`
-   `failure-marker`\(`STDERR:The deployment of html5 application content failed.*`\)
-   `stop-app` \(`true`\). Defines if the application should be stopped after execution.
-   `check-deploy-id` \(`true`\) - Defines if the deployment \(process\) ID should also be checked when checking the application execution status.
-   `dependency-type`\(`hard`\). Defines if this module should be deployed first, if it takes part in circular module dependency cycles. If `hard` means that this module is deployed first.
-   `health-check-type`\(none\). Defines if the module should be monitored for availability.



</td>
<td>

None



</td>
<td>

Deploys a content deployment application, and creates a task that performs the content deployment.



</td>
</tr>
<tr>
<td>

`com.sap.business-logging.content`



</td>
<td>

> ### Note:  
> Before using this module type, update the content deployer applications to their latest version.

-   `no-route` \(`true`\). Defines if a route should be assigned to the application.
-   `no-start` - \(`true`\). Only the one-off tasks will be executed, that is, without triggering the start of the application.
-   `memory` \(`256M`\). Defines the memory allocated to the application.
-   `tasks` \(`name:deploy, memory:256M, command:npm start)`

    For more information, see [Tasks](Tasks_a1c184c.md).

-   `dependency-type`\(`hard`\). Defines if this module should be deployed first, if it takes part in circular module dependency cycles. If `hard` means that this module is deployed first.



</td>
<td>

 



</td>
<td>

Deploys the Business Logging for configuring text resources



</td>
</tr>
<tr>
<td>

`business-logging`



</td>
<td>

This module type is **deprecated**.

You have to use `com.sap.business-logging.content` instead.



</td>
<td>

None



</td>
<td>

Deploys the Business Logging for configuring text resources



</td>
</tr>
<tr>
<td>

`staticfile`



</td>
<td>

`buildpack` \(`staticfile_buildpack`\)



</td>
<td>

None



</td>
<td>

CF application with static file runtime



</td>
</tr>
<tr>
<td>

`ruby`



</td>
<td>

`buildpack`\(`ruby_buildpack`\)



</td>
<td>

None



</td>
<td>

CF application with Ruby runtime



</td>
</tr>
<tr>
<td>

`go`



</td>
<td>

`buildpack`\(`go_buildpack`\)



</td>
<td>

None



</td>
<td>

CF application with Go runtime



</td>
</tr>
<tr>
<td>

`python`



</td>
<td>

`buildpack`\(`python_buildpack`\)



</td>
<td>

None



</td>
<td>

CF application with Python runtime



</td>
</tr>
<tr>
<td>

`php`



</td>
<td>

`buildpack`\(`php_buildpack`\)



</td>
<td>

None



</td>
<td>

CF application with PHP runtime



</td>
</tr>
<tr>
<td>

`binary`



</td>
<td>

`buildpack`\(`binary_buildpack`\)



</td>
<td>

None



</td>
<td>

CF application with Binary runtime



</td>
</tr>
<tr>
<td>

`dotnet_core`



</td>
<td>

`buildpack`\(`dotnet_core_buildpack`\)



</td>
<td>

None



</td>
<td>

CF application with Dotnet runtime



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

Module parameters have platform-specific semantics. To reference a parameter value, use the placeholder notation `${*<parameter\>*}`, for example, `${default-host}`.

> ### Tip:  
> It is also possible to declare metadata for parameters and properties defined in the MTA deployment description; the mapping is based on the parameter or property keys. For example, you can specify if a parameter is **required** \(`optional; false`\) or can be modified `overwritable: true`.

The following parameters are supported:

<a name="loio177d34d45e3d4fd99f4eeeffc5814cf1__table_moduleSpecificParameters"/>MTA Development and Deployment Module Parameters


<table>
<tr>
<th>

Parameter



</th>
<th>

Read-Only \(System\)



</th>
<th>

Description



</th>
<th>

Default Value



</th>
<th>

Example



</th>
</tr>
<tr>
<td>

`app-name`



</td>
<td>

 



</td>
<td>

The name of the application in the Cloud Foundry environment to be deployed for this module, based on the module name



</td>
<td>

`${default-app-name`\}



</td>
<td>

`node-hello-world`

`com.sap.xs2.samples.xsjshelloworld.node-hello-world`



</td>
</tr>
<tr>
<td>

`buildpack`



</td>
<td>

 



</td>
<td>

The name or the URL of a custom buildpack required by the application



</td>
<td>

Empty, or as specified in the deploy service configuration



</td>
<td>

 `buildpack: git://github.acme.com/xs2-java/xs2javabuildpack` 



</td>
</tr>
<tr>
<td>

`buildpacks`



</td>
<td>

 



</td>
<td>

An array of buildpacks. If a buildpack parameter already exists, it will be overwritten by the buildpacks listed in the buildpacks parameter, so that you have to include it in the array.



</td>
<td>

Empty, or as specified in the deploy service configuration



</td>
<td>

 `buildpacks: [java_buildpack, nodejs_buildpack, staticfile_buildpack]` 



</td>
</tr>
<tr>
<td>

`command`



</td>
<td>

 



</td>
<td>

A custom command required to start the application



</td>
<td>

Empty, or as specified in the deploy service configuration



</td>
<td>

 `command: node index.js` 



</td>
</tr>
<tr>
<td>

`create-service-broker`



</td>
<td>

 



</td>
<td>

Specifies whether \[true|false\] a service broker should be registered for the application module



</td>
<td>

`false`



</td>
<td>

`create-service-broker: true`



</td>
</tr>
<tr>
<td>

`default-app-name`



</td>
<td>

Yes



</td>
<td>

The name of the application in the Cloud Foundry environment to be deployed for this module, based on the module name



</td>
<td>

The module name with or without a name-space prefix



</td>
<td>

`node-hello-world`

`com.sap.xs2.samples.xsjshelloworld.node-hello-world`



</td>
</tr>
<tr>
<td>

`default-host`



</td>
<td>

Yes



</td>
<td>

The default host name, which is composed based on the module name to ensure uniqueness. Used with host-based routing to compose the default URI, see below. It follows the convention `${org}-${space}-<module_name>`.

> ### Tip:  
> We recommend you explicitly use the `routes` parameter. See [Routes](Routes_53daaaf.md).

> ### Note:  
> Host names that do not comply with the Cloud Foundry naming limitations are automatically corrected:
> 
> -   Any characters that are not within the allowed `a-z` and `0-9` ranges are replaced by dashes \(-\) to prevent deployment issues.
> -   If the host name length exceeds 63 symbols, the name is shortened and its end is replaced with a hash code.



</td>
<td>

Generated as described in the description



</td>
<td>

`trial-a007007-node-hello-world`



</td>
</tr>
<tr>
<td>

`default-instances`



</td>
<td>

Yes



</td>
<td>

The number of application instances that are started during the deployment



</td>
<td>

1



</td>
<td>

`default-instances: 1`



</td>
</tr>
<tr>
<td>

`default-uri`



</td>
<td>

Yes



</td>
<td>

The default URI, composed as `${host}.${domain}` \(host-based routing\). Note that `${host}` will be the same as `${default-host}`, unless specified explicitly as a parameter. Similarly, `${domain}` would be the same as `${default-domain}`, unless specified explicitly.



</td>
<td>

Generated as described in the description.



</td>
<td>

`trial-a007007-node-hello-world.cfapps.acme.ondemand.com`



</td>
</tr>
<tr>
<td>

`default-url`



</td>
<td>

Yes



</td>
<td>

The default URL, composed as `${protocol}://${default-uri}`. Note that the `${default-uri}` placeholder is resolved as `${host}.${domain}` \(host-based routing\)



</td>
<td>

Generated as described in the description.



</td>
<td>

`${protocol}://${default-uri}`



</td>
</tr>
<tr>
<td>

`dependency-type`



</td>
<td>

 



</td>
<td>

Deployment order of modules with circular dependencies



</td>
<td>

soft



</td>
<td>

`dependency-type: hard`

`dependency-type: soft`



</td>
</tr>
<tr>
<td>

`disk-quota`



</td>
<td>

 



</td>
<td>

The disk space that will be available to the application. This parameter requires a unit of measurement M, MB, G, or GB in upper or lower case.



</td>
<td>

1, or as specified in module-type



</td>
<td>

`disk-quota: 1G`



</td>
</tr>
<tr>
<td>

`docker`



</td>
<td>

Write



</td>
<td>

Creates a module from a docker image. When using a docker image parameter, we do not need to specify the module in the `MANIFEST.mf` file. An image parameter is a docker image from the Docker Hub or somewhere else. The username and the password are optional, but if a Docker image from a private repository is uploaded, then they are mandatory.

When uploading a docker image, the content of a module is not needed.



</td>
<td>

n/a



</td>
<td>

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
<td>

`domain`



</td>
<td>

 



</td>
<td>

The domain on which the application is available later



</td>
<td>

`${default-domain}`



</td>
<td>

`domain: ${default-domain}.acme.com`



</td>
</tr>
<tr>
<td>

`domains`



</td>
<td>

 



</td>
<td>

The domains on which the application is available later. The resulting application routes are the Cartesian product of the domains and hosts. That is, a separate route for each host is constructed on each domain.



</td>
<td>

`domains: - ${default}`



</td>
<td>

`domains: - ${default-domain}.acme.com - test-${default-domain}.acme.com`



</td>
</tr>
<tr>
<td>

`default-domain`



</td>
<td>

Yes



</td>
<td>

The value of this parameter is the default domain for the current organization.



</td>
<td>

 



</td>
<td>

 



</td>
</tr>
<tr>
<td>

`enable-ssh`



</td>
<td>

 



</td>
<td>

Enables use of SSH within an application. Supported for the Diego container runtime environment only.



</td>
<td>

n/a



</td>
<td>

`"enable-ssh": true`

`"enable-ssh": false`



</td>
</tr>
<tr>
<td>

`enable-parallel-service-bindings`



</td>
<td>

 



</td>
<td>

Enables or disables the parallel binding or unbinding of services during deployment. If disabled, the services are bound and unbound sequentially in the order provided in the deployment descriptor.



</td>
<td>

`true`



</td>
<td>

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
<td>

`health-check-http-endpoint`



</td>
<td>

 



</td>
<td>

If the `health-check-type` parameter is set to `http`, the controller will do a `GET` request to this endpoint. The application will be considered as healthy if the response is 200 OK.



</td>
<td>

If health-check-type is set to `http`, the default value is `/`, otherwise there is no default value



</td>
<td>

`health-check-type: http`

`health-check-http-endpoint: /health`



</td>
</tr>
<tr>
<td>

`health-check-timeout`



</td>
<td>

 



</td>
<td>

The application health check timeout in seconds



</td>
<td>

n/a



</td>
<td>

`health-check-timeout:120`



</td>
</tr>
<tr>
<td>

`health-check-invocation-timeout`



</td>
<td>

 



</td>
<td>

The time period in seconds, within which the application health check should be automatically started. If the health check does not start within the defined time period, it is omitted, and the deployment process continues.



</td>
<td>

n/a



</td>
<td>

`health-check-invocation-timeout:16`



</td>
</tr>
<tr>
<td>

`upload-timeout`



</td>
<td>

 



</td>
<td>

The application upload timeout in seconds



</td>
<td>

3600



</td>
<td>

`upload-timeout: 1800`



</td>
</tr>
<tr>
<td>

`health-check-type`



</td>
<td>

 



</td>
<td>

The application health check type



</td>
<td>

`port`



</td>
<td>

`health-check-type: port`

`health-check-type: http`

`health-check-type: process`



</td>
</tr>
<tr>
<td>

`host`



</td>
<td>

 



</td>
<td>

The hostname or subdomain where an application is available later.

If you want to create a wildcard hostname, use an asterisk in quotes \("\*"\).



</td>
<td>

`${default-host}`



</td>
<td>

`host: ${space}-node-hello-world`

`host: "*"`



</td>
</tr>
<tr>
<td>

`hosts`



</td>
<td>

 



</td>
<td>

The hostnames or subdomain where an application is available later.

If you want to create a wildcard hostname, use an asterisk in quotes \("\*"\).



</td>
<td>

`hosts: - ${host}`



</td>
<td>

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
<td>

`idle-domain`



</td>
<td>

 



</td>
<td>

Valid for a blue-green deployment when a new application version is started on a temporary route.

Specify this parameter if you want to use another domain for temporary routes.



</td>
<td>

`${default-domain}`



</td>
<td>

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
<td>

`idle-domains`



</td>
<td>

 



</td>
<td>

Valid for a blue-green deployment when a new application version is started on several temporary routes.

Specify this parameter if you want to use other domains for temporary routes by listing them in an array.



</td>
<td>

`${default-domain}`



</td>
<td>

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
<td>

`idle-host`



</td>
<td>

 



</td>
<td>

Valid for a blue-green deployment when a new application version is started on a temporary route.

Specify this parameter if you want to use another host for a temporary route.

> ### Note:  
> The new application will start on a route comprised of the specified host and the default domain.



</td>
<td>

`${default-host}-idle`



</td>
<td>

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
<td>

`idle-hosts`



</td>
<td>

 



</td>
<td>

Valid for a blue-green deployment when a new application version is started on temporary routes.

Specify this parameter if you want to use other hosts for temporary routes by listing them in an array.

> ### Note:  
> The new application will start on routes comprised of the specified hosts and default domain.



</td>
<td>

`${default-host}-idle`



</td>
<td>

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
<td>

`idle-routes`



</td>
<td>

 



</td>
<td>

Valid for a blue-green deployment when a new application version is started on temporary routes.

Specify this parameter if you want to use other routes for the application.



</td>
<td>

`${default-uri}-idle`



</td>
<td>

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
<td>

`instances`



</td>
<td>

 



</td>
<td>

The number of application instances that will be started during the deployment



</td>
<td>

`${default-instances}`



</td>
<td>

`instances: 2`



</td>
</tr>
<tr>
<td>

`keep-existing`



</td>
<td>

 



</td>
<td>

Defines the application attributes which will be kept after the deployment or blue-green deployment has finished. The supported attributes which could be kept are application environment, application bindings and application routes. If not specified, the default values are false, which indicates that each application attribute will be updated with the new values presented in the deployment descriptor



</td>
<td>

`false`



</td>
<td>

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
<td>

`keep-existing-routes`



</td>
<td>

Write



</td>
<td>

When specified on module level, it indicates if the existing routes of the module's corresponding application should be kept even if they are not defined within the deployment and/or extension descriptors.

When specified on global level, under the `parameters` section of the descriptor, it indicates if the existing routes of all applications within that MTA should be kept.

> ### Note:  
> -   The module-level variant of the parameter has priority over the global parameter.
> -   This parameter is typically used when users want to keep the routes they have mapped manually by using the `cf map-route` command. We discourage this approach, as manual operations could lead to inconsistent deployment results and difficult troubleshooting. We recommend you to define all routes in the deployment and/or extension descriptors, which allows for their automatic management.



</td>
<td>

`false`



</td>
<td>

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
<td>

`memory`



</td>
<td>

 



</td>
<td>

The memory limit for all instances of an application. This parameter requires a unit of measurement M, MB, G, or GB in upper or lower case.



</td>
<td>

256M, or as specified in module-type



</td>
<td>

`memory: 128M`



</td>
</tr>
<tr>
<td>

`no-route`



</td>
<td>

Write



</td>
<td>

Configures the deployer to create or skip the creation of a route for the application described by the module



</td>
<td>

false



</td>
<td>

`no-route: true`



</td>
</tr>
<tr>
<td>

`no-start`



</td>
<td>

 



</td>
<td>

Start/do not start the application during deployment.

> ### Tip:  
> This parameter setting overrides the command-line option *--no-start*.

If you explicitly set the `no-start` to `false` for the module `foo` in the example provided, then the module `foo` **is** started on deployment, even if you also specify the command-line option `--no-start` with the `cf deploy` command.



</td>
<td>

Depends on the command line option `--no-start`



</td>
<td>

`no-stsart: true`



</td>
</tr>
<tr>
<td>

`restart-on-env-change`



</td>
<td>

Write



</td>
<td>

Specifies whether an application should be restarted if an environment variable has been changed in one of the following categories:

-   vcap-application
-   vcap-services
-   user-provided

> ### Note:  
> If you set these parameters to `false`, the changes in environment are not consumable by a running instances of the application. If your application depends on the latest environment, it might become outdated.



</td>
<td>

> ### Sample Code:  
> ```
> restart-on-env-change:
>   vcap-application: true
>   vcap-services: true
>   user-provided: true
> ```



</td>
<td>

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
<td>

`routes`



</td>
<td>

 



</td>
<td>

A parameter that lists multiple HTTP routes. For more information, see [Routes](Routes_53daaaf.md) 



</td>
<td>

`${default-uri}`



</td>
<td>

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
<td>

`route-path`



</td>
<td>

 



</td>
<td>

The context “route-path” which is part of the application default URI. Context path routing is routing based not only on domain names \(host header\) but also the path specified in the URL



</td>
<td>

n/a



</td>
<td>

`route-path: /myapp`



</td>
</tr>
<tr>
<td>

`service-broker-name`



</td>
<td>

 



</td>
<td>

The name of the service broker in the Cloud Foundry environment to be created and registered for the specified application module



</td>
<td>

`${app-name}`



</td>
<td>

`service-broker-name: jobscheduler`

`service-broker-name: ${app-name}`



</td>
</tr>
<tr>
<td>

`service-broker-password`



</td>
<td>

 



</td>
<td>

The password used for authentication by the XS controller at the service broker when performing service-related requests. The parameter is mandatory if `create-service-broker: true`.



</td>
<td>

 



</td>
<td>

 `service-broker-password: ${generated-password}` 



</td>
</tr>
<tr>
<td>

`service-broker-space-scoped`



</td>
<td>

 



</td>
<td>

Makes the service plans of the broker visible only within the targeted space.



</td>
<td>

`false`



</td>
<td>

`service-broker-space-scoped: true`



</td>
</tr>
<tr>
<td>

`service-broker-url`



</td>
<td>

 



</td>
<td>

Specifies the value of the service broker universal resource locator \(URL\) to register; service requests are sent to this URL. The parameter is mandatory if `create-service-broker: true`.



</td>
<td>

 



</td>
<td>

`service-broker-url: ${default-url}`



</td>
</tr>
<tr>
<td>

`service-broker-user`



</td>
<td>

 



</td>
<td>

The name of the user required for authentication by the XS controller at the service broker when performing service-related requests. The parameter is mandatory if `create-service-broker: true`.



</td>
<td>

 



</td>
<td>

 `service-broker-user: ${generated-user}` 



</td>
</tr>
<tr>
<td>

`stack`



</td>
<td>

 



</td>
<td>

Use this parameter to define which prebuilt root file system \(`rootfs`\) you want to use.



</td>
<td>

n/a



</td>
<td>

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
<td>

`tasks`



</td>
<td>

 



</td>
<td>

Specify tasks, which are available for execution in the current droplet of the application. Also provide use of environment variables which are specified with the `env` scope.



</td>
<td>

n/a



</td>
<td>

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
<td>

`tcp`



</td>
<td>

 



</td>
<td>

Specifies whether the application should have `TCP` type routes.



</td>
<td>

`false`



</td>
<td>

`tcp:true`



</td>
</tr>
<tr>
<td>

`tcps`



</td>
<td>

 



</td>
<td>

Specifies whether the application should have `TCPS` type routes.



</td>
<td>

`false`



</td>
<td>

`tcps:true`



</td>
</tr>
<tr>
<td>

`timestamp`



</td>
<td>

Yes



</td>
<td>

Current timestamp in milliseconds



</td>
<td>

Generated as described in the description.



</td>
<td>

 



</td>
</tr>
<tr>
<td>

`zdm-mode`



</td>
<td>

 



</td>
<td>

Parameter value of the `com.sap.xs.hdi` module type that if set to `true`, runs the deployment in a ZDM mode.



</td>
<td>

n/a



</td>
<td>

`zdm-mode: true`



</td>
</tr>
</table>



<a name="loio177d34d45e3d4fd99f4eeeffc5814cf1__section_sharedModuleBinaries"/>

## Shared Module Binaries

By default every module has its own binary that is uploaded and deployed in specific manner. It is possible for multiple MTA modules to reference a single deployable binary, for example, an application archive. This means that during deployment, the same application archive is executed separately in multiple applications or application instances, but with different parameters and properties. This results in multiple running applications based on the same source code, which have different configurations and setup. A development project can have one source folder, which is referenced by multiple module entries in the MTA deployment descriptor `mtad.yaml`, as illustrated in the following example:

> ### Code Syntax:  
> Multiple MTA Module Entries in the Deployment Descriptor \(`mtad.yaml`\)
> 
> > ### Sample Code:  
> > ```
> > 
> > _schema-version: "3.1.0"
> > ID: hello
> > version: 0.1.0
> > 
> > modules:
> > - name: hello-router
> > type: java.tomee
> > path: web/router.war
> > requires:
> > - name: backend
> > properties:
> > backend: ~{url}/content
> > name: backend
> > url: ~{url}
> > 
> > - name: hello-backend
> > type: java.tomee
> > path: web/router.war
> > provides:
> > - name: backend
> > properties:
> > url: "${default-url}"
> > 
> > 
> > ```

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


[https://docs.cloudfoundry.org/services/managing-service-brokers.html](https://docs.cloudfoundry.org/services/managing-service-brokers.html)

[Parameters and Properties](Parameters_and_Properties_490c8f7.md)

[Metadata for Properties and Parameters](Metadata_for_Properties_and_Parameters_fca2ced.md "It is possible to declare metadata for parameters and properties defined in the MTA deployment description, for example, using the “parameters-metadata:” or “properties-metadata:” keys, respectively; the mapping is based on the keys defined for a parameter or property.")

