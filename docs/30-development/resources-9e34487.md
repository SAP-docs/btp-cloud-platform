<!-- loio9e34487b1a8643fb9a93ae6c4894f015 -->

# Resources

The application modules defined in the “modules” section of the deployment descriptor may depend on **resources**.

The resources may be used as:

-   platform services managed by the deployer or only used by the applications
-   configuration entries used by the applications and services

In the `resources` section, the following elements are mandatory:

-   `name` - Must be unique within the MTA it identifies

Optional resource attributes include:

-   `type` - the resource **type** is one of a reserved list of resource types supported by the MTA-aware deployment tools, for example: `com.sap.xs.uaa`, `com.sap.xs.hdi-container`, `com.sap.xs.job-scheduler`; the **type** indicates to the deployer how to discover, allocate, or provision the resource, for example, a managed service such as a database, or a user-provided service. When `type` is not defined, `resource` is used for configurations only for other modules and resources.
-   `description` - non-translatable, free-text string; the string is not meant to be presented on application user interfaces \(UI\)
-   `properties` - a structured set of name-value pairs
-   `parameters` - reserved variables that affect the behavior of the MTA-aware tools, such as the deployer
-   `active` - its value can be `true` or `false` and the default value is `true`. If set to `false`, the resource is not processed and it is ignored in the `requires` list of the application that requires it.
-   `processed-after` - the attribute is used to create an order, in which resources should be processed. If a resource has this attribute, it will be processed after the other resources in a higher position are processed. The attribute value is a structured set of a list comprised of other resource names of the same MTA.

    > ### Tip:  
    > By default recourses process in parallel, but if you want to enable an order of resources, see [Sequential Resource Processing](sequential-resource-processing-b93db81.md).

-   `optional`- its value can be `true` or `false` and the default value is `false`. If set to `true`, the resource processing is fail-safe.



<a name="loio9e34487b1a8643fb9a93ae6c4894f015__section_activeAndInactiveResources"/>

## Active and Inactive Resources

If you deploy an application with a resource type attribute `active` set to `false`, the resource is not provisioned and no binding is created. If you have already deployed the application with the resource type attribute `active` set to `true`, the binding to the resource is removed.

**Deployment with `managed-service`, `existing-service` and `user-provided service`**

No binding is created and in case of `managed-service`, no service is created.

**Deployment with `org.cloudfoundry.existing-service-key` **

No binding to an application environment will be done in the following cases:

-   If the `org.cloudfoundry.existing-service-key` resource itself is set to `active: false`
-   If the `org.cloudfoundry.existing-service-key` resource is set to `active: true`, but refers to a resource, which is set to `active: false`

**Deployment with configuration resources \(cross MTA dependencies\)**

If the configuration resource is set to `active: false`, then:

-   If the requires section of the module type expects a list, then the environment variable assigned to this list is empty and subscriptions between the modules is not created
-   If the requires section does not expect a list, then no environment variable is created

See section “Optional resources” below for more information.

> ### Restriction:  
> System-specific parameters for the deployment descriptor must be included in a so-called MTA deployment extension descriptor.



<a name="loio9e34487b1a8643fb9a93ae6c4894f015__section_optionalResources"/>

## Optional Resources

To describe resources that are not mission-critical for the operation of your Multitarget Application, proceed as described below.

> ### Note:  
> This option is available with schema version `3.1`.

You can declare some resources as optional, which mitigates the cases when they are not listed, not available, or have failed to be created or updated. This means that when the deployer cannot allocate the required resource due to any of these reasons, it generates a warning and continues processing. Alternatively, if a resource is not declared as optional, the deployer generates an error and stops processing.

The following excerpt is a code example for the `MANIFEST.MF` file.

> ### Sample Code:  
> ```
> ...
> resources:
> ...
> - name: log
>   type: com.sap.xs.auditlog
>   optional: true
> ...
> ```

In the above example:

-   If the `log` managed resource is not provided by the platform or landscape, a warning is logged and traced and the MTA deployment continues while ignoring the error.
-   The available values for the `optional` parameter are `true` and `false`, with the latter being the default.



<a name="loio9e34487b1a8643fb9a93ae6c4894f015__section_mtaResourceTypes"/>

## Generic MTA Resource Types

