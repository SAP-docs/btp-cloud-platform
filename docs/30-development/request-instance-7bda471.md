<!-- loio7bda4718f8b84ec4ae04396822c9105a -->

# Request Instance

A request instance describes the action you want to take on a resource.



<a name="loio7bda4718f8b84ec4ae04396822c9105a__section_b4c_czm_4tb"/>

## Overview

You can read or modify an OData [Resource Instance](resource-instance-25e2e3d.md) by sending an OData request on this resource. This example reads all entities for the entity set “***teams***”:

> ### Sample Code:  
> ```
> GET /sap/opu/odata/sap/srv/teams
> ```

This example deletes the “***order***” entity of customer "***Jane Doe***":

> ### Sample Code:  
> ```
> DELETE /sap/opu/odata/sap/srv/order(customer=’Jane Doe’)
> ```

A request instance describes the actual operation you want to perform on the corresponding resource. It includes all relevant information \(for example. the request body data for updating an entity\) for the operation execution.

> ### Note:  
> The requests are not OData protocol-specific \(Version 2 or. Version 4\).



<a name="loio7bda4718f8b84ec4ae04396822c9105a__section_osh_dzm_4tb"/>

## Creating an Instance

Request instances are created on the resource instance the request will act on \(for example, a request to update an entity is created on the corresponding entity resource. The only exceptions are `$batch/changeset requests` \(these can contain requests acting on different resources\), and delta link requests, that are both created on the Proxy Instance



### Request Examples

-   `/IWBEP/IF_CP_REQUEST_ACTION`: A request to execute an **ACTION** \(using action import or as a bound action.

-   `/IWBEP/IF_CP_REQUEST_BATCH`: A `$batch` request. It can be used to add other requests \(for example. a ***DELETE*** request\) and execute them together as part of a `$batch`.
-   `/IWBEP/IF_CP_REQUEST_CHANGESET`: A request for a ***changeset***. This request can be used to add other requests \(for example, `CREATE` request\) into one changeset. The changeset request can only be executed as part of a `$batch` request \(for example, it must be added to a ***$batch*** request before executing the request\).
-   `/IWBEP/IF_CP_REQUEST_CREATE`: A request to ***CREATE*** an entity.
-   `/IWBEP/IF_CP_REQUEST_DELETE` : A request to ***DELETE*** an entity
-   `/IWBEP/IF_CP_REQUEST_FUNCTION`: A request to execute a **FUNCTION** \(using function import or as bound function.
-   `/IWBEP/IF_CP_REQUEST_READ`: A request to ***READ*** an entity.
-   `/IWBEP/IF_CP_REQUEST_READ_01`: A request to ***READ*** an entity WITH a zero-to-one navigation.
-   `/IWBEP/IF_CP_REQUEST_READ_DLTA`: A request to ***READ*** the delta of a list of entities
-   `/IWBEP/IF_CP_REQUEST_READ_LIST`: A request to ***READ*** a list of entities.
-   `/IWBEP/IF_CP_REQUEST_UPDATE`: A request to ***UPDATE*** an entity.
-   `/IWBEP/IF_CP_REQUEST_UPDATE_L`: A request to ***UPDATE*** a list of entities.



<a name="loio7bda4718f8b84ec4ae04396822c9105a__section_us5_dzm_4tb"/>

## Functionality

Request instances create an OData request and a corresponding [Response Instance](response-instance-de1b8ed.md). The options a request instance offers depend on the different request types.



<a name="loio7bda4718f8b84ec4ae04396822c9105a__section_byw_2zm_4tb"/>

## Example

For examples of how to create and work with requests, see the [OData Requests](odata-requests-bbaf7a4.md).

