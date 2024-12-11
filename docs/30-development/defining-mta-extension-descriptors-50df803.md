<!-- loio50df803465324d36851c79fd07e8972c -->

# Defining MTA Extension Descriptors

The Multitarget Application \(МТА\) extension descriptor is a YAML file that contains data complementary to the deployment descriptor \(from MTA archive\). It has a structure similar to the one of the deployment descriptor, and you will normally find it placed outside of the MTA archive.

The data can be environment-specific or deployment-specific, for example, application scaling setup or credentials depending on the user who performs the deployment. This allows you to use the one and the same unmodifiable MTA archive and deploy it with different extension descriptors, resulting in different setups.

When you are deploying an MTA, you can provide several extension descriptors. The descriptors in the chain are considered in order, with each descriptor having a higher priority than the one it extends.

> ### Note:  
> The format and available options within the extension descriptor may change with newer versions of the MTA specification. You must always specify the schema version option when defining an extension descriptor to inform the SAP BTP which MTA specification version should be used. Furthermore, the schema version used within the extension descriptor and the deployment descriptor should always be the same.

> ### Note:  
> Each extension descriptor is defined in a separate file with an extension `.mtaext`.

In the examples below, we have a deployment descriptor, which has already been defined, and several extension descriptors.

MTA deployment descriptor:

> ### Example:  
> ```
> ----MTA Deployment descriptor-----
> _schema-version: '3.1'
> ID: sample.app
> version: 0.1.0
>  
> modules:
>   - name: my-app
>     type: application
>     parameters:
>       memory: 2GB
> ```

When an MTA with the above deployment descriptor is being deployed, the following steps are performed:

-   Validates the deployment descriptor against the MTA specification version `3.1`. If it is not compliant, the deployment will fail at the beginning
-   Defines an MTA module with type `application` that will end up into a Cloud Foundry application
-   Defines a parameter `memory` that equals to 2GB
-   …...
-   Creates a Cloud Foundry application that runs with 2GB memory

The following is a basic example of an extension descriptor that adds and overwrites data:

> ### Example:  
> ```
> ----prod.mtaext-----
> _schema-version: '3.1'
> ID: sample.app.prod
> extends: sample.app
>  
> modules:
>   - name: my-app
>     parameter:
>       memory: 4GB
>       instances: 2
> ```

When the same MTA is deployed in combination with the above MTA extension descriptor, using the command `cf deploy <mtar> -e prod.mtaext`, the following steps are performed:

-   Validates the deployment descriptor and the extension descriptor against the MTA specification version **3.1**
-   Extends the deployment descriptor with an extension descriptor with ID `sample.app.prod` and merges the result:
    -   Overwrites the value of the parameter `memory`. It becomes equals to 4GB
    -   Adds a new parameter `instances` that equals to 2

-   …...
-   Creates a Cloud Foundry application which runs on 2 instances with 4GB memory each

In this scenario, the descriptor chain will consist of two descriptors. They will be arranged in this order: `sample.app` followed by `sample.app.prod`.

The following is an example of a second extension descriptor that builds upon the extension descriptor from the previous example:

> ### Example:  
> ```
> ----largemtaext-----
> _schema-version: '3.1'
> ID: sample.app.large
> extends: sample.app.prod
>  
> modules:
>   - name: my-app
>     parameter:
>       instances: 5
>       disk-quota: 10GB
> ```

When you deploy the same MTA in combination with the two MTA extension descriptors, using the command `cf deploy <mtar> -e prod.mtaext,large.mtaext`, the following steps are performed:

-   Validates the deployment descriptor and the extension descriptors against the MTA specification version **3.1**
-   Extends the deployment descriptor with an extension descriptor with ID `sample.app.prod` and merges the result:
    -   Overwrites the value of the parameter `memory`. It becomes equals to 4GB
    -   Adds a new parameter `instances` that equals to 2

-   Extends the merged descriptor with an extension descriptor with ID `sample.app.large` and merges the result:
    -   Overwrites the value of the parameter `instances`. It becomes equals to 5
    -   Adds a new parameter `disk-quota` that equals to 10GB


-   …
-   Creates a Cloud Foundry application, which runs on 5 instances, each with 4GB of memory and 10GB of disk space