-   `org.cloudfoundry.managed-service`

    In cases you have to choose a managed service and/or service plan that is not listed in [Generic MTA Resource Types](resources-9e34487.md#loio9e34487b1a8643fb9a93ae6c4894f015__section_mtaResourceTypes), you define it using the `org.cloudfoundry.managed-service` resource type with the following parameters:

    -   \(Required\) `service` - Name of the service to create.
    -   \(Optional\) `service-name` - Service instance name. Default value is the resource name.

        > ### Note:  
        > Service names that do not comply with the Cloud Foundry limitation of 50 symbols are automatically corrected. In such cases, the name is shortened and its end is replaced with a hash code.

    -   \(Required\) `service-plan` - Name of the service to create.

    For example:

    > ### Sample Code:  
    > ```
    > resources:
    >   - name: my-postgre-service
    >     type: org.cloudfoundry.managed-service
    >     parameters:
    >       service: postgresql
    >       service-plan: v9.6-dev
    > 
    > ```

    > ### Note:  
    > To choose a different service plan for a predefined MTA resource type, for example to change the service plan for `PostgreSQL` service, you define it using:
    > 
    > > ### Sample Code:  
    > > ```
    > > resources:
    > >   - name: my-postgre-service
    > >     type: org.postgresql
    > >     parameters:
    > >       service-plan: v9.6-dev
    > > 
    > > ```

-   `org.cloudfoundry.existing-service`

    То indicate that the \(named\) service exists, without managing its lifecycle, you define the service name by using the `org.cloudfoundry.managed-service` resource type with the following parameters:

    -   \(Optional\) `service-name` - Service instance name. Default value is the resource name.

-   `org.cloudfoundry.existing-service-key`

    Existing service keys can be modeled as a resource of type `org.cloudfoundry.existing-service-key`, which checks and uses their credentials. For more information, see [Service Keys](service-keys-32297f1.md).

-   `org.cloudfoundry.user-provided-service`

    Create or update a user-provided service configured with the following resource parameters:

    -   \(Optional\) `service-name` - Name of the service to create. Default value is the resource name.

        > ### Note:  
        > Service names that do not comply with the Cloud Foundry limitation of 50 symbols are automatically corrected. In such cases, the name is shortened and its end is replaced with a hash code.

    -   \(Required\) `config` - Map value, containing the service creation configuration, for example url and user credentials \(user and password\)

    > ### Example:  
    > > ### Sample Code:  
    > > ```
    > > resources:
    > >   - name: my-destination-service
    > >     type: org.cloudfoundry.user-provided-service
    > >     parameters:
    > >       config:
    > >         <credential1>: <value1>
    > >         <credential2>: <value2>
    > > 
    > > ```

-   `configuration`

    For more information, see [Cross-MTA Dependencies](cross-mta-dependencies-b8e1953.md).




<a name="loio9e34487b1a8643fb9a93ae6c4894f015__section_predefinedMTAResourceTypes"/>

## Predefined MTA Resource Types

Modify the default MTA resource types by providing specific properties or parameters in the MTA deployment descriptor.

**Predefined MTA Resource Types and Mapped Services**


<table>
<tr>
<th valign="top">

Resource Type

</th>
<th valign="top">

Service

</th>
<th valign="top">

Service Plan

</th>
<th valign="top">

Created Service

</th>
</tr>
<tr>
<td valign="top">

`com.sap.xs.hana-schema`

> ### Example:  
> > ### Sample Code:  
> > ```
> > name: hcsp-sch
> > type: com.sap.xs.hana-schema
> > parameters:
> > service-name: HCSP_SCH
> > config:
> > database_id: 9bf1f23a-123c-456e-b789-ff12ea34a5dc
> > schema: HCSP_DB
> > ```



</td>
<td valign="top">

`hana`

</td>
<td valign="top">

`schema`

</td>
<td valign="top">

Plain schema

</td>
</tr>
<tr>
<td valign="top">

`com.sap.xs.hana-securestore`

</td>
<td valign="top">

`hana`

</td>
<td valign="top">

`securestore`

</td>
<td valign="top">

SAP HANA secure store

</td>
</tr>
<tr>
<td valign="top">

`com.sap.xs.hdi-container`

> ### Note:  
> modules: When using the free trial subaccount, modify the default service:
> 
> > ### Sample Code:  
> > ```
> > resources:
> > 	- name: my-hdi-service 
> > 	  type: com.sap.xs.hdi-container 
> > 	  parameters: 
> > 		service: hanatrial
> > ```



</td>
<td valign="top">

`hana`

</td>
<td valign="top">

`hdi-shared`

</td>
<td valign="top">

HDI container

</td>
</tr>
<tr>
<td valign="top">

`com.sap.xs.jobscheduler`

</td>
<td valign="top">

`jobscheduler`

</td>
<td valign="top">

`lite`

</td>
<td valign="top">

Job Scheduler

</td>
</tr>
<tr>
<td valign="top">

`com.sap.xs.uaa`

</td>
<td valign="top">

`xsuaa`

</td>
<td valign="top">

`applicaton`

</td>
<td valign="top">

Application UAA

</td>
</tr>
<tr>
<td valign="top">

`com.sap.xs.uaa-application`

</td>
<td valign="top">

`xsuaa`

</td>
<td valign="top">

`application`

</td>
<td valign="top">

Application UAA

</td>
</tr>
<tr>
<td valign="top">

`com.sap.xs.uaa-devuser`

</td>
<td valign="top">

`xsuaa`

</td>
<td valign="top">

`application`

</td>
<td valign="top">

Application UAA

</td>
</tr>
<tr>
<td valign="top">

`com.sap.xs.uaa-space`

</td>
<td valign="top">

`xsuaa`

</td>
<td valign="top">

`application`

</td>
<td valign="top">

Application UAA

</td>
</tr>
<tr>
<td valign="top">

`com.sap.xs.application-logs`

> ### Restriction:  
> This resource type is now deprecated. Use `application-logs` instead.



</td>
<td valign="top">

`application-logs`

</td>
<td valign="top">

`lite`

</td>
<td valign="top">

Streams logs of bound applications to a central application logging stack

</td>
</tr>
<tr>
<td valign="top">

`com.sap.portal.site-content`

> ### Restriction:  
> Use only with the SAP Node.js module `@sap/site-content-deployer`



</td>
<td valign="top">

`portal-services`

</td>
<td valign="top">

`site-content`

</td>
<td valign="top">

Portal services

</td>
</tr>
<tr>
<td valign="top">

`com.sap.portal.site-host`

> ### Restriction:  
> Only for use with the SAP Node.js module `@sap/site-entry` 



</td>
<td valign="top">

`portal-services`

</td>
<td valign="top">

`site-host`

</td>
<td valign="top">

Portal services

</td>
</tr>
<tr>
<td valign="top">

`com.sap.xs.auditlog`

</td>
<td valign="top">

`auditlog`

</td>
<td valign="top">

`standard`

</td>
<td valign="top">

Audit log service

</td>
</tr>
<tr>
<td valign="top">

`auditlog`

</td>
<td valign="top">

`auditlog`

</td>
<td valign="top">

`standard`

</td>
<td valign="top">

Audit log service

</td>
</tr>
<tr>
<td valign="top">

`autoscaler`

</td>
<td valign="top">

`autoscaler`

</td>
<td valign="top">

`lite`

</td>
<td valign="top">

Automatically increase or decrease the number of application instances based on a policy you define.

</td>
</tr>
<tr>
<td valign="top">

`application-logs`

</td>
<td valign="top">

`application-logs`

</td>
<td valign="top">

`lite`

</td>
<td valign="top">

Streams logs of bound applications to a central application logging stack

</td>
</tr>
<tr>
<td valign="top">

`connectivity`

</td>
<td valign="top">

`connectivity` 

</td>
<td valign="top">

`lite`

</td>
<td valign="top">

Establishes a secure and reliable connectivity between cloud applications and on-premise systems

</td>
</tr>
<tr>
<td valign="top">

`destination`

</td>
<td valign="top">

`destination`

</td>
<td valign="top">

`lite`

</td>
<td valign="top">

Provides a secure and a reliable access to destination configurations

</td>
</tr>
<tr>
<td valign="top">

`feature-flags`

</td>
<td valign="top">

`feature-flags` 

</td>
<td valign="top">

`lite`

</td>
<td valign="top">

Feature Flags service for controlling feature rollout

</td>
</tr>
<tr>
<td valign="top">

`ml-foundation-services`

</td>
<td valign="top">

`ml-foundation-services`

</td>
<td valign="top">

`lite`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

`objectstore`

</td>
<td valign="top">

`objectstore`

</td>
<td valign="top">

`s3-standard`

</td>
<td valign="top">

Highly available and distributed consistent object store

</td>
</tr>
<tr>
<td valign="top">

`org.mongodb`

> ### Restriction:  
> This resource type is now deprecated. Use `mongodb` instead.



</td>
<td valign="top">

`mongodb`

</td>
<td valign="top">

`v3.0-container`

</td>
<td valign="top">

MongoDB document-oriented database system.

</td>
</tr>
<tr>
<td valign="top">

`mongodb`

</td>
<td valign="top">

`mongodb`

</td>
<td valign="top">

`v3.0-container`

</td>
<td valign="top">

MongoDB document-oriented database system

</td>
</tr>
<tr>
<td valign="top">

`org.postgresql`

> ### Restriction:  
> This resource type is now deprecated. Use `postgresql` instead.



</td>
<td valign="top">

`postgresql`

</td>
<td valign="top">

`v9.4-container`

</td>
<td valign="top">

PostgreSQL object-relational database system

</td>
</tr>
<tr>
<td valign="top">

`postgresql`

</td>
<td valign="top">

`postgresql`

</td>
<td valign="top">

`v9.4-container`

</td>
<td valign="top">

PostgreSQL object-relational database system

</td>
</tr>
<tr>
<td valign="top">

`com.rabbitmq`

> ### Restriction:  
> This resource type is now deprecated. Use `rabbitmq` instead.



</td>
<td valign="top">

`rabbitmq`

</td>
<td valign="top">

`v3.6-container`

</td>
<td valign="top">

RabbitMQ messaging

</td>
</tr>
<tr>
<td valign="top">

`rabbitmq`

</td>
<td valign="top">

`rabbitmq`

</td>
<td valign="top">

`v3.6-container`

</td>
<td valign="top">

RabbitMQ messaging

</td>
</tr>
<tr>
<td valign="top">

`io.redis`

> ### Restriction:  
> This resource type is now deprecated. Use `redis` instead.



</td>
<td valign="top">

`redis`

</td>
<td valign="top">

`v3.0-container`

</td>
<td valign="top">

Redis in-memory data structure store

</td>
</tr>
<tr>
<td valign="top">

`redis`

</td>
<td valign="top">

`redis`

</td>
<td valign="top">

`v3.0-container`

</td>
<td valign="top">

Redis in-memory data structure store

</td>
</tr>
</table>



<a name="loio9e34487b1a8643fb9a93ae6c4894f015__section_resourceSpecificParameters"/>

## Resource-Specific Parameters

Resource parameters have platform-specific semantics. To reference a parameter value, use the placeholder notation <code>${<i class="varname">&lt;parameter&gt;</i>}</code>, for example, `${default-host}`.

> ### Tip:  
> It is also possible to declare metadata for parameters and properties defined in the MTA deployment description; the mapping is based on the parameter or property keys. For example, you can specify if a parameter is **required** \(`optional; false`\) or can be modified `overwritable: true`.

The following parameters are supported:

> ### Note:  
> If you can't find a specific parameter from the native Cloud Foundry manifest here, refer to [Prerequisites and Restrictions](multitarget-applications-in-the-cloud-foundry-environment-d04fc0e.md#loiod04fc0e2ad894545aebfd7126384307c__section_ph2_r5h_1cb) to see which Cloud Foundry features are currently not supported.

**MTA Development and Deployment Parameters**


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

`apply-namespace`

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

Write

</td>
<td valign="top">

Defines service creation parameters. More information in [Service Creation Parameters](service-creation-parameters-a36df26.md).

</td>
<td valign="top">

n/a

</td>
<td valign="top">

See [Service Creation Parameters](service-creation-parameters-a36df26.md).

</td>
</tr>
<tr>
<td valign="top">

`syslog-drain-url`

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
<tr>
<td valign="top">

`default-container-name`

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

`service`

</td>
<td valign="top">

 

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
</table>



> ### Tip:  
> For a better understanding of the interactions among the service, service broker, and service instances, see [Provisioning and integrating service instances](https://docs.cloudfoundry.org/devguide/services/).

**Related Information**  


[Services Overview](https://docs.cloudfoundry.org/services/overview.html)

[Provisioning and integrating service instances](https://docs.cloudfoundry.org/devguide/services/)

