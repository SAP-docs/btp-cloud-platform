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
-   `description`
-   `properties`
-   `parameters`
-   `active` - its value can be `true` or `false` and the default value is `true`. If set to `false`, the resource is not processed and it is ignored in the `requires` list of the application that requires it.
-   `optional`



<a name="loio9e34487b1a8643fb9a93ae6c4894f015__section_activeAndInactiveResources"/>

## Active and Inactive Resources

If you deploy an application with a resource type attribute `active` set to `false`, the resource is not provisioned and no binding is created. If you have already deployed the application with the resource type attribute `active` set to `true`, the binding to the resource is removed.

**Deployment with `managed-service`, `existing-service` and `user-provided service`**

No binding is created and in case of `managed-service`, no service is created .

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

    In cases you have to choose a managed service and/or service plan that is not listed in [Generic MTA Resource Types](Resources_9e34487.md#loio9e34487b1a8643fb9a93ae6c4894f015__section_mtaResourceTypes), you define it using the `org.cloudfoundry.managed-service` resource type with the following parameters:

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
    > To choose a different service plan for a predefined MTA resource type, for example, to change the service plan for `PostgreSQL` service, you define it using:
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

    То аssume that the named service exists, but to not manage its lifecycle, you define the service name by using the `org.cloudfoundry.managed-service` resource type with the following parameters:

    -   \(Optional\) `service-name` - Service instance name. Default value is the resource name.
-   `org.cloudfoundry.existing-service-key`

    Existing service keys can be modeled as a resource of type `org.cloudfoundry.existing-service-key`, which checks and uses their credentials. For more information, see [Service Keys](Service_Keys_32297f1.md).

-   `org.cloudfoundry.user-provided-service`

    Create or update a user-provided service configured with the following resource parameters:

    -   \(Optional\) `service-name` - Name of the service to create. Default value is the resource name.

        > ### Note:  
        > Service names that do not comply with the Cloud Foundry limitation of 50 symbols are automatically corrected. In such cases, the name is shortened and its end is replaced with a hash code.

    -   \(Required\) `config` - Map value, containing the service creation configuration, for example, url and user credentials \(user and password\)
    > ### Example:  

    > ### Sample Code:  
    > ```
    > resources:
    >   - name: my-destination-service
    >     type: org.cloudfoundry.user-provided-service
    >     parameters:
    >       config:
    >         <credential1>: <value1>
    >         <credential2>: <value2>
    > 
    > ```

-   `configuration`

    For more information, see [Cross-MTA Dependencies](Cross-MTA_Dependencies_b8e1953.md).




<a name="loio9e34487b1a8643fb9a93ae6c4894f015__section_predefinedMTAResourceTypes"/>

## Predefined MTA Resource Types

Modify the default MTA resource types by providing specific properties or parameters in the MTA deployment descriptor.

<a name="loio9e34487b1a8643fb9a93ae6c4894f015__table_mtaResourceTypes"/>Predefined MTA Resource Types and Mapped Services


<table>
<tr>
<th>

Resource Type



</th>
<th>

Service



</th>
<th>

Service Plan



</th>
<th>

Created Service



</th>
</tr>
<tr>
<td>

`com.sap.xs.hana-sbss`



</td>
<td>

`hana`



</td>
<td>

`sbss`



</td>
<td>

Service-broker security



</td>
</tr>
<tr>
<td>

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
<td>

`hana`



</td>
<td>

`schema`



</td>
<td>

Plain schema



</td>
</tr>
<tr>
<td>

`com.sap.xs.hana-securestore`



</td>
<td>

`hana`



</td>
<td>

`securestore`



</td>
<td>

SAP HANA secure store



</td>
</tr>
<tr>
<td>

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
<td>

`hana`



</td>
<td>

`hdi-shared`



</td>
<td>

HDI container



</td>
</tr>
<tr>
<td>

`com.sap.xs.jobscheduler`



</td>
<td>

`jobscheduler`



</td>
<td>

`lite`



</td>
<td>

Job Scheduler



</td>
</tr>
<tr>
<td>

`com.sap.xs.uaa`



</td>
<td>

`xsuaa`



</td>
<td>

`applicaton`



</td>
<td>

Application UAA



</td>
</tr>
<tr>
<td>

`com.sap.xs.uaa-application`



</td>
<td>

`xsuaa`



</td>
<td>

`application`



</td>
<td>

Application UAA



</td>
</tr>
<tr>
<td>

`com.sap.xs.uaa-devuser`



</td>
<td>

`xsuaa`



</td>
<td>

`application`



</td>
<td>

Application UAA



</td>
</tr>
<tr>
<td>

`com.sap.xs.uaa-space`



</td>
<td>

`xsuaa`



</td>
<td>

`application`



</td>
<td>

Application UAA



</td>
</tr>
<tr>
<td>

`com.sap.xs.application-logs`

> ### Restriction:  
> This resource type is now deprecated. Use `application-logs` instead.



</td>
<td>

`application-logs`



</td>
<td>

`lite`



</td>
<td>

Streams logs of bound applications to a central application logging stack



</td>
</tr>
<tr>
<td>

`com.sap.portal.site-content`

> ### Restriction:  
> Use only with the SAP Node.js module `@sap/site-content-deployer`



</td>
<td>

`portal-services`



</td>
<td>

`site-content`



</td>
<td>

Portal services



</td>
</tr>
<tr>
<td>

`com.sap.portal.site-host`

> ### Restriction:  
> Only for use with the SAP Node.js module `@sap/site-entry` 



</td>
<td>

`portal-services`



</td>
<td>

`site-host`



</td>
<td>

Portal services



</td>
</tr>
<tr>
<td>

`com.sap.xs.auditlog`



</td>
<td>

`auditlog`



</td>
<td>

`standard`



</td>
<td>

Audit log service



</td>
</tr>
<tr>
<td>

`auditlog`



</td>
<td>

`auditlog`



</td>
<td>

`standard`



</td>
<td>

Audit log service



</td>
</tr>
<tr>
<td>

`autoscaler`



</td>
<td>

`autoscaler`



</td>
<td>

`lite`



</td>
<td>

Automatically increase or decrease the number of application instances based on a policy you define.



</td>
</tr>
<tr>
<td>

`application-logs`



</td>
<td>

`application-logs`



</td>
<td>

`lite`



</td>
<td>

Streams logs of bound applications to a central application logging stack



</td>
</tr>
<tr>
<td>

`connectivity`



</td>
<td>

`connectivity` 



</td>
<td>

`lite`



</td>
<td>

Establishes a secure and reliable connectivity between cloud applications and on-premise systems



</td>
</tr>
<tr>
<td>

`destination`



</td>
<td>

`destination`



</td>
<td>

`lite`



</td>
<td>

Provides a secure and a reliable access to destination configurations



</td>
</tr>
<tr>
<td>

`feature-flags`



</td>
<td>

`feature-flags` 



</td>
<td>

`lite`



</td>
<td>

Feature Flags service for controlling feature rollout



</td>
</tr>
<tr>
<td>

`ml-foundation-services`



</td>
<td>

`ml-foundation-services`



</td>
<td>

`lite`



</td>
<td>

 



</td>
</tr>
<tr>
<td>

`objectstore`



</td>
<td>

`objectstore`



</td>
<td>

`s3-standard`



</td>
<td>

Highly available and distributed consistent object store



</td>
</tr>
<tr>
<td>

`org.mongodb`

> ### Restriction:  
> This resource type is now deprecated. Use `mongodb` instead.



</td>
<td>

`mongodb`



</td>
<td>

`v3.0-container`



</td>
<td>

MongoDB document-oriented database system.



</td>
</tr>
<tr>
<td>

`mongodb`



</td>
<td>

`mongodb`



</td>
<td>

`v3.0-container`



</td>
<td>

MongoDB document-oriented database system



</td>
</tr>
<tr>
<td>

`org.postgresql`

> ### Restriction:  
> This resource type is now deprecated. Use `postgresql` instead.



</td>
<td>

`postgresql`



</td>
<td>

`v9.4-container`



</td>
<td>

PostgreSQL object-relational database system



</td>
</tr>
<tr>
<td>

`postgresql`



</td>
<td>

`postgresql`



</td>
<td>

`v9.4-container`



</td>
<td>

PostgreSQL object-relational database system



</td>
</tr>
<tr>
<td>

`com.rabbitmq`

> ### Restriction:  
> This resource type is now deprecated. Use `rabbitmq` instead.



</td>
<td>

`rabbitmq`



</td>
<td>

`v3.6-container`



</td>
<td>

RabbitMQ messaging



</td>
</tr>
<tr>
<td>

`rabbitmq`



</td>
<td>

`rabbitmq`



</td>
<td>

`v3.6-container`



</td>
<td>

RabbitMQ messaging



</td>
</tr>
<tr>
<td>

`io.redis`

> ### Restriction:  
> This resource type is now deprecated. Use `redis` instead.



</td>
<td>

`redis`



</td>
<td>

`v3.0-container`



</td>
<td>

Redis in-memory data structure store



</td>
</tr>
<tr>
<td>

`redis`



</td>
<td>

`redis`



</td>
<td>

`v3.0-container`



</td>
<td>

Redis in-memory data structure store



</td>
</tr>
</table>



<a name="loio9e34487b1a8643fb9a93ae6c4894f015__section_resourceSpecificParameters"/>

## Resource-Specific Parameters

Resource parameters have platform-specific semantics. To reference a parameter value, use the placeholder notation `${*<parameter\>*}`, for example, `${default-host}`.

> ### Tip:  
> It is also possible to declare metadata for parameters and properties defined in the MTA deployment description; the mapping is based on the parameter or property keys. For example, you can specify if a parameter is **required** \(`optional; false`\) or can be modified `overwritable: true`.

The following parameters are supported:

<a name="loio9e34487b1a8643fb9a93ae6c4894f015__table_resourceSpecificParameters"/>MTA Development and Deployment Parameters


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

`default-container-name`



</td>
<td>

Yes



</td>
<td>

Default value for the container-name parameter that is used during HDI creation. It is based on the organization, space and service name, which are combined in a way that conforms to the container-name restrictions for length and legal characters.



</td>
<td>

Generated as described in the description.



</td>
<td>

 `INITIAL_INITIAL_SERVICE_NAME` 



</td>
</tr>
<tr>
<td>

`default-service-name`



</td>
<td>

Yes



</td>
<td>

The name of the service in the Cloud Foundry environment to be created for this resource, based on the resource name with or without a name-space prefix



</td>
<td>

The resource name with or without a name-space prefix



</td>
<td>

`nodejs-hdi-container`

`com.sap.xs2.samples.xsjshelloworld.nodejs-hdi-container`



</td>
</tr>
<tr>
<td>

`default-xsappname`



</td>
<td>

Yes



</td>
<td>

Default value for the `xsappname` parameter that is used during UAA creation. It is based on the service name, which is modified in a way that conforms to the `xsappname` restrictions for length and legal characters.



</td>
<td>

Generated as described in the description.



</td>
<td>

`xs_-deploy-service-database` \(if the service name is “`xs@-deploy-service-database`”\)



</td>
</tr>
<tr>
<td>

`service`



</td>
<td>

 



</td>
<td>

The type of the created service



</td>
<td>

Empty, or as specified in resource-type



</td>
<td>

`service: hana`



</td>
</tr>
<tr>
<td>

`service-key-name`



</td>
<td>

Write



</td>
<td>

Used when consuming an existing service key. Specifies the name of the service key. See Consumption of existing service keys for more information.



</td>
<td>

The name of the resource.



</td>
<td>

`service-key-name: my-service-key`



</td>
</tr>
<tr>
<td>

`service-name`



</td>
<td>

 



</td>
<td>

The name of the service in the Cloud Foundry environment to be created for this resource, based on the resource name with or without a name-space prefix.

> ### Note:  
> Service names that do not comply with the Cloud Foundry limitation of 50 symbols are automatically corrected. In such cases, the name is shortened and its end is replaced with a hash code.



</td>
<td>

`${default-service-name}`



</td>
<td>

`nodejs-hdi-container`

`com.sap.xs2.samples.xsjshelloworld.nodejs-hdi-container`



</td>
</tr>
<tr>
<td>

`service-plan`



</td>
<td>

 



</td>
<td>

The plan of the created service



</td>
<td>

Empty, or as specified in resource-type



</td>
<td>

`service-plan: hdi-shared`



</td>
</tr>
<tr>
<td>

`service-tags`



</td>
<td>

Write



</td>
<td>

Some services employ a list of custom tags, which provide an easier way for applications to parse `<VCAP_SERVICES>` for credentials. You can provide custom tags when creating a service instance. For more information, see [Service Tags](Service_Tags_3e36d13.md).



</td>
<td>

n/a



</td>
<td>

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
<td>

`service-broker`



</td>
<td>

 



</td>
<td>

Use this parameter to specify the service broker you want to employ when you create your service. This can be useful for testing purposes, among others.



</td>
<td>

Name of service broker you want to be used.



</td>
<td>

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
<td>

`skip-service-updates`



</td>
<td>

 



</td>
<td>

This parameter allows you to specify the service configuration changes to `ignore`, when deciding if you want to update a service instance – in particular changes of service `parameters`, `plan`, or `tags`.



</td>
<td>

The default value for all is `false`. The service instance would be updated on change in any of the configurations.



</td>
<td>

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
> For a better understanding of the interactions among the service, service broker, and service instances, see [section "Architecture and Terminology"](https://docs.cloudfoundry.org/devguide/services/).

**Related Information**  


[Services Overview](https://docs.cloudfoundry.org/services/overview.html)

[Managing Services](https://docs.cloudfoundry.org/devguide/services/)

