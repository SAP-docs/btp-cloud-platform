<!-- loio490c8f71e2b74bc0a59302cada66117c -->

# Parameters and Properties

This section contains information about the parameters and properties of a Multitarget Application \(MTA\).

The values of parameters and properties can be specified at design time, in the deployment description \(`mtad.yaml`\). More often, however, property values are determined during deployment, where the values are either explicitly set by the administrator, for example, in an deployment-extension descriptor file \(`myDeployExtension.mtaext`\). When set, the deployer injects the property values into the module's environment. The deployment operation reports an error if it cannot determine a value for a property that is referenced in another or is marked as mandatory.

> ### Tip:  
> -   You can declare metadata for parameters and properties defined in the MTA deployment description; the mapping is based on the parameter or property keys. For example, you can specify if a parameter is **required** \(`optional; false`\) or can be modified `overwritable: true`.
> -   Descriptors can contain so-called placeholders \(also known as substitution variables\), which can be used as sub-strings within property and parameter values. Placeholder names are enclosed by the dollar sign \(`$`\) and curly brackets \(`{}`\). For example: `${host}` and `${domain}`. For each parameter “`P`”, there is a corresponding placeholder `${P}`. The value of *<P\>* can be defined either by a descriptor used for deployment, or by the deploy service itself. Placeholders can also be used without any corresponding parameters; in this scenario, their value cannot be overridden in a descriptor. Such placeholders are read-only.



<a name="loio490c8f71e2b74bc0a59302cada66117c__section_moduleSpecificParameters"/>

## Parameters

Parameters are reserved variables that affect the behavior of the MTA-aware tools, such as the deployer. Module, resource, and dependency parameters have platform-specific semantics. To reference a parameter value, use the placeholder notation `${*<parameter\>*}`, for example, `${default-host}`.

> ### Note:  
> Both parameters and properties may have literal values, that is, strings, integers, and so on. This also applies to deeply nested structured values, such as arrays or maps.

Parameters can be “system”, “write-only”, or “read-write” \(default value can be overwritten\). Each tool publishes a list of system parameters and their \(default\) values for its supported target environments. All parameter values can be referenced as part of other property or parameter value strings. To reference a parameter value, use the placeholder notation `${*<parameter\>*}`. The value of a system parameter cannot be changed in descriptors. Only its value can be referenced using the placeholder notation.

Examples of common read-only parameters are `user`, `default-host`, `default-uri`. The value of a writable parameter can be specified within a descriptor. For example, a module might need to specify a non-default value for a target-specific parameter that configures the amount of memory for the module’s runtime.

> ### Sample Code:  
> Parameters and Placeholders
> 
> ```
> modules:
>   - name: node-hello-world
>     type: javascript.nodejs
>     path: web/
>     parameters:
>       host: ${user}-node-hello-world
> ```

The following parameters are supported:

-   [Module-Specific Parameters](Modules_177d34d.md#loio177d34d45e3d4fd99f4eeeffc5814cf1__section_moduleSpecificParameters)
-   [Resource-Specific Parameters](Resources_9e34487.md#loio9e34487b1a8643fb9a93ae6c4894f015__section_resourceSpecificParameters)
-   [Module Hooks - Specific Parameters](Module_Hooks_b9245ba.md#loiob9245ba90aa14681a416065df8e8c593__section_byz_kcf_wjb)
-   Generic parameters that can have the following scopes:

    -   Global - can be defined on root document level
    -   All - can be consumed everywhere throughout the document
    <a name="loio490c8f71e2b74bc0a59302cada66117c__table_h3d_jp5_pt"/>Global Parameters


    <table>
    <tr>
    <th>

    Parameter


    
    </th>
    <th>

    Scope


    
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

    `authorization-url`


    
    </td>
    <td>

    All


    
    </td>
    <td>

    Yes


    
    </td>
    <td>

    The authorization URL as specified in the cloud controller's `/v2/info` endpoint.


    
    </td>
    <td>

    Generated as described in the description.


    
    </td>
    <td>

    `https://login.cf.sap.hana.ondemand.com`

    `https://localhost:30032/uaa-security`


    
    </td>
    </tr>
    <tr>
    <td>

    `controller-url`


    
    </td>
    <td>

    All


    
    </td>
    <td>

    Yes


    
    </td>
    <td>

    The URL of the cloud controller


    
    </td>
    <td>

    Generated as described in the description.


    
    </td>
    <td>

    `https://api.cf.sap.hana.ondemand.com`

    `https://localhost:30030`


    
    </td>
    </tr>
    <tr>
    <td>

    `default-domain`


    
    </td>
    <td>

    All


    
    </td>
    <td>

    Yes


    
    </td>
    <td>

    The default domain \(configured in the Cloud Foundry environment\)


    
    </td>
    <td>

    Generated as described in the description.


    
    </td>
    <td>

    `accra6024`

    `cfapps.acme.com`


    
    </td>
    </tr>
    <tr>
    <td>

    `deploy-url`


    
    </td>
    <td>

    All


    
    </td>
    <td>

    Yes


    
    </td>
    <td>

    The deploy service URL for the Cloud Foundry environment


    
    </td>
    <td>

    Generated as described in the description.


    
    </td>
    <td>

    ``


    
    </td>
    </tr>
    <tr>
    <td>

    `generated-password`


    
    </td>
    <td>

    All


    
    </td>
    <td>

    Yes


    
    </td>
    <td>

    Randomly generated string value that is composed of 16 characters that may contain upper and lower case letters, digits and special characters \(\_, -, @, $, &, \#, \*\).


    
    </td>
    <td>

    Generated as described in the description.


    
    </td>
    <td>

    `IG@zGg#2g-cvMvsW`


    
    </td>
    </tr>
    <tr>
    <td>

    `generated-user`


    
    </td>
    <td>

    All


    
    </td>
    <td>

    Yes


    
    </td>
    <td>

    A generated user id that is composed of 16 characters that may contain upper and lower case letters, digits and special characters \(\_, -, @, $, &, \#, \*\).


    
    </td>
    <td>

    Generated as described in the description.


    
    </td>
    <td>

    `uYi$d41TzM1-Dm6f`


    
    </td>
    </tr>
    <tr>
    <td>

    `keep-existing-routes`


    
    </td>
    <td>

    Global


    
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
    <td>

    `org`


    
    </td>
    <td>

    All


    
    </td>
    <td>

    Yes


    
    </td>
    <td>

    Name of the target organization


    
    </td>
    <td>

    The current name of the target organization


    
    </td>
    <td>

    `initial, trial`


    
    </td>
    </tr>
    <tr>
    <td>

    `protocol`


    
    </td>
    <td>

    All


    
    </td>
    <td>

    Yes


    
    </td>
    <td>

    The protocol used by the Cloud Foundry environment.


    
    </td>
    <td>

    `http` or `https`


    
    </td>
    <td>

    `http, https`


    
    </td>
    </tr>
    <tr>
    <td>

    `space`


    
    </td>
    <td>

    All


    
    </td>
    <td>

    Yes


    
    </td>
    <td>

    Name of the target organizational space


    
    </td>
    <td>

    Generated as described in the description.


    
    </td>
    <td>

    `initial, a007007`


    
    </td>
    </tr>
    <tr>
    <td>

    `user`


    
    </td>
    <td>

    All


    
    </td>
    <td>

    Yes


    
    </td>
    <td>

    Name of the current user


    
    </td>
    <td>

    Generated as described in the description.


    
    </td>
    <td>

     


    
    </td>
    </tr>
    <tr>
    <td>

    `xs-type`


    
    </td>
    <td>

    All


    
    </td>
    <td>

    Yes


    
    </td>
    <td>

    The XS type, Cloud Foundry or XS advanced


    
    </td>
    <td>

    CF


    
    </td>
    <td>

    `CF, XSA`


    
    </td>
    </tr>
    <tr>
    <td>

    `org-guid`


    
    </td>
    <td>

    All


    
    </td>
    <td>

    Yes


    
    </td>
    <td>

    GUID \(Globally Unique Identifier\) of the target organization


    
    </td>
    <td>

    N/A


    
    </td>
    <td>

    `06564ad5-1b38-458d-8c85-a2e0bcd990a9`


    
    </td>
    </tr>
    <tr>
    <td>

    `space-guid`


    
    </td>
    <td>

    All


    
    </td>
    <td>

    Yes


    
    </td>
    <td>

    GUID \(Globally Unique Identifier\) of the target space


    
    </td>
    <td>

    N/A


    
    </td>
    <td>

    `06564ad5-1b38-458d-8c85-a2e0bcd990a9`


    
    </td>
    </tr>
    </table>
    

These parameters can be used with the `provides` or `requires` dependencies:

<a name="loio490c8f71e2b74bc0a59302cada66117c__table_dependencySpecificParameters"/>Dependency-Specific Parameters


<table>
<tr>
<th>

Parameter



</th>
<th>

Scope



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

`env-var-name`



</td>
<td>

required dependency



</td>
<td>

Write



</td>
<td>

Used when consuming an existing service key. Specifies the name of the environment variable that will contain the service key's credentials. See Consumption of existing service keys for more information.



</td>
<td>

The name of the service key.



</td>
<td>

`env-var-name: SERVICE_KEY_CREDENTIALS`



</td>
</tr>
<tr>
<td>

`visibility`



</td>
<td>

provided dependency



</td>
<td>

Write



</td>
<td>

Specifies the organizations and spaces in which public provided dependencies are visible. See Visibility of cross-MTA configuration for more information.



</td>
<td>

In all spaces of the current organization.

```
visibility:
  - org: ${org}
    space: "*"
```



</td>
<td>

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
</table>

As an alternative, you can also externalize such configurations in a file. See [Service Creation Parameters](Service_Creation_Parameters_a36df26.md).



<a name="loio490c8f71e2b74bc0a59302cada66117c__section_p3w_xdw_vjb"/>

## Properties

The MTA deployment descriptor can contain two types of properties, which are very similar, and are intended for use in the `modules` or `resources` configuration, respectively.

Properties can be declared in the deployment description both in the `modules` configuration \(for example, to define `provides` or `requires` dependencies\), or in the `resources` configuration to specify `requires` dependencies. Both kinds of properties \(`modules` and `requires`\) are injected into the module’s environment. In the `requires` configuration, properties can reference other properties that are declared in the corresponding `provides` configuration, for example, using the `~{}` syntax.





### Cross-References to Properties

To enable resource properties to resolve values from a property in another resource or module, a resource must declare a dependency. However, these “requires” declarations do not affect the order of the application deployment.

> ### Restriction:  
> It is not possible to reference **list** configuration entries either from resources or “subscription” functionalities \(deployment features that are available to subscriber applications\).

> ### Code Syntax:  
> Cross-References between Properties in the MTA Deployment Descriptor
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

