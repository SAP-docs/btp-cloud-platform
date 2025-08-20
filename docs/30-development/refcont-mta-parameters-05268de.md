<!-- loio05268de28b514552b03c497fcc25b5dd -->

# REFCONT: MTA Parameters

> ### Note:  
> If you can't find a specific parameter from the native Cloud Foundry manifest here, refer to [Prerequisites and Restrictions](multitarget-applications-in-the-cloud-foundry-environment-d04fc0e.md#loiod04fc0e2ad894545aebfd7126384307c__section_ph2_r5h_1cb) to see which Cloud Foundry features are currently not supported.

**MTA Development and Deployment Module Parameters**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Scope

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

`app-features`

</td>
<td valign="top">

Module

</td>
<td valign="top">

Write

</td>
<td valign="top">

Allows enabling, disabling, and querying specific features for individual applications. These features typically control behaviors or capabilities related to application execution.

All parameters in the map are passed directly to the CF API. This mechanism ensures that all future app features will be automatically supported through MTA deployment.

For more information about the supported features, see [Supported app features](https://v3-apidocs.cloudfoundry.org/index.html#supported-app-features).

> ### Note:  
> If you want to configure SSH enablement, use this parameter instead of the deprecated `enable-ssh` parameter.



</td>
<td valign="top">

n/a

</td>
<td valign="top">

```
modules:
- name: foo
  type: application
  parameters:
    app-features:
      file-based-vcap-services: true
      ssh: true

```



</td>
</tr>
<tr>
<td valign="top">

`app-name`

</td>
<td valign="top">

Module

</td>
<td valign="top">

Write

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

Module

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

Module

</td>
<td valign="top">

Write

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

Module

</td>
<td valign="top">

Write

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

Module

</td>
<td valign="top">

Write

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

Module

</td>
<td valign="top">

Write

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

Module

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

Module

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

Module

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

Module

</td>
<td valign="top">

Yes

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

Module

</td>
<td valign="top">

Yes

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

Module

</td>
<td valign="top">

Yes

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

Module

</td>
<td valign="top">

Yes

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

Module

</td>
<td valign="top">

Yes

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

Module

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

Module

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

Module

</td>
<td valign="top">

Write

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

Module

</td>
<td valign="top">

Write

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

Module

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

Module

</td>
<td valign="top">

Write

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

Module

</td>
<td valign="top">

Write

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

Module

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

Module

</td>
<td valign="top">

Write

</td>
<td valign="top">

Enables use of SSH within an application. Supported for the Diego container runtime environment only.

> ### Note:  
> This parameter is deprecated. To enable SSH within an application, use the `app-features` parameter instead.



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

Module

</td>
<td valign="top">

Write

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

Module

</td>
<td valign="top">

Write

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

Module

</td>
<td valign="top">

Write

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

Module

</td>
<td valign="top">

Write

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

Module

</td>
<td valign="top">

Write

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

Module

</td>
<td valign="top">

Write

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

Module

</td>
<td valign="top">

Write

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

Module

</td>
<td valign="top">

Write

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

Module

</td>
<td valign="top">

Write

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

Module

</td>
<td valign="top">

Write

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

Module

</td>
<td valign="top">

Write

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

Module

</td>
<td valign="top">

Write

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

Module

</td>
<td valign="top">

Write

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

Module

</td>
<td valign="top">

Write

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

Module

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

Module

</td>
<td valign="top">

Write

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

Module

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

Module

</td>
<td valign="top">

Write

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

Module

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

Module

</td>
<td valign="top">

Write

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

Module

</td>
<td valign="top">

Write

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

Module

</td>
<td valign="top">

Write

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

Module

</td>
<td valign="top">

Write

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

Module

</td>
<td valign="top">

Write

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

Module

</td>
<td valign="top">

Write

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

Module

</td>
<td valign="top">

Write

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

Module

</td>
<td valign="top">

Write

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

Module

</td>
<td valign="top">

Write

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

Module

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

Module

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

Module

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

Module

</td>
<td valign="top">

Write

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

`upload-timeout`

</td>
<td valign="top">

Module

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

Module

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

**MTA Development and Deployment Parameters**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Scope

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

`apply-namespace`

</td>
<td valign="top">

Resource

</td>
<td valign="top">

Write

</td>
<td valign="top">

Applies namespace to the service name. If the namespace value is not provided in the CLI options, it is not applied. For more information, see [Fine-Grained Configuration](experimental-namespaces-b28fd77.md#loiob28fd77836d44bde8c404618bf0f1228__section_hmf_khn_xcc).

</td>
<td valign="top">

 

</td>
<td valign="top">

```
resources:
- name: java
     ...
  parameters:
	apply-namespace: true 
   
```



</td>
</tr>
<tr>
<td valign="top">

`config`

</td>
<td valign="top">

Resource

</td>
<td valign="top">

Write

</td>
<td valign="top">

Defines service creation parameters. More information in [Service Instance Parameters](service-instance-parameters-a36df26.md).

</td>
<td valign="top">

n/a

</td>
<td valign="top">

See [Service Instance Parameters](service-instance-parameters-a36df26.md).

</td>
</tr>
<tr>
<td valign="top">

`default-container-name`

</td>
<td valign="top">

Resource

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Default value for the `container-name` parameter that is used during HDI creation. It is based on the organization, space and resource name, which are combined in a way that conforms to the container-name restrictions for length and legal characters. All dash \(-\) symbols are replaced with an underscore \(\_\).

> ### Note:  
> It is highly recommended to avoid using this parameter with HANA services because in some cases the generated name cannot comply with the HANA naming limitations' requirements. Forward compatability is not guaranteed.



</td>
<td valign="top">

Generated as described in the description.

</td>
<td valign="top">

`<org_name>_<space_name>_<resource_name>` 

</td>
</tr>
<tr>
<td valign="top">

`default-service-name`

</td>
<td valign="top">

Resource

</td>
<td valign="top">

Yes

</td>
<td valign="top">

The name of the service in the Cloud Foundry environment to be created for this resource, based on the resource name with or without a name-space prefix.

</td>
<td valign="top">

The resource name with or without a name-space prefix

</td>
<td valign="top">

`nodejs-hdi-container`

`com.sap.xs2.samples.xsjshelloworld.nodejs-hdi-container`

</td>
</tr>
<tr>
<td valign="top">

`default-xsappname`

</td>
<td valign="top">

Resource

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Default value for the `xsappname` parameter that is used during UAA creation. It is based on the service name, which is modified in a way that conforms to the `xsappname` restrictions for length and legal characters.

</td>
<td valign="top">

Generated as described in the description.

</td>
<td valign="top">

`xs_-deploy-service-database` \(if the service name is “`xs@-deploy-service-database`”\)

</td>
</tr>
<tr>
<td valign="top">

`fail-on-service-update`

</td>
<td valign="top">

Resource

</td>
<td valign="top">

Write

</td>
<td valign="top">

When this parameter is set to true, the deployment will fail on every service update failure. By default, service updates are fail-safe for asynchronous calls \(Cloud Foundry API calls that result in a call to the service broker\).

When the parameter is set to false, deployments will not fail on service update failures, as the updates will be made fail-safe even for calls that do not result in a call to the respective service broker.

For more information, see:

-   [Updating Service Plans](services-6ef40df.md#loio6ef40dfc2ef14bb08c28cd53b4de4c0b__section_sgc_322_mfc)
-   [Updating Service Instance Parameters](service-instance-parameters-a36df26.md#loioa36df26b36484129b482ae20c3eb8004__section_ap5_lrd_mfc)
-   [Updating Service Tags](service-tags-3e36d13.md#loio3e36d133d9f342d4a3a6fde235783ccc__section_tht_232_mfc)



</td>
<td valign="top">

n/a \(fails only on asynchronous calls\)

</td>
<td valign="top">

```
fail-on-service-update:
  parameters: true
  plan: true
  tags: true

```



</td>
</tr>
<tr>
<td valign="top">

`service`

</td>
<td valign="top">

Resource

</td>
<td valign="top">

Write

</td>
<td valign="top">

The type of the created service

</td>
<td valign="top">

Empty, or as specified in resource-type

</td>
<td valign="top">

`service: hana`

</td>
</tr>
<tr>
<td valign="top">

`service-key-name`

</td>
<td valign="top">

Resource

</td>
<td valign="top">

Write

</td>
<td valign="top">

Used when consuming an existing service key. Specifies the name of the service key. See [Consumption of Service Keys](service-keys-32297f1.md#loio32297f15898f47329df76b706447fc3e__consumption-of-service-keys) for more information.

</td>
<td valign="top">

The name of the resource.

</td>
<td valign="top">

`service-key-name: my-service-key`

</td>
</tr>
<tr>
<td valign="top">

`service-name`

</td>
<td valign="top">

Resource

</td>
<td valign="top">

Write

</td>
<td valign="top">

The name of the service in the Cloud Foundry environment to be created for this resource, based on the resource name with or without a name-space prefix.

> ### Note:  
> Service names that do not comply with the Cloud Foundry limitation of 50 symbols are automatically corrected. In such cases, the name is shortened and its end is replaced with a hash code.



</td>
<td valign="top">

`${default-service-name}`

</td>
<td valign="top">

`nodejs-hdi-container`

`com.sap.xs2.samples.xsjshelloworld.nodejs-hdi-container`

</td>
</tr>
<tr>
<td valign="top">

`service-plan`

</td>
<td valign="top">

Resource

</td>
<td valign="top">

Write

</td>
<td valign="top">

The plan of the created service

</td>
<td valign="top">

Empty, or as specified in resource-type

</td>
<td valign="top">

`service-plan: hdi-shared`

</td>
</tr>
<tr>
<td valign="top">

`service-tags`

</td>
<td valign="top">

Resource

</td>
<td valign="top">

Write

</td>
<td valign="top">

Some services employ a list of custom tags, which provide an easier way for applications to parse `<VCAP_SERVICES>` for credentials. You can provide custom tags when creating a service instance. For more information, see [Service Tags](service-tags-3e36d13.md).

</td>
<td valign="top">

n/a

</td>
<td valign="top">

```
resources: 
  - name: nodejs-uaa 
    type: com.sap.xs.uaa 
    parameters: 
      service-tags: ["custom-tag-A", "custom-tag-B"] 
```



</td>
</tr>
<tr>
<td valign="top">

`service-broker`

</td>
<td valign="top">

Resource

</td>
<td valign="top">

Write

</td>
<td valign="top">

Use this parameter to specify the service broker you want to employ when you create your service. This can be useful for testing purposes, among others.

</td>
<td valign="top">

Name of service broker you want to be used.

</td>
<td valign="top">

```
resources: 
  - name: test-service
    type: org.cloudfoundry.managed-service
    parameters: 
      service: foo
      service-plan: bar-a
      service-broker: test-broker-1
```



</td>
</tr>
<tr>
<td valign="top">

`skip-service-updates`

</td>
<td valign="top">

Resource

</td>
<td valign="top">

Write

</td>
<td valign="top">

This parameter allows you to specify the service configuration changes to `ignore`, when deciding if you want to update a service instance – in particular changes of service `parameters`, `plan`, or `tags`.

</td>
<td valign="top">

The default value for all is `false`. The service instance would be updated on change in any of the configurations.

</td>
<td valign="top">

```

resources:
  - name: service-name
    type: org.cloudfoundry.managed-service
    parameters:
      skip-service-updates:
          plan: true
          parameters: true
          tags: true

```

In the example above, `skip-service-updates` modifies the update strategy as follows:

-   allows users to specify which configurations should not be updated

Note that these 3 key-value pairs can be in any order.

</td>
</tr>
<tr>
<td valign="top">

`syslog-drain-url`

</td>
<td valign="top">

Resource

</td>
<td valign="top">

Write

</td>
<td valign="top">

The URL to which logs for bound applications are streamed.

> ### Note:  
> This feature only works for user-provided services.



</td>
<td valign="top">

n/a

</td>
<td valign="top">

```
resources: 
  - name: service-name 
    type: org.cloudfoundry.user-provided-service 
    parameters: 
      syslog-drain-url: syslog://example.log-aggregator.com

```



</td>
</tr>
</table>

