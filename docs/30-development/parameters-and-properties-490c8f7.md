<!-- loio490c8f71e2b74bc0a59302cada66117c -->

# Parameters and Properties

This section contains information about the parameters and properties of a Multitarget Application \(MTA\).

The values of parameters and properties can be specified at design time, in the MTA development description \(`mta.yaml`\) or in the MTA deployment descriptor \(`mtad.yaml`\). In some cases, it is better to declare certain values depending on the deployment, for example, in an extension descriptor file \(`myDeployExtension.mtaext`\).

The values of parameters and properties might be literals. This way, the result of each deployment will be the same every time. However, by using the placeholders described below, the values might also be set as substitution variables and therefore each deployment might end in a different result depending on the environment or other configurations.

Regardless of the defined value - literal or substitution variable, in most cases the end value for each parameter or property is definitive and well-known before the deployment. This is because the substitution variable values represent a certain template and template resolving is done in the beginning of the MTA deployment.

The module level parameter `${default-host}` follows the template `${org}-${space}-<module_name>`. For example, when it is used in a module `my-module` and the deployment is done within org `my-org`, space `my-space`, the end value of `${default-host}` will be `my-org-my-space-my-module`.

However, in some cases the parameter or property value is dynamic and cannot be predicted before the deployment. In these cases, the substitution variable is dynamic and is done in a later phase of the MTA deployment.

