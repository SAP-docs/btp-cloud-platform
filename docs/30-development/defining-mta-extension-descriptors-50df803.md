<!-- loio50df803465324d36851c79fd07e8972c -->

# Defining MTA Extension Descriptors

The Multitarget Application \(МТА\) extension descriptor is a YAML file that contains data complementary to the deployment descriptor. The data can be environment or deployment specific, for example, credentials depending on the user who performs the deployment. The MTA extension descriptor is a YAML file that has a similar structure to the deployment descriptor, by following the Multitarget Application Model structure with several limitations and differences. Normally, extension descriptor extends deployment descriptor but it is possible to extends other extension descriptor, making extension descriptors chain. It can add or overwrite existing data if necessary.

Several extension descriptors can be additionally used after the initial deployment.

> ### Note:  
> The format and available options within the extension descriptor may change with newer versions of the MTA specification. You must always specify the schema version option when defining an extension descriptor to inform the SAP BTP which MTA specification version should be used. Furthermore, the schema version used within the extension descriptor and the deployment descriptor should always be same.

In the examples below, we have a deployment descriptor, which has already been defined, and several extension descriptors.

> ### Note:  
> Each extension descriptor is defined in a separate file with an extension `.mtaext`.

Deployment descriptor:

> ### Example:  
> ```
> _schema-version: '3.1'
> parameters:
>   hcp-deployer-version: '1.0'
> ID: com.example.extension
> version: 0.1.0
> 
> resources:
>   - name: data-storage
>     properties:
>       existing-data: value
> ```

The example above instructs SAP BTP to:

-   Validate the extension descriptor against the MTA specification version `3.1`
-   Extend the `com.example.extension` deployment descriptor

The following is a basic example of an extension descriptor that adds data and overwrites data to another extension descriptor:

> ### Example:  
> ```
> _schema-version: '3.1'
> ID: com.example.extension.first
> extends: com.example.extension
> 
> resources:
>   - name: data-storage
>     properties:
>       existing-data: new-value
>       non-existing-data: value
> ```

The above instructs SAP BTP to:

-   Extend the deployment descriptor by its ID `com.example.extension`
-   Validate the extension descriptor against the MTA specification version 3.1
-   Overwrite the data for the `existing-data` property
-   Add a new data called `non-existing-data` to the `data-storage` properties

The following is an example of another extension descriptor that extends the extension descriptor from the previous example:

> ### Example:  
> ```
> _schema-version: '3.1'
> ID: com.example.extension.second
> extends: com.example.extension.first
> 
> resources:
>   - name: data-storage
>     properties:
>       second-non-existing-data: value
> ```

The example above instructs the SAP BTP to:

-   Extend the first extension descriptor by its ID
-   Add a new data called `second-non-existing-data` to the `data-storage` properties

-   The examples above are incomplete. To deploy a solution, you have to create a deployment descriptor and an MTA archive.



**What is possible to do with an extension descriptor?**

You can do the following using an extension descriptor:

-   Add a new data in properties and parameters on module level, resource level, provided section level and required section level

-   Overwrite an existing data \(in depth\) in modules, resources, parameters, properties, provides, requires sections. This depends on the parameter or property metadata overwritable. See section 9. Metadata for Properties and Parameters

-   As of schema version 3.xx, by default parameters and properties are overwritable and optional. If you want to make a certain parameter or property non-overwritable or required, you need to add specific metadata. See [Metadata for Properties and Parameters](metadata-for-properties-and-parameters-fca2ced.md).

You cannot use an extension descriptor to:

-   Add new entities such as modules or resources
-   Change module or resource type
-   Alter read-only \(system\) parameters

**Related Information**  


[Defining MTA Deployment Descriptors for the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/ef90452321f84b43af8d14d4012aefe0.html "") :arrow_upper_right:

[Defining Multitarget Application Archives](defining-multitarget-application-archives-33a0e0e.md "You package the MTA deployment descriptor and module binaries in an MTA archive. You can manually do so as described below, or alternatively use the Cloud MTA Build tool.")

[MTA Module Types, Resource Types, and Parameters for Applications in the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/f1caa871360c40e7be7ce4264ab9c336.html "") :arrow_upper_right:

[The Multitarget Application Model v.2](http://go.sap.com/documents/2016/06/e2f618e4-757c-0010-82c7-eda71af511fa.html)

[The Multitarget Application Model v.3](https://www.sap.com/documents/2021/09/66d96898-fa7d-0010-bca6-c68f7e60039b.html)