In this scenario, the descriptor chain will consist of three descriptors: `sample.app`, followed by `sample.app.prod`, and then `sample.app.large`.

Extension descriptors can be used to add or override all data types of parameters and properties, following the specified rules.

-   Simple data types, such as Boolean, integer and String, are overwritten directly

-   Maps \(objects\) are overwritten and merged in depth

```
----MTA Deployment descriptor-----
ID: sample.postgre
 
resources:
  - name: my-postgre
    type: org.cloudfoundry.managed-service
    parameters:
      service-plan: standard
      service: postgresql-db
      config:
        memory: 4
        storage: 200
```

```
----prod-postgre.mtaext-----
ID: sample.postgre.dev
extends: sample.postgre
 
resources:
  - name: my-postgre
    parameters:
      config:
        storage: 10
```

When using a combination of the MTA deployment descriptor and MTA extension descriptor, the MTA deployment will result in the creation of a service instance with the service offering `postgresql-db`, plan **standard**, running on 4GB memory, and 10GB storage. This example demonstrates how the parameter `config`, a YAML map \(JSON Object\), is processed. The value from the extension descriptor is merged with the value from the deployment descriptor while retaining the element `memory`. Without using the extension descriptor, the result of the MTA deployment would be a Postgre service instance with 4GB memory and 200GB storage.

Note that lists \(arrays\) are overwritten by replacing all elements. This means that if you want to preserve any of the elements from the MTA deployment descriptor you need to define them again in the extension descriptor.

```
----MTA Deployment descriptor-----
ID: sample.app
 
modules:
  - name: my-app
    type: application
    properties:
      my-list: [1,2]
```

```
----app-list.mtaext-----
ID: sample.app.ext
extends: sample.app
 
modules:
  - name: my-app
    type: application
    properties:
      my-list: [2,3]
```

When you use a combination of the MTA deployment descriptor and an MTA extension descriptor, the resulting MTA deployment will create an application with the environment variable `my-list` set to \[2,3\]. This example demonstrates how the parameter `my-list`, which is a YAML list \(JSON Array\), is processed. The value from the extension descriptor completely overwrites the value from the deployment descriptor without retaining element “1”. If the extension descriptor is not used, the environment variable `my-list` would be \[1,2\].

In some cases, there are operation-level parameters \(command-line arguments\) that take the highest priority over all descriptors. See [Application-Specific Timeouts](applications-0540211.md#loio05402110821742479725338cc8d7fe8c__section_qlj_kky_ncc).



**What is possible to do with an extension descriptor?**

You can do the following using an extension descriptor:

-   Add new data in properties and parameters on module level, resource level, `provides` and `requires` section level

-   Overwrite existing data \(in depth\) in modules, resources, parameters, properties, `provides` and `requires` sections. This depends on the parameter or property metadata `overwritable`. See [Metadata for Properties and Parameters](metadata-for-properties-and-parameters-fca2ced.md).

-   As of schema version 3.xx, by default parameters and properties are overwritable and optional. If you want to make a certain parameter or property non-overwritable or required, you need to add specific metadata. See [Metadata for Properties and Parameters](metadata-for-properties-and-parameters-fca2ced.md).

You cannot use an extension descriptor to:

-   Add new entities such as modules or resources
-   Change module or resource type
-   Alter read-only \(system\) parameters
-   Add new provided or required dependencies
-   Change the processing order of modules and resources with `deployed-after` and `processed-after` parameters

**Related Information**  


[Defining MTA Deployment Descriptors for the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/ef90452321f84b43af8d14d4012aefe0.html "") :arrow_upper_right:

[Defining Multitarget Application Archives](defining-multitarget-application-archives-33a0e0e.md "You package the MTA deployment descriptor and module binaries in an MTA archive. You can manually do so as described below, or alternatively use the Cloud MTA Build tool.")

[MTA Module Types, Resource Types, and Parameters for Applications in the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/f1caa871360c40e7be7ce4264ab9c336.html "") :arrow_upper_right:

[The Multitarget Application Model v.2](https://help.sap.com/doc/multitarget-application-modelv2/Cloud/en-US/The%20Multitarget%20Application%20Model.pdf)

[The Multitarget Application Model v.3](https://help.sap.com/doc/multitarget-application-modelv3/Cloud/en-US/The%20Multitarget%20Application%20M%D0%BEdel.pdf)

