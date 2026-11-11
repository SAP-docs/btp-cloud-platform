<!-- loio490c8f71e2b74bc0a59302cada66117c -->

# Parameters and Properties

Parameters and properties are the two kinds of configurable values in an MTA descriptor. Learn how to configure, reference, escape, and resolve them dynamically.



<a name="loio490c8f71e2b74bc0a59302cada66117c__section_overview"/>

## Overview

A multitarget application \(MTA\) is configured through two kinds of values:

-   **Parameters** are reserved variables that control the behavior of the MTA tooling \(Cloud MTA Build Tool, SAP Cloud Deployment service\) — for example, how much memory an application gets or how long staging may take.
-   **Properties** are values injected into your application at runtime as Cloud Foundry environment variables.


<table>
<tr>
<th valign="top">

 

</th>
<th valign="top">

Parameters

</th>
<th valign="top">

Properties

</th>
</tr>
<tr>
<td valign="top">

**Purpose**

</td>
<td valign="top">

Control build and deploy behavior

</td>
<td valign="top">

Provide runtime configuration to the application

</td>
</tr>
<tr>
<td valign="top">

**Consumed By**

</td>
<td valign="top">

MTA tooling and SAP Cloud Deployment service

</td>
<td valign="top">

Your running application \(as environment variables\)

</td>
</tr>
<tr>
<td valign="top">

**Placeholder Syntax**

</td>
<td valign="top">

`${name}`

</td>
<td valign="top">

`~{name}`

</td>
</tr>
<tr>
<td valign="top">

**Declared At**

</td>
<td valign="top">

Top, module, resource, and dependency level

</td>
<td valign="top">

Module, resource, and dependency level

</td>
</tr>
</table>

You declare both at design time in the MTA development descriptor \(`mta.yaml`\) or MTA deployment descriptor \(`mtad.yaml`\). When a value should depend on the target environment, you override it at deploy time in an extension descriptor \(`myDeployExtension.mtaext`\).

