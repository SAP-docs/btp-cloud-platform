<!-- loio6ef40dfc2ef14bb08c28cd53b4de4c0b -->

# Services

If you want to create a service instance in the Cloud Foundry environment using the SAP Cloud Deployment service, you must define an MTA resource first. These resources can have different types and parameters which modify their behavior. There is a predefined set of supported resource types, that in most cases represents a certain combination of service offering and plan. See [Predefined MTA Resource Types](resources-9e34487.md#loio9e34487b1a8643fb9a93ae6c4894f015__section_predefinedMTAResourceTypes).

> ### Sample Code:  
> ```
> resources:
>   - name: my-xsuaa-service
>     type: com.sap.xs.uaa
> ```

The result will be a service instance called `my-xsuaa-service` with service offering `xsuaa` and service plan `application`.

For a more flexible approach, see [Generic MTA Resource Types](resources-9e34487.md#loio9e34487b1a8643fb9a93ae6c4894f015__section_mtaResourceTypes) and [Resource-Specific Parameters](resources-9e34487.md#loio9e34487b1a8643fb9a93ae6c4894f015__section_resourceSpecificParameters).

> ### Note:  
> In most cases, MTA resources represent a Cloud Foundry service, but there are cases where they represent a different platform entity, for example a service key. They can even serve only to a group of configurations. See [Resources](resources-9e34487.md) for more information.



<a name="loio6ef40dfc2ef14bb08c28cd53b4de4c0b__section_sgc_322_mfc"/>

## Service Plans

> ### Note:  
> This information applies only to service instances that are managed by service brokers.

A service plan defines a specific configuration of a service offered on SAP BTP. While the service itself provides the functionality \(e.g., database, messaging, etc.\), the service plan determines the level or variant of that functionality - such as free, standard, or enterprise editions.

Each service offered on the marketplace has one or more available service plans. Choosing the appropriate plan is essential for resource allocation, cost, and feature set.

When you create or update a service instance, you need to specify the desired service with the required `service-plan` parameter:

> ### Sample Code:  
> ```
> resources:
>   - name: my-database
>     type: org.cloudfoundry.managed-service
>     parameters:
>       service: hana
>       service-plan: hdi-shared
> ```



### Updating Service Plans

Updating service plans is, by default, **fail-safe** for those operations which result in a call to the service brokers. You can control this behavior by using the `fail-on-service-update` parameter.

Possible values for the parameter are:

-   **null** \(default value\): If the update triggers an asynchronous operation \(when the service brokers allow plan updates\), the deployment will not fail even if the operation fails.
-   **true**: If the update of the service plan fails \(even asynchronously\), the deployment will also fail.
-   **false**: The update becomes even more permissive - even if the initial call to update the service plan fails, the deployment will still continue.

> ### Example:  
> ```
> parameters:
>   fail-on-service-update:
>     plan: true
> ```