If you want to learn more about dynamically resolved parameters see the [Dynamic parameters](parameters-and-properties-490c8f7.md#loio490c8f71e2b74bc0a59302cada66117c__section_kdm_3qt_txb) section below.

The values of properties and parameters are used during the deployment or at runtime of the MTA.

> ### Note:  
> Both parameters and properties may have literal values, such as strings, integers, etc. This also applies to deeply nested structured values, such as arrays or maps.

> ### Tip:  
> -   You can declare metadata for parameters and properties defined in the MTA deployment description; the mapping is based on the parameter or property keys. For example, you can specify if a parameter is **required** \(`optional; false`\) or can be modified `overwritable: true`.
> -   Descriptors can contain so-called placeholders \(also known as substitution variables\), which can be used as sub-strings within property and parameter values. Placeholder names are enclosed by the dollar sign \(`$`\) and curly brackets \(`{}`\). For example: `${host}` and `${domain}`. For each parameter “`P`”, there is a corresponding placeholder `${P}`. The value of *<P\>* can be defined either by a descriptor used for deployment, or by the deploy service itself. Placeholders can also be used without any corresponding parameters; in this scenario, their value cannot be overridden in a descriptor. Such placeholders are read-only.



<a name="loio490c8f71e2b74bc0a59302cada66117c__section_moduleSpecificParameters"/>

## Parameters

Parameters are reserved variables that affect the behavior of the MTA-aware tools, such as the Cloud MTA Build Tool \(MBT\) or SAP Cloud Deployment service.

Parameters might be used on various levels in the MTA descriptor - top-level, module level, resource level, and dependency level. Based on the parameter applicability it might be used in combination in several places, for example, both on resource and module levels.

Parameters can be “Read-Only” \(also known as “System”\) or “Read-Write” \(default value can be overwritten\). All parameter values can be referenced as part of other property or parameter value strings. The value of a “Read-Only” parameter cannot be changed in descriptors. Only its value can be referenced using the placeholder notation. To reference a parameter value, use the placeholder notation <code>${<i class="varname">&lt;parameter&gt;</i>}</code>, for example `${org}`

SAP Cloud Deployment service supports a list of parameters and their \(default\) values:

-   [Module-Specific Parameters](modules-177d34d.md#loio177d34d45e3d4fd99f4eeeffc5814cf1__section_moduleSpecificParameters)
-   [Resource-Specific Parameters](resources-9e34487.md#loio9e34487b1a8643fb9a93ae6c4894f015__section_resourceSpecificParameters)
-   [Module Hooks - Specific Parameters](module-hooks-b9245ba.md#loiob9245ba90aa14681a416065df8e8c593__section_byz_kcf_wjb)
-   Generic parameters \(table below\) that can have the following scopes:
    -   Top-level - can be defined on top level.
    -   All - can be consumed everywhere throughout the document.


> ### Note:  
> Generic Parameters table contains parameters that might be used on top-level or on all levels. Other supported parameters are distributed in the dedicated pages, for example, module-specific parameters.

The example below shows the parameter \``memory`\` on a module level which defines the amount of memory used by the Cloud Foundry application represented by the module \``node-hello-world`\` during application runtime.

> ### Sample Code:  
> ```
> modules:
>   - name: node-hello-world
>     type: javascript.nodejs
>     path: web/
>     parameters:
>        memory: 128M 
> ```

-   **Generic Parameters**


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

```

apply-namespace:
	app-names: true/false
	service-names: true/false
	app-routes: true/false
	as-suffix: true/false
											
```



</td>
<td valign="top">

Global

</td>
<td valign="top">

Write

</td>
<td valign="top">

Applies namespace to application names \(app-names\), service names \(service-names\), application routes \(app-routes\) as suffix or prefix \(as-suffix\). If the namespace value is not provided in the CLI options, it is not applied.

See [Fine-Grained Configuration](experimental-namespaces-b28fd77.md#loiob28fd77836d44bde8c404618bf0f1228__section_hmf_khn_xcc).

> ### Note:  
> This applies to all applications.



</td>
<td valign="top">

true

</td>
<td valign="top">

```

parameters:
	apply-namespace:
		app-names: true
		service-names: true
		app-routes: false
		as-suffix: true
											
```



</td>
</tr>
<tr>
<td valign="top">

`apps-stage-timeout`

</td>
<td valign="top">

Global

</td>
<td valign="top">

Write

</td>
<td valign="top">

Defines how long, in seconds, your application can take during staging before the MTA operation times out.

See [Application-Specific Timeouts](applications-0540211.md#loio05402110821742479725338cc8d7fe8c__section_qlj_kky_ncc) .

> ### Note:  
> This applies to all applications.



</td>
<td valign="top">

1h

</td>
<td valign="top">

```

parameters: 
    apps-stage-timeout: 100
```



</td>
</tr>
<tr>
<td valign="top">

`apps-start-timeout`

</td>
<td valign="top">

Global

</td>
<td valign="top">

Write

</td>
<td valign="top">

Defines how long, in seconds, your application can take to start before the MTA operation times out.

See [Application-Specific Timeouts](applications-0540211.md#loio05402110821742479725338cc8d7fe8c__section_qlj_kky_ncc) .

> ### Note:  
> This applies to all applications.



</td>
<td valign="top">

1h

</td>
<td valign="top">

```

parameters: 
    apps-start-timeout: 100
```



</td>
</tr>
<tr>
<td valign="top">

`apps-task-execution-timeout`

</td>
<td valign="top">

Global

</td>
<td valign="top">

Write

</td>
<td valign="top">

Defines how long, in seconds, your application can take to execute a task before the MTA operation times out.

See [Application-Specific Timeouts](applications-0540211.md#loio05402110821742479725338cc8d7fe8c__section_qlj_kky_ncc) .

> ### Note:  
> This applies to all applications.



</td>
<td valign="top">

12h

</td>
<td valign="top">

```

parameters: 
    apps-task-execution-timeout: 100
```



</td>
</tr>
<tr>
<td valign="top">

`apps-upload-timeout` 

</td>
<td valign="top">

Global

</td>
<td valign="top">

Write

</td>
<td valign="top">

Defines how long, in seconds, you can upload your application binary before the MTA operation times out.

See [Application-Specific Timeouts](applications-0540211.md#loio05402110821742479725338cc8d7fe8c__section_qlj_kky_ncc) .

> ### Note:  
> This applies to all applications.



</td>
<td valign="top">

1h

</td>
<td valign="top">

```

parameters: 
    apps-upload-timeout: 100 
```



</td>
</tr>
<tr>
<td valign="top">

`authorization-url`

</td>
<td valign="top">

All

</td>
<td valign="top">

Yes

</td>
<td valign="top">

The authorization URL as specified in the cloud controller's `/v2/info` endpoint.

</td>
<td valign="top">

Generated as described in the description.

</td>
<td valign="top">

`https://login.cf.sap.hana.ondemand.com`

</td>
</tr>
<tr>
<td valign="top">

`controller-url`

</td>
<td valign="top">

All

</td>
<td valign="top">

Yes

</td>
<td valign="top">

The URL of the cloud controller

</td>
<td valign="top">

Generated as described in the description.

</td>
<td valign="top">

`https://api.cf.sap.hana.ondemand.com`

</td>
</tr>
<tr>
<td valign="top">

`default-domain`

</td>
<td valign="top">

All

</td>
<td valign="top">

Yes

</td>
<td valign="top">

The default domain \(configured in the Cloud Foundry environment\)

</td>
<td valign="top">

Generated as described in the description.

</td>
<td valign="top">

`accra6024`

`cfapps.acme.com`

</td>
</tr>
<tr>
<td valign="top">

`deploy-url`

</td>
<td valign="top">

All

</td>
<td valign="top">

Yes

</td>
<td valign="top">

The deploy service URL for the Cloud Foundry environment

</td>
<td valign="top">

Generated as described in the description.

</td>
<td valign="top">

``

</td>
</tr>
<tr>
<td valign="top">

`generated-password`

</td>
<td valign="top">

All

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Randomly generated string value that is composed of 16 characters that may contain upper and lower case letters, digits and special characters \(\_, -, @, $, &, \#, \*\).

</td>
<td valign="top">

Generated as described in the description.

</td>
<td valign="top">

`IG@zGg#2g-cvMvsW`

</td>
</tr>
<tr>
<td valign="top">

`generated-user`

</td>
<td valign="top">

All

</td>
<td valign="top">

Yes

</td>
<td valign="top">

A generated user id that is composed of 16 characters that may contain upper and lower case letters, digits and special characters \(\_, -, @, $, &, \#, \*\).

</td>
<td valign="top">

Generated as described in the description.

</td>
<td valign="top">

`uYi$d41TzM1-Dm6f`

</td>
</tr>
<tr>
<td valign="top">

`keep-existing-routes`

</td>
<td valign="top">

Global

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

```

parameters:
keep-existing-routes: true
modules:
  - name: foo
    type: nodejs
    parameters:
       keep-existing-routes: false 
  - name: bar
    type: nodejs
  - name: baz
    type: nodejs
```



</td>
</tr>
<tr>
<td valign="top">

`org`

</td>
<td valign="top">

All

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Name of the target organization

</td>
<td valign="top">

The current name of the target organization

</td>
<td valign="top">

`initial, trial`

</td>
</tr>
<tr>
<td valign="top">

`protocol`

</td>
<td valign="top">

All

</td>
<td valign="top">

Yes

</td>
<td valign="top">

The protocol used by the Cloud Foundry environment.

</td>
<td valign="top">

`http` or `https`

</td>
<td valign="top">

`http, https`

</td>
</tr>
<tr>
<td valign="top">

`space`

</td>
<td valign="top">

All

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Name of the target organizational space

</td>
<td valign="top">

Generated as described in the description.

</td>
<td valign="top">

`initial, a007007`

</td>
</tr>
<tr>
<td valign="top">

`user`

</td>
<td valign="top">

All

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Name of the current user

</td>
<td valign="top">

Generated as described in the description.

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

`xs-type`

</td>
<td valign="top">

All

</td>
<td valign="top">

Yes

</td>
<td valign="top">

The XS type, Cloud Foundry or XS advanced

</td>
<td valign="top">

CF

</td>
<td valign="top">

`CF, XSA`

</td>
</tr>
<tr>
<td valign="top">

`org-guid`

</td>
<td valign="top">

All

</td>
<td valign="top">

Yes

</td>
<td valign="top">

GUID \(Globally Unique Identifier\) of the target organization

</td>
<td valign="top">

N/A

</td>
<td valign="top">

`06564ad5-1b38-458d-8c85-a2e0bcd990a9`

</td>
</tr>
<tr>
<td valign="top">

`space-guid`

</td>
<td valign="top">

All

</td>
<td valign="top">

Yes

</td>
<td valign="top">

GUID \(Globally Unique Identifier\) of the target space

</td>
<td valign="top">

N/A

</td>
<td valign="top">

`06564ad5-1b38-458d-8c85-a2e0bcd990a9`

</td>
</tr>
<tr>
<td valign="top">

`mta-version`

</td>
<td valign="top">

All

</td>
<td valign="top">

Write

</td>
<td valign="top">

The version of the MTA

</td>
<td valign="top">

N/A

</td>
<td valign="top">

`1.0.0`

</td>
</tr>
<tr>
<td valign="top">

`mta-id`

</td>
<td valign="top">

All

</td>
<td valign="top">

Write

</td>
<td valign="top">

The ID of the MTA

</td>
<td valign="top">

N/A

</td>
<td valign="top">

`1.0.0`

</td>
</tr>
</table>


These parameters can be used with the `provides` or `requires` dependencies:

**Dependency-Specific Parameters**


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

`binding-name`

</td>
<td valign="top">

required dependency

</td>
<td valign="top">

Write

</td>
<td valign="top">

Provide a binding name for the association between an application and a service instance

</td>
<td valign="top">

 

</td>
<td valign="top">

```
modules:
 - name: java
 .........
 requires:
  - name:test
    parameters:
     binding-name: java-test
```



</td>
</tr>
<tr>
<td valign="top">

`content-target`

</td>
<td valign="top">

required dependency

</td>
<td valign="top">

Write

</td>
<td valign="top">

This parameter defines the target for the content deployment. It is usually a service instance or a service key toward the content backend that processes the content. The parameter is valid only for modules with direct content deployment:

-   `com.sap.application.content`
-   `com.sap.integration`
-   `com.sap.api.management`

For more information, see [Deploying Content with Generic Application Content Deployment](deploying-content-with-generic-application-content-deployment-d3e2319.md).

</td>
<td valign="top">

false

</td>
<td valign="top">

```
modules: 
 - name: java 
 ......... 
 requires: 
  - name: test 
    parameters: 
     content-target: true
```



</td>
</tr>
<tr>
<td valign="top">

`delete-service-key-after-deployment`

</td>
<td valign="top">

required dependency

</td>
<td valign="top">

Write

</td>
<td valign="top">

If this parameter is set to true, the service keys used during the content deployment are deleted once the deployment is completed. The parameter is valid only for modules with direct content deployment:

-   `com.sap.application.content`
-   `com.sap.integration`
-   `com.sap.api.management`



</td>
<td valign="top">

false

</td>
<td valign="top">

```
modules: 
 - name: java 
 ......... 
 requires: 
  - name: test 
    parameters: 
     delete-service-key-after-deployment: true
```



</td>
</tr>
<tr>
<td valign="top">

`env-var-name`

</td>
<td valign="top">

required dependency

</td>
<td valign="top">

Write

</td>
<td valign="top">

Used when consuming an existing service key. Specifies the name of the environment variable that will contain the service key's credentials. See Consumption of existing service keys for more information.

</td>
<td valign="top">

The name of the service key.

</td>
<td valign="top">

`env-var-name: SERVICE_KEY_CREDENTIALS`

</td>
</tr>
<tr>
<td valign="top">

`visibility`

</td>
<td valign="top">

provided dependency

</td>
<td valign="top">

Write

</td>
<td valign="top">

Specifies the organizations and spaces in which public provided dependencies are visible. See Visibility of cross-MTA configuration for more information.

</td>
<td valign="top">

In all spaces of the current organization.

```
visibility:
  - org: ${org}
    space: "*"
```



</td>
<td valign="top">

```
visibility:
  - org: foo
    space: "*"
  - org: bar
    space: "*"
  - org: baz
    space: qux
```



</td>
</tr>
<tr>
<td valign="top">

`use-live-routes`

</td>
<td valign="top">

provided dependency

</td>
<td valign="top">

Write

</td>
<td valign="top">

Valid for blue-green deployment. Specify this parameter if you want to provide the routes specified in the descriptor.

</td>
<td valign="top">

false

</td>
<td valign="top">

```
provides:
  - name: example-name
    properties:
      provided-route: ${routes/0/route}
    parameters:
      use-live-routes: true
```



</td>
</tr>
</table>

As an alternative, you can also externalize such configurations in a file. See [Service Creation Parameters](service-creation-parameters-a36df26.md).



<a name="loio490c8f71e2b74bc0a59302cada66117c__section_p3w_xdw_vjb"/>

## Properties

MTA properties are Cloud Foundry application environment variables that are used during application runtime. When an MTA property is set, the SAP Cloud Deployment service injects its key as the environment variable key and its value as the variable value in the application, represented by the corresponding MTA module.

MTA properties can be declared in different levels - module level, resource level, and dependency level.





### Cross-References to Properties

To enable resource properties to resolve values from a property in another resource or module, a resource must declare a dependency. However, these “requires” declarations do not affect the order of the application deployment.

> ### Restriction:  
> It is not possible to reference **list** configuration entries either from resources or “subscription” functionalities \(deployment features that are available to subscriber applications\).

> ### Code Syntax:  
> Cross-References between Properties in the MTA Deployment Descriptor in a YAML file
> 
> ```
> 
> modules: 
>   - name: java 
>     ... 
>     provides:  
>       - name: backend  
>         properties:  
>           url: ${default-url}/foo 
> resources:  
>   - name: example  
>     type: example-type   
>     properties:   
>       example-prop: my-example-prop   
>     - name: uaa
>       type: uaa-type 
>       requires: 
>         - name: example 
>         - name: backend 
>             properties: 
>               prop: ~{url} 
>             parameters: 
>               param: ~{url} 
>       properties: 
>         pro1: ~{example/example-prop} 
>       parameters: 
>         config: 
>           app-router-url: ~{backend/url}
>           example-prop: ~{example/example-prop}
> ```

Note the following about the example above:

-   The application name `backend` can depend on the provided content.
-   The `java` module provides the `url` property, which can be referenced by other modules. Its value is generated using the default `url` provided to the application during deployment.
-   The `java` module property `prop` contains a parameter `url`, which results in an environment variable *<prop\>* containing the referenced value.
-   References to other properties can also be used for parameter values, for example in values contained in the `provides` section of a module.



<a name="loio490c8f71e2b74bc0a59302cada66117c__section_nyn_gl2_fpb"/>

## Fully qualified references to properties

The SAP Cloud Deployment service supports the extension of the standard syntax for references in module properties. This extension enables you to specify the name of the `requires` section inside the property reference. You can use this syntax extension to declare implicit groups, as illustrated in the following example:

> ### Sample Code:  
> Syntax Extension: Alternative Grouping of MTA Properties
> 
> ```
> modules:
>   - name: pricing-ui
>     type: javascript.nodejs 
>     properties: 
>       API: # equivalent to group, but defined in the module properties
>        - key: internal1
>          protocol: ~{price_opt/protocol} #reference to value of protocol defined in price_opt of module pricing-backend
>        - key: external 
>          url: ~{competitor_data/url} # reference to string value of property 'url' in required resource 'competitor_data' 
>          api_keys: ~{competitor_data/creds} # reference to list value of property 'creds' in 'competitor_data' 
>     requires: 
>      - name: competitor_data 
>      - name: price_opt 
>   - name: pricing-backend
>     type: java.tomcat 
>     provides: 
>      - name: price_opt 
>        properties: 
>           protocol: http ... 
>   resources: 
>     - name: competitor_data 
>       properties: 
>         url: "https://marketwatch.acme.com/" 
>         creds: 
>           app_key: 25892e17-80f6 
>           secret_key: cd171f7c-560d 
> ```



<a name="loio490c8f71e2b74bc0a59302cada66117c__section_kdm_3qt_txb"/>

## Dynamic parameters

In some cases, it is required to use a value that is unknown before deployment. For example, such entity could be the GUID of another service instance. The GUID of a newly created service instance is not known before the creation of said service but it might be consumed during the MTA deployment.

The feature enables an existing Cloud Foundry entity parameter value to be used inside an MTA descriptor.

> ### Note:  
> Currently, the feature is limited to resolving service GUID for the following resource types:
> 
> -   `org.cloudfoundry.managed-service`
> -   `org.cloudfoundry.user-provided-service`
> -   `org.cloudfoundry.existing-service`

Resolved parameters can only be referenced from other resources or from a cross-MTA dependency. If a dynamic parameter is referenced from other places, like modules, the reference won’t be resolved.

> ### Sample Code:  
> MTA Deployment Descriptor \(`mtad.yaml`\)
> 
> ```
> _schema-version: 3 
> ID: sample-dynamic-service-guid 
> version: 1.0.0 
> 
> modules: 
>   - name: sample-app 
>     type: staticfile 
>     path: content.zip 
>     requires: 
>       - name: test-service 
>       - name: hana-service 
> 
> resources: 
>   - name: test-service 
>     type: org.cloudfoundry.user-provided-service 
>     parameters: 
>       config: 
>         service-guid-of-db: ~{hana-service/my-db-service-guid} 
>     requires: 
>       - name: hana-service 
>     processed-after: [hana-service] 
> 
>   - name: hana-service 
>     type: org.cloudfoundry.managed-service 
>     parameters: 
>       service: hana 
>       service-plan: schema 
>     properties: 
>       my-db-service-guid: ${service-guid}
> ```

> ### Note:  
> In order to use this feature, it is necessary to specify `${service-guid}` inside the `properties` section of the resource. Consumer of service GUID value must add respective resource name in the `requires` section and specify the `processed-after` parameter because the order of resource processing must be explicitly described.



### Dynamic parameter as a cross-MTA dependency

Resolved parameters can also be referenced from a cross-MTA dependency, allowing the service instance to be referenced from another MTA.

The following example shows the dependency declaration referencing a dynamic parameter in the deployment descriptor of the “provider” MTA:

> ### Sample Code:  
> ```
> _schema-version: 3
> ID: dynamic-service-guid-consumer
> version: 1.0.0
> 
> modules:
>   - name: app-consumer
>     type: staticfile
>     path: content.zip
>     requires:
>       - name: db-config
>         properties:
>           reference_instance: ~{db-instanceid}
> 
> resources:
>   - name: db-config
>     type: configuration
>     parameters:
>       provider-id: "dynamic-service-guid-provider:db-guid"
>       version: ">=1.0.0"
>       target:
>         org: ${org}
>         space: ${space}
> ```

The following example shows the dependency declaration in the deployment descriptor of the “consumer” MTA:

> ### Sample Code:  
> ```
> _schema-version: 3
> ID: dynamic-service-guid-consumer
> version: 1.0.0
> 
> modules:
>   - name: app-consumer
>     type: staticfile
>     path: content.zip
>     requires:
>       - name: db-config
>         properties:
>           reference_instance: ~{db-instanceid}
> 
> resources:
>   - name: db-config
>     type: configuration
>     parameters:
>       provider-id: "dynamic-service-guid-provider:db-guid"
>       version: ">=1.0.0"
>       target:
>         org: ${org}
>         space: ${space}
> ```

For more information about cross-MTA configurations see [Cross-MTA Dependencies](cross-mta-dependencies-b8e1953.md).