Values may be literals \(strings, integers, arrays, or maps\) or placeholders that are resolved during deployment. See [Placeholders \(Substitution Variables\)](parameters-and-properties-490c8f7.md#loio490c8f71e2b74bc0a59302cada66117c__section_placeholders).

> ### Tip:  
> You can declare metadata for parameters and properties defined in the MTA deployment descriptor. For example, you can specify if a parameter is required \(`optional: false`\) or can be modified \(`overwritable: true`\). For more information, see [Metadata for Properties and Parameters](metadata-for-properties-and-parameters-fca2ced.md).



<a name="loio490c8f71e2b74bc0a59302cada66117c__section_moduleSpecificParameters"/>

## Parameters

Parameters are values that affect the behavior of MTA-aware tools, such as the Cloud MTA Build Tool \(MBT\) or SAP Cloud Deployment service. The SAP Cloud Deployment service defines a set of supported parameters with predefined behavior.

> ### Example:  
> The `memory` parameter at the module level defines the amount of memory used by the Cloud Foundry application represented by the module `node-hello-world` during application runtime.
> 
> > ### Sample Code:  
> > ```
> > modules:
> >   - name: node-hello-world
> >     type: javascript.nodejs
> >     path: web/
> >     parameters:
> >       memory: 128M
> > ```

Parameters can be set at several levels: top level, module and module hook level, resource level, and dependency \(`provides` / `requires`\) level. The same parameter may be used at more than one level — for example, it can be set both at the resource and module levels — and depending on the level, it may be interpreted and applied differently. Top-level parameters have global scope and are accessible anywhere in the descriptor. Parameters set at lower levels — module, resource, or dependency level — are local to that scope and visible only within the same block.

Parameters can be **Read-Only** \(also known as "System"\) or **Write** \(if they have a default value, it can be overwritten\). All parameter values can be referenced using the placeholder notation `${<parameter>}`, for example `${org}`. The value of a **Read-Only** parameter cannot be changed in descriptors — it can only be referenced.

SAP Cloud Deployment service supports the following types of parameters:

-   [Module-Specific Parameters](modules-177d34d.md#loio177d34d45e3d4fd99f4eeeffc5814cf1__section_moduleSpecificParameters)
-   [Resource-Specific Parameters](resources-9e34487.md#loio9e34487b1a8643fb9a93ae6c4894f015__section_resourceSpecificParameters)
-   [Module Hooks - Specific Parameters](module-hooks-b9245ba.md#loiob9245ba90aa14681a416065df8e8c593__section_byz_kcf_wjb)
-   Top-Level Parameters \(see the table in [Reference: Parameter Tables](parameters-and-properties-490c8f7.md#loio490c8f71e2b74bc0a59302cada66117c__section_parameterTables)\) — Top-level parameters are generally applicable parameters that cover various scenarios and can be used in different parts of the MTA descriptors. They can be grouped into to categories - "Read-Only" and "Write":
    -   Top-level "Write" parameters are designed to impact the behavior of the whole MTA deployment or many parts of it. It is wise to use them in order to avoid duplication. Their values can be defined and controlled by the customer. These parameters can be referenced throughout the whole document.
    -   Top-level "Read-Only" parameters are commonly used parameters that can only be referenced in different parts of the MTA descriptors.

-   Dependency-Specific Parameters \(see the table in [Reference: Parameter Tables](parameters-and-properties-490c8f7.md#loio490c8f71e2b74bc0a59302cada66117c__section_parameterTables)\) — These parameters can be used with the `provides` or `requires` dependencies


All supported parameters are consolidated in [List of Supported MTA Parameters](list-of-supported-mta-parameters-6aa426e.md) for your convenience.

> ### Note:  
> The supported parameters follow the kebab-case naming notation \(lowercase words separated by hyphens, for example `service-plan` or `health-check-type`\), not camelCase \(for example `servicePlan`\).
> 
> This notation applies only to the supported parameters defined by the SAP Cloud Deployment service. Customer-defined parameters that you declare and reference elsewhere in the descriptor are not bound by this convention and may use any notation you choose.

You can declare custom parameters at any level in the descriptor and reference them with `${...}`:

> ### Example:  
> The custom parameter `environment` is declared once at the top level. It is referenced in the resource configuration.
> 
> > ### Sample Code:  
> > ```
> > _schema-version: 3.3.0
> > ID: my-app
> > version: 1.0.0
> > 
> > parameters:
> >   environment: dev   # custom parameter
> > 
> > resources:
> >   - name: external-config
> >     type: configuration
> >     parameters:
> >       provider-id: my-provider:configuration_${environment}   # referencing the custom parameter
> > ```



<a name="loio490c8f71e2b74bc0a59302cada66117c__section_p3w_xdw_vjb"/>

## Properties

MTA properties are Cloud Foundry application environment variables used during application runtime. When an MTA property is set, the SAP Cloud Deployment service injects its key as the environment variable name and its value as the variable value into the application represented by the corresponding MTA module. Properties are not taken into account when an MTA module represents SAP content rather than a Cloud Foundry application \(see [Content Deployment](content-deployment-68d0da8.md)\).

You can declare MTA properties at module level, resource level, and dependency level.

> ### Sample Code:  
> ```
> modules:
>   - name: my-app-module
>     type: application 
>     path: "appBits.zip"
>     properties: 
>       default-host: ${default-host}
> ```

To make a property consume a value produced by another module or resource, see [Referencing Values Across the Descriptor](parameters-and-properties-490c8f7.md#loio490c8f71e2b74bc0a59302cada66117c__section_referencing).



<a name="loio490c8f71e2b74bc0a59302cada66117c__section_placeholders"/>

## Placeholders \(Substitution Variables\)

Instead of hard-coding a value or duplicating it, you can reference another value with a **placeholder**. Placeholder names are enclosed in a sigil and curly braces:

-   `${parameter}` references a **parameter** value – for example, `${org}` resolves to the current Cloud Foundry org name.
-   `~{property}` references a **property** value provided by another module or resource.

Each supported parameter `P` has a corresponding placeholder `${P}`. "Write" parameters can have their value set in a descriptor, while "Read-Only" parameters can only be referenced, as their value is always set by the SAP Cloud Deployment service.



### When Placeholders Are Resolved

In most cases, the final value is known during the initial phase of deployment **before** any changes are applied. Placeholder resolution acts as a template pass that the SAP Cloud Deployment service runs at the start of the operation.

For example, the module-level parameter `${default-host}` follows the template `${org}-${space}-<module_name>`. When it is used in module `my-module` and deployed to org `my-org`, space `my-space`, it resolves to `my-org-my-space-my-module`.

Some values, however, cannot be known until the deployment is in progress — for example, the GUID of a newly created service instance. These are resolved in a later phase. See [Dynamic Parameters](parameters-and-properties-490c8f7.md#loio490c8f71e2b74bc0a59302cada66117c__section_kdm_3qt_txb).



### Escaping Placeholders and References

In some cases, you may want a value that looks like a placeholder \(`${...}`\) or a cross-reference \(`~{...}`\) to be passed through unchanged, instead of being resolved during deployment. This is required when the value is resolved later by a different component \(for example, by the application's own configuration engine at runtime, or by a service broker when it provisions the instance\), which must therefore receive the `${...}` syntax intact.

To prevent a placeholder or reference from being resolved, escape it with a single backslash \(`\`\) directly before the opening `${` or `~{`. The escaped expression is skipped during template resolution, and the leading backslash is removed once all other placeholders and references have been resolved. As a result, the deployed value contains the literal `${...}` or `~{...}`.

> ### Note:  
> Escaping applies to both placeholder syntax \(`${...}`\) and property reference syntax \(`~{...}`\). Each occurrence must be escaped individually, including repeated occurrences within the same value.

> ### Note:  
> Escaping a reference in a **quoted** string requires **two** backslashes, whereas escaping a reference in a **non-quoted** string requires only **one**. This is a consequence of YAML's own escaping rules and is not an MTA-specific detail.

> ### Sample Code:  
> Escaping Placeholders in the MTA Deployment Descriptor \(mtad.yaml\)
> 
> ```
> modules:
>   - name: my-app
>     type: application
>     parameters:
>       # Resolved by the Cloud Deployment service to the actual application host:
>       app-host: ${default-host}
>     properties:
>       # Escaped in a quoted string - two backslashes. Passed through
>       # unchanged; the application's own configuration engine resolves
>       # ${server.port} at runtime:
>       LISTEN_CONFIG: "port=\\${server.port}"
>     requires:
>       - name: identity-service
> 
> resources:
>   - name: identity-service
>     type: org.cloudfoundry.managed-service
>     parameters:
>       service: identity
>       service-plan: application
>       config:
>         display-name: my-app-${space}
>         default-attributes:
>           # Escaped in non-quoted strings - one backslash. Forwarded to the
>           # service instance verbatim; the Identity Authentication service substitutes
>           # the values per user at runtime, not the Cloud Deployment service:
>           user_name: \${corporateIdP.user_uuid}
>           email: \${corporateIdP.mail}
> ```

In this example:

-   In module `my-app`, the parameter `app-host` is resolved by the SAP Cloud Deployment service to the real application host, while the property `LISTEN_CONFIG` reaches the application as the literal string `port=${server.port}`, which the application's own configuration engine resolves at runtime. Because the value is a **double-quoted** string, the reference is escaped with **two** backslashes.
-   In the `identity-service` resource, `${space}` in `display-name` is resolved by the SAP Cloud Deployment service, while the escaped `user_name` and `email` values are forwarded to the Identity Authentication service instance as the literal strings `${corporateIdP.user_uuid}` and `${corporateIdP.mail}`. Because these are **non-quoted** values, each reference is escaped with a **single** backslash.

> ### Note:  
> A backslash that does not precede `${` or `~{` is treated as an ordinary character and is left unchanged.



<a name="loio490c8f71e2b74bc0a59302cada66117c__section_referencing"/>

## Referencing Values Across the Descriptor

One module or resource often needs a value produced by another. This is done with a `requires` declaration that points at a `provides` block, which belongs to a module, or at another resource's properties.



### Sharing a Value Between Two Modules

The most common cross-reference is one module consuming a value that another module exposes. The producing module declares a `provides` block, while the consuming module declares a matching `requires` entry and reads individual properties with the `~{<provides-name>/<property>}` syntax.

> ### Sample Code:  
> Sharing a value between two modules in the MTA deployment descriptor \(mtad.yaml\)
> 
> ```
> modules:
>   - name: providing-module
>     type: application
>     path: appBits.zip
>     provides:
>       - name: module-1-provided        # the shared bundle of values
>         properties:
>           user: ${generated-user}      # may reference module or global parameters
>           config: "static-string"      # or be a literal
>           url: ${default-url}
> 
>   - name: consuming-module
>     type: application
>     path: appBits.zip
>     requires:
>       - name: module-1-provided        # gain access to the provided values
>     properties:                        # injected as application environment variables
>       m1-user: ~{module-1-provided/user}
>       m1-config: '~{module-1-provided/config}-with-suffix'   # usable inside a string
>       m1-url: ~{module-1-provided/url}
> ```

Note the following about the example above:

-   `~{<provides-name>/<property>}` names the `provides` block first, then the property inside it — **not** the module name.
-   A reference can be embedded inside a larger string value \(see `m1-config`\).
-   A module-to-module `requires` dependency **does** influence deployment order: the providing module is deployed before the consuming module.

> ### Note:  
> The choice between `${default-url}` and `${default-live-url}` in a `provides` block depends on who consumes the provided value:
> 
> -   **Module consumer**: `${default-url}` is the right choice when you want modules to communicate with each other during the testing phase of a blue-green deployment. At the end of deployment, both the providing and consuming module resolve to the correct live URLs.
> -   **Resource consumer**: Use `${default-live-url}`. Resource parameters are resolved during the initial phase of a blue-green deployment, before idle applications are started. Using `${default-url}` here causes the resource to target the idle URL \(with the `-idle` suffix\) and misdirect traffic.



### Consuming a Provided Dependency from a Resource

A resource can also consume a value from a module's `provides` block, or from another resource's properties, by declaring a `requires` dependency. These `requires` declarations do **not** affect the order of application deployment.

> ### Restriction:  
> It is not possible to reference **list** configuration entries either from resources or from "subscription" functionalities \(deployment features available to subscriber applications\).

> ### Sample Code:  
> Cross-references between properties in the MTA deployment descriptor \(mtad.yaml\)
> 
> ```
> modules:
>   - name: java
>     type: java.tomcat
>     path: java.war
>     provides:
>       - name: backend
>         properties:
>           url: ${default-live-url}/foo
> 
>   - name: app-router
>     type: javascript.nodejs
>     path: router/
>     requires:
>       # Consuming from a resource's provided value: makes UAA_SHARED an
>       # environment variable of the app-router application.
>       - name: uaa
>         properties:
>           UAA_SHARED: ~{uaa/pro1}
>       # Consuming from a module's provided dependency: BACKEND_URL becomes
>       # an environment variable built from backend's url property.
>       - name: backend
>         properties:
>           BACKEND_URL: ~{backend/url}
> 
> resources:
>   - name: example
>     type: example-type
>     properties:
>       example-prop: my-example-prop
> 
>   - name: uaa
>     type: org.cloudfoundry.managed-service
>     parameters:
>       service: xsuaa
>       service-plan: application
>       # Resource parameters feed service configuration.
>       # ~{example/example-prop} pulls a value from the 'example' resource.
>       config:
>         example-prop: ~{example/example-prop}
>     properties:
>       # This property is a REFERENCE SOURCE only. It is resolved from
>       # example/example-prop and exposed so other entities can read it as
>       # ~{uaa/pro1}. It is consumed above by the app-router module.
>       pro1: ~{example/example-prop}
> ```

Note the following about the example above:

-   The `java` module provides a dependency named `backend`, which exposes a `url` property. Its value is built from `${default-live-url}`, which always resolves to the live \(non-idle\) application URL. This is the recommended choice when the property is consumed by a **resource**, because resource parameters are resolved during the initial phase of deployment, before idle applications are started.
-   **Environment variables are injected only into applications \(modules\).** The `app-router` module gets two environment variables — `UAA_SHARED` and `BACKEND_URL` — because they are declared in the `properties` block of that module's `requires` dependencies. This is the only place a `~{...}` property reference becomes an environment variable.
-   **A property defined on a resource does not become an environment variable.** A resource's `properties` — such as `pro1` on the `uaa` resource — serve solely as a source of values that other entities can reference through the `~{resource-name/property}` syntax. Here `pro1` is resolved from `example/example-prop` and exposed so that `app-router` can consume it as `~{uaa/pro1}`.
-   References to provided properties can also be used in resource **parameter** values, as shown in the `config` block of the `uaa` resource, where `~{example/example-prop}` uses the fully qualified cross-reference syntax. These parameter values feed service configuration, not environment variables.



### Property Reference Syntax

Property references use the `~{...}` syntax. Two forms are supported:

-   Short form \(`~{property}`\): valid when the reference appears inside a `requires` entry's own `properties` or `parameters` block. The resolver identifies the source from the enclosing `requires` block, so no prefix is needed.
-   Fully qualified form \(`~{requires-name/property}`\): required when the reference appears outside a `requires` block — for example, at the module's top-level `properties` or `parameters`, or inside a resource's `parameters`. The requires-name tells the resolver which `requires` entry provides the value.

> ### Sample Code:  
> The module `staticapp` uses both forms for the same property. Inside the `external-configurations` requires block the short form is valid. At module level, the fully qualified form is required.
> 
> ```
> modules:
>   - name: staticapp
>     parameters:
>       module-param: ~{external-configurations/a-config-property}.inModuleParameter   # fully qualified — at module level
>     properties:
>       module-prop: ~{external-configurations/a-config-property}.directly             # fully qualified — at module level
>     requires:
>       - name: external-configurations
>         parameters:
>           param-in-requires: ~{a-config-property}.inRequiresParam      # short form — inside requires block
>         properties:
>           prop-in-requires: ~{a-config-property}.inRequiresProperty    # short form — inside requires block
>       - name: myBackingService
> ```

The fully qualified form also lets you combine values from multiple `requires` entries into a single structured property. The SAP Cloud Deployment service supports this as an extension of the standard syntax, enabling you to declare implicit groups, as illustrated in the following example:

> ### Sample Code:  
> Syntax Extension: Alternative Grouping of MTA Properties
> 
> ```
> modules:
>   - name: pricing-ui
>     type: javascript.nodejs
>     properties:
>       API:
>        - key: internal1
>          protocol: ~{price_opt/protocol}
>        - key: external
>          url: ~{competitor_data/url}
>          api_keys: ~{competitor_data/creds}
>     requires:
>       - name: competitor_data
>       - name: price_opt
>   - name: pricing-backend
>     type: java.tomcat
>     provides:
>       - name: price_opt
>         properties:
>           protocol: http
> 
> resources:
>   - name: competitor_data
>     properties:
>       url: "https://marketwatch.acme.com/"
>       creds:
>         app_key: 25892e17-80f6
>         secret_key: cd171f7c-560d
> ```



### Resolution Order

Values are resolved in a fixed order during deployment. Understanding it explains which value "wins" when the same name is defined at multiple levels, and why a reference is sometimes still empty.

1.  **Descriptors are merged first.** The deployment descriptor \(`mtad.yaml`\) is merged with any extension descriptors \(`.mtaext`\) before any placeholder is resolved. Extension descriptors therefore override literal values, and the overridden result is what later steps work with.
2.  **System \(read-only\) parameters are collected**, such as `${org}`, `${space}`, and `${default-domain}`. These are available to everything resolved afterward.
3.  **A single resolution pass then runs, in this order:**
    1.  **Parameters** \(`${...}`\) are resolved and validated.
    2.  **Properties** \(`${...}` inside property values\) are resolved. This is why a property may reference a parameter, but a parameter must not depend on a property.
    3.  **Cross-MTA `configuration` references** are resolved \(looked up from other already-deployed MTAs\).
    4.  **`provides` / `requires` references** \(`~{...}`\) are resolved last, so a `~{...}` can consume any value produced in the earlier phases.


**Precedence when the same parameter is defined at multiple levels** \(most specific wins\):

For module parameters, from highest to lowest precedence:

1.  Required-dependency level
2.  Module level
3.  Module-type level
4.  Global \(top-level\)

For resource parameters, from highest to lowest precedence:

1.  Resource level
2.  Resource-type level

> ### Note:  
> If a `~{...}` reference points at a value that cannot exist until later in the deployment \(for example, a service instance GUID\), it is deferred and resolved in a later phase. See [Dynamic Parameters](parameters-and-properties-490c8f7.md#loio490c8f71e2b74bc0a59302cada66117c__section_kdm_3qt_txb).



<a name="loio490c8f71e2b74bc0a59302cada66117c__section_kdm_3qt_txb"/>

## Dynamic Parameters

Unlike the template placeholders described above, dynamic parameters are resolved in a later deployment phase, once the referenced entity exists.

In some cases, it is required to use a value that is unknown before deployment — for example, the GUID of another service instance. The GUID of a newly created service instance is not known before the creation of that service, but it might be consumed later during the same MTA deployment.

> ### Note:  
> Currently, this feature is limited to resolving the service GUID for the following resource types:
> 
> -   `org.cloudfoundry.managed-service`
> -   `org.cloudfoundry.user-provided-service`
> -   `org.cloudfoundry.existing-service`

Resolved parameters can only be referenced from other resources or from a cross-MTA dependency. References from modules are not resolved.

> ### Sample Code:  
> MTA Deployment Descriptor \(mtad.yaml\)
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
> To use this feature, declare `${service-guid}` inside the `properties` section of the resource. The consumer of the service GUID value must add the respective resource name to its `requires` section and specify the `processed-after` parameter, because the order of resource processing must be explicitly described.



### Dynamic Parameters Across MTAs

Resolved parameters can also be referenced from a cross-MTA dependency, allowing a service instance GUID to be referenced from another MTA.

The following example shows the dependency declaration referencing a dynamic parameter in the deployment descriptor of the "provider" MTA:

> ### Sample Code:  
> Provider MTA \(mtad.yaml\)
> 
> ```
> _schema-version: 3
> ID: dynamic-service-guid-provider
> version: 1.0.0
> 
> modules:
>   - name: app-provider
>     type: staticfile
>     path: appBits.zip
>     provides:
>       - name: db-guid
>         public: true
>         parameters:
>           visibility:
>             - org: ${org}
>               space: ${space}
>         properties:
>           db-instanceid: ~{hana-service/my-db-service-guid}
>     requires:
>       - name: hana-service
> 
> resources:
>   - name: hana-service
>     type: org.cloudfoundry.managed-service
>     parameters:
>       service: hana
>       service-plan: schema
>     properties:
>       my-db-service-guid: ${service-guid}
> ```

The following example shows the dependency declaration in the deployment descriptor of the "consumer" MTA:

> ### Sample Code:  
> Consumer MTA \(mtad.yaml\)
> 
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



<a name="loio490c8f71e2b74bc0a59302cada66117c__section_parameterTables"/>

## Reference: Parameter Tables



### Top-Level Parameters

**Top-Level Parameters**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Scope

</th>
<th valign="top">

Read-Only / Write

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

Top-Level

</td>
<td valign="top">

Write

</td>
<td valign="top">

Applies namespace to application names \(app-names\), service names \(service-names\), application routes \(app-routes\) as suffix or prefix \(as-suffix\). If the namespace value is not provided in the CLI options, it is not applied.

See [Fine-Grained Configuration](namespaces-b28fd77.md#loiob28fd77836d44bde8c404618bf0f1228__section_hmf_khn_xcc).

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

Top-Level

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

Top-Level

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

Top-Level

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

Top-Level

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

Top-Level

</td>
<td valign="top">

Read-Only

</td>
<td valign="top">

The authorization URL as specified in the cloud controller's `/v2/info` endpoint.

</td>
<td valign="top">

Generated as described in the description.

</td>
<td valign="top">

`https://login.cf.eu10-004.hana.ondemand.com`

</td>
</tr>
<tr>
<td valign="top">

`bg-dependency-aware-stop-order`

> ### Note:  
> This parameter is currently experimental.



</td>
<td valign="top">

Top-Level

</td>
<td valign="top">

Write

</td>
<td valign="top">

Ensures that during the final phase of a blue-green deployment, idle applications are stopped and restarted in a dependency-aware order based on the dependencies defined in the `deployed-after` attribute. This prevents transient failures caused by short-lived unavailability of dependent modules. First, dependent modules are stopped, then their dependencies are restarted, and finally the dependent modules are updated and started.

> ### Note:  
> When both are specified, the command-line option `--dependency-aware-stop-order` overrides the `bg-dependency-aware-stop-order` descriptor parameter.



</td>
<td valign="top">

false

</td>
<td valign="top">

```

parameters: 
    bg-dependency-aware-stop-order: true
```



</td>
</tr>
<tr>
<td valign="top">

`controller-url`

</td>
<td valign="top">

Top-Level

</td>
<td valign="top">

Read-Only

</td>
<td valign="top">

The URL of the cloud controller

</td>
<td valign="top">

Generated as described in the description.

</td>
<td valign="top">

`https://api.cf.eu10-004.hana.ondemand.com`

</td>
</tr>
<tr>
<td valign="top">

`default-domain`

</td>
<td valign="top">

Top-Level

</td>
<td valign="top">

Read-Only

</td>
<td valign="top">

The default domain of the target organization \(configured in the Cloud Foundry environment\). The value is coming from CF API endpoint [Get default domain](https://v3-apidocs.cloudfoundry.org/index.html#get-default-domain), and normally, it depends on the shared domains in the current organization.

</td>
<td valign="top">

Generated as described in the description.

</td>
<td valign="top">

> ### Example:  
> If MTA deployment is done in a target org/space with CF API endpoint that is equal to `api.eu10-004.hana.ondemand.com`, the value of `default-domain` would be `cfapps.eu10-004.hana.ondemand.com`.

> ### Example:  
> If MTA deployment is done in a target org/space with CF API endpoint that is equal to `api.eu10.hana.ondemand.com`, the value of `default-domain` would be `cfapps.eu10.hana.ondemand.com`.



</td>
</tr>
<tr>
<td valign="top">

`region-domain`

</td>
<td valign="top">

Top-Level

</td>
<td valign="top">

Read-Only

</td>
<td valign="top">

The domain of the current region. For more information, refer to the **Domain** column in [Regions and API Endpoints Available for the Cloud Foundry Environment](../10-concepts/regions-and-api-endpoints-available-for-the-cloud-foundry-environment-f344a57.md). When a region has multiple CF API endpoints, it will point to the domain of the respective endpoint used for the deployment.

> ### Note:  
> The parameters `region-primary-domain` and `region-domain` are equal when used in most of the regions. They are different when MTA deployments are done in a target org/space in different CF APIs in one region.



</td>
<td valign="top">

Generated as described in the description.

</td>
<td valign="top">

> ### Example:  
> If MTA deployment is done in a target org/space with CF API endpoint that is equal to `api.eu10.hana.ondemand.com`, the value of `region-domain` would be `eu10.hana.ondemand.com`.

> ### Example:  
> If MTA deployment is done in a target org/space with CF API endpoint that is equal to `api.eu10-004.hana.ondemand.com`, the value of `region-domain` would be `eu10-004.hana.ondemand.com`.



</td>
</tr>
<tr>
<td valign="top">

`region-primary-domain`

</td>
<td valign="top">

Top-Level

</td>
<td valign="top">

Read-Only

</td>
<td valign="top">

The primary domain of a region. For more information, refer to the **Domain** column in [Regions and API Endpoints Available for the Cloud Foundry Environment](../10-concepts/regions-and-api-endpoints-available-for-the-cloud-foundry-environment-f344a57.md). When a region has multiple CF API endpoints, it will point to the primary domain \(the first one\).

> ### Note:  
> The parameters `region-primary-domain` and `region-domain` are equal when used in most of the regions. They are different when MTA deployments are done in a target org/space in different CF APIs in one region.



</td>
<td valign="top">

Generated as described in the description.

</td>
<td valign="top">

> ### Example:  
> If MTA deployment is done in a target org/space with CF API endpoint that is equal to `api.eu10.hana.ondemand.com`, the value of `region-primary-domain` would be `eu10.hana.ondemand.com`.

> ### Example:  
> If MTA deployment is done in a target org/space with CF API endpoint that is equal to `api.eu10-004.hana.ondemand.com`, the value of `region-primary-domain` would be `eu10.hana.ondemand.com`.



</td>
</tr>
<tr>
<td valign="top">

`deploy-url`

</td>
<td valign="top">

Top-Level

</td>
<td valign="top">

Read-Only

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

`enable-parallel-deployments`

</td>
<td valign="top">

Top-Level

</td>
<td valign="top">

Write

</td>
<td valign="top">

Defines if parallel deployment of modules is enabled. When enabled, modules without explicitly set `deployed-after` parameter are deployed in parallel. For more information, see [Parallel Module Deployment](parallel-module-deployment-0384158.md).

</td>
<td valign="top">

no

</td>
<td valign="top">

```
parameters:
  enable-parallel-deployments: true
```



</td>
</tr>
<tr>
<td valign="top">

`generated-password`

</td>
<td valign="top">

Top-Level

</td>
<td valign="top">

Read-Only

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

Top-Level

</td>
<td valign="top">

Read-Only

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

Top-Level

</td>
<td valign="top">

Write

</td>
<td valign="top">

When specified on module level, it indicates if the existing routes of the module's corresponding application should be kept even if they are not defined within the deployment and/or extension descriptors.

When specified on top level, under the `parameters` section of the descriptor, it indicates if the existing routes of all applications within that MTA should be kept.

> ### Note:  
> -   The module-level variant of the parameter has priority over the top-level parameter.
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

Top-Level

</td>
<td valign="top">

Read-Only

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

Top-Level

</td>
<td valign="top">

Read-Only

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

Top-Level

</td>
<td valign="top">

Read-Only

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

Top-Level

</td>
<td valign="top">

Read-Only

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

Top-Level

</td>
<td valign="top">

Read-Only

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

Top-Level

</td>
<td valign="top">

Read-Only

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

Top-Level

</td>
<td valign="top">

Read-Only

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

Top-Level

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

Top-Level

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

`com.sap.sample`

</td>
</tr>
</table>



### Dependency-Specific Parameters

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

Read-Only / Write

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

Module-Required Dependency

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

Module-Required Dependency

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

Module-Required Dependency

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

Module-Required Dependency

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

Module-Provided Dependency

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

Module-Provided Dependency

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



### Level-Specific Parameter Lists

-   [Module-Specific Parameters](modules-177d34d.md#loio177d34d45e3d4fd99f4eeeffc5814cf1__section_moduleSpecificParameters)
-   [Resource-Specific Parameters](resources-9e34487.md#loio9e34487b1a8643fb9a93ae6c4894f015__section_resourceSpecificParameters)
-   [Module Hooks - Specific Parameters](module-hooks-b9245ba.md#loiob9245ba90aa14681a416065df8e8c593__section_byz_kcf_wjb)

