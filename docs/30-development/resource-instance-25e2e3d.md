<!-- loio25e2e3db141d446d900c94285d2ef56e -->

# Resource Instance

A resource instance represents a resource that is shared between applications and identified using URLs and defined in the data model.



<a name="loio25e2e3db141d446d900c94285d2ef56e__section_b4c_czm_4tb"/>

## Overview

In OData Version 4, a resource is anything in the model that can be addressed \(an entity set, entity, property, or operation\).

The OData instance creates REST-based data services that allows resources \(identified using URLs and defined in an Entity Data Model\), to be published and edited by web clients with simple HTTP messages.

For a standard OData request, you must preovide a corresponding URL that points to a resource \(for example, `entity_list(id=‘1‘)` points to a specific resource:

> ### Sample Code:  
> ```
> /sap/opu/odata/sap/srv/entity_list(id=‘1‘)/entity
> ```

> ### Note:  
> The resources aren't OData protocol-specific \(Version 2 or Version 4\).

In the Client Proxy, you don't need to provide the URI. But you need to create an instance of the resource you want to access \(for example, a function or a single entity\).



<a name="loio25e2e3db141d446d900c94285d2ef56e__section_osh_dzm_4tb"/>

## Creating an Instance

Depending on the resource type, the instance creation can vary. Some resources \(for example, an entity set or action resources\) are created at the [Client Proxy Instance Types](client-proxy-instance-types-079517f.md). Other resources are created on another resource instance \(for example, an entity resource, created on the entity set resource\). You can't call an entity resource without providing the corresponding entity set resource.



### Examples

-   `GET/sap/opu/odata/sap/srv/teams` The target resource is an entity set \(***teams***\). The resource instance is created at the Client Proxy instance. For more information, see [OData Request: Read Entity List](odata-request-read-entity-list-b810028.md).

-   `GET /sap/opu/odata/sap/srv/order(customer=’Jane Doe’)` The target resource is a single entity \(Jane Doe\), so the resource instance is created at the parent resource instance \(entity set order\).




### Resource Types

These resource types are available to users:

-   `/IWBEP/IF_CP_RESOURCE_ACTION`: Describes the resource of an **action** that is created on the Client Proxy instance \(for action imports\) or on an entity \(set\) resource \(for bound actions\).

-   `/IWBEP/IF_CP_RESOURCE_ENTITY`: Describes the resource of a **single** entity that is created on an entity \(set\) resource.
-   `/IWBEP/IF_CP_RESOURCE_ENTITY01`: Describes the resource of an **optional** entity \(the target entity of a zero-to-one navigation\) that is created on an entity resource.
-   `/IWBEP/IF_CP_RESOURCE_FUNCTION`: Describes the resource of a **function** that is created on the Client Proxy instance \(for function imports\) or on an entity \(set\) resource \(for bound functions\).

-   `/IWBEP/IF_CP_RESOURCE_LIST`: Describes the resource of an **entity set** that is created on the Client Proxy instance or an entity resource.



<a name="loio25e2e3db141d446d900c94285d2ef56e__section_us5_dzm_4tb"/>

## Functionality

Resource instances are used to create requests \(for example, an update request on an entity\) or other resource instances \(for example, an action resource from an entity list resource\). The options that a resource instance offers depends on the different resource types.



<a name="loio25e2e3db141d446d900c94285d2ef56e__section_byw_2zm_4tb"/>

## Example

For examples of how to create and work with resources see [Actions and Functions](actions-and-functions-cea94cf.md) and [OData Request: Using Navigation](odata-request-using-navigation-57f2139.md).

**Related Information**  


[OData Request: Read Entity List](odata-request-read-entity-list-b810028.md "Create an OData request to read an entity list (entity collection) in the Client Proxy instance.")

