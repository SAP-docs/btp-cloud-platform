<!-- loio6ef40dfc2ef14bb08c28cd53b4de4c0b -->

# Services

If you want to create a service in the Cloud Foundry environment using the SAP Cloud Deployment service, you must define an MTA resource first. These resources can have different types and parameters which modify their behavior. There is a predefined set of supported resource types, that in most cases represents a certain combination of service offering and plan. See [Predefined MTA Resource Types](resources-9e34487.md#loio9e34487b1a8643fb9a93ae6c4894f015__section_predefinedMTAResourceTypes).

> ### Sample Code:  
> ```
> resources:
>   - name: my-xsuaa-service
>     type: com.sap.xs.uaa
> ```

The result will be a service instance called `my-xsuaa-service` with service offering `xsuaa` and service plan `application`.

For a more flexible approach, see [Generic MTA Resource Types](resources-9e34487.md#loio9e34487b1a8643fb9a93ae6c4894f015__section_mtaResourceTypes) and [Resource-Specific Parameters](resources-9e34487.md#loio9e34487b1a8643fb9a93ae6c4894f015__section_resourceSpecificParameters).

> ### Note:  
> In most of cases, MTA resources represent a Cloud Foundry service, but there are cases where they represent a different platform entity, for example a service key. They can even serve only to a group of configurations. See [Resources](resources-9e34487.md) for more information.

