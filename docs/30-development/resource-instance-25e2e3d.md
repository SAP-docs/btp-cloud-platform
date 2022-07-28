<!-- loio25e2e3db141d446d900c94285d2ef56e -->

# Resource Instance

In this chapter, we'll learn the meaning of a Client Proxy resource as well as how to create and use a Client Proxy resource instance



<a name="loio25e2e3db141d446d900c94285d2ef56e__section_b4c_czm_4tb"/>

## Overview

According to the OData V4 Spec, an OData resource is anything in the model that can be addressed \(an entity set, entity, property, or operation\).

It further states:

“The Open Data Protocol \(OData\) enables the creation of REST-based data services, which allow resources, identified using Uniform Resource Locators \(URLs\) and defined in an Entity Data Model \(EDM\), to be published and edited by web clients using simple HTTP messages.”

Therefore, for a standard OData request, a corresponding URL pointing to a resource must be provided, like in the following example `entity_list(id=‘1‘)` points to a specific resource:

> ### Sample Code:  
> ```
>                (---------Ressource-------)
> /sap/opu/odata/sap/srv/entity_list(id=‘1‘)/entity
> ```

> ### Note:  
> The resources aren't OData protocol \(V2 or V4\) specific.

Using the Client Proxy, it'sn't necessary to provide the URL yourself. You must, however, create an instance of the resource you want to access \(e.g. a function or a single entity\).



<a name="loio25e2e3db141d446d900c94285d2ef56e__section_osh_dzm_4tb"/>

## Creating an Instance

The actual creation of the instance depends on the resource kind. Some resources \(like, e.g., entity set or action resources\) are created at the [Client Proxy Instance](client-proxy-instance-079517f.md), others are created on another resource instance \(e.g. an entity resource, which is created on the entity set resource\). This is similar to the corresponding URL, where it's also not possible to call an entity resource without providing the corresponding entity set resource.



### Examples

-   `GET/sap/opu/odata/sap/srv/teams` =\> The target resource is an entity set \(teams\), so the resource instance is created at the Client Proxy instance. For more information, see [OData Request: Read Entity List](odata-request-read-entity-list-b810028.md).

-   `GET /sap/opu/odata/sap/srv/order(customer=’Jane Doe’)` =\> The target resource is a single entity \(Jane Doe\), so the resource instance is created at the parent resource instance \(entity set order\). For more information, see [OData Request: Read Entity](odata-request-read-entity-9d7dde4.md).




### Resource Types

The following resource types are available to users.

-   `/IWBEP/IF_CP_RESOURCE_ACTION`: Describing the resource of an action; created on the Client Proxy instance \(for action imports\) or on an entity \(set\) resource \(for bound actions\)

    ,

-   `/IWBEP/IF_CP_RESOURCE_ENTITY`: Describing the resource of a single entity; created on an entity \(set\) resource.
-   `/IWBEP/IF_CP_RESOURCE_ENTITY01`: Describing the resource of an optional entity \(that is, the target entity of a zero-to-one navigation\); created on an entity resource.
-   `/IWBEP/IF_CP_RESOURCE_FUNCTION`: Describing the resource of a function; created on the Client Proxy instance \(for function imports\) or on an entity \(set\) resource \(for bound functions\).

-   `/IWBEP/IF_CP_RESOURCE_LIST`: Describing the resource of an entity set; created on the Client Proxy instance or an entity resource.



<a name="loio25e2e3db141d446d900c94285d2ef56e__section_us5_dzm_4tb"/>

## Functionality

The main functionality of resource instances is to create requests \(e.g. an update request on an entity\) or other resource instances \(e.g. an action resource from an entity list resource\). However, the options that a resource instance offer depends strongly on the different resource kinds; kindly check the example section or consult the provided ABAP doc to get an overview over the different functionalities.



<a name="loio25e2e3db141d446d900c94285d2ef56e__section_byw_2zm_4tb"/>

## Example

Examples on how to create and work with resources are given in the corresponding How-To section .

