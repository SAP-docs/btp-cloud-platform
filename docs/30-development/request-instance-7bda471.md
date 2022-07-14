<!-- loio7bda4718f8b84ec4ae04396822c9105a -->

# Request Instance

In this chapter, we will learn the meaning of a Client Proxy request as well as how to create and use a Client Proxy request instance.



<a name="loio7bda4718f8b84ec4ae04396822c9105a__section_b4c_czm_4tb"/>

## Overview

An OData [Resource Instance](resource-instance-25e2e3d.md) can be read and/or modified by sending an OData request on this resource. The following example reads all entities of the entity set **“teams”:**

> ### Sample Code:  
> ```
> GET /sap/opu/odata/sap/srv/teams
> ```

The following example deletes the “order” entity of customer **Jane Doe**:

> ### Sample Code:  
> ```
> DELETE /sap/opu/odata/sap/srv/order(customer=’Jane Doe’)
> ```

When using the Client Proxy, a request instance describes the actual operation you want to perform on the corresponding resource and includes all relevant information \(e.g. the request body data for updating an entity\) for the operation execution.

> ### Note:  
> The requests are not OData protocol \(V2 or. V4\) specific.



<a name="loio7bda4718f8b84ec4ae04396822c9105a__section_osh_dzm_4tb"/>

## Creating an Instance

Request instances are always created on the resource instance the request is supposed to act on, i.e. a request to update an entity is created on the corresponding entity resource. The only exception from this rule are `$batch/changeset requests` \(as these may contain requests acting on different resources\), and delta link requests \(for convenience\), which are both created on the [Client Proxy Instance](client-proxy-instance-079517f.md).



### Request Types

-   `/IWBEP/IF_CP_REQUEST_ACTION`: A request to execute an ACTION \(via action import or as a bound action.

-   `/IWBEP/IF_CP_REQUEST_BATCH`: A `$batch`request. It can be used to add other requests \(e.g. a DELETE request\) and execute them together \(as part of a `$batch`\).
-   `/IWBEP/IF_CP_REQUEST_CHANGESET`: A request for a changeset. This request can be used to add other requests \(e.g. a `CREATE` request\) into one changeset. The changeset request can only be executed as part of a `$batch` request \(i.e. must be added to a `$batch` request before execution\).
-   `/IWBEP/IF_CP_REQUEST_CREATE`: A request to `CREATE` an entity.
-   `/IWBEP/IF_CP_REQUEST_DELETE` : A request to DELETE an entity
-   `/IWBEP/IF_CP_REQUEST_FUNCTION`: A request to execute a FUNCTION \(either via function import or as bound function.
-   `/IWBEP/IF_CP_REQUEST_READ`: A request to `READ` an entity.
-   `/IWBEP/IF_CP_REQUEST_READ_01`: A request to `READ` an entity via a zero-to-one navigation.
-   `/IWBEP/IF_CP_REQUEST_READ_DLTA`: A request to `READ`the delta of a list of entities
-   `/IWBEP/IF_CP_REQUEST_READ_LIST`: A request to `READ` a list of entities.
-   `/IWBEP/IF_CP_REQUEST_UPDATE`: A request to `UPDATE` an entity.
-   `/IWBEP/IF_CP_REQUEST_UPDATE_L`: A request to `UPDATE` a list of entities.



<a name="loio7bda4718f8b84ec4ae04396822c9105a__section_us5_dzm_4tb"/>

## Functionality

The main functionality of request instances is to execute an OData request and create a corresponding [Response Instance](response-instance-de1b8ed.md). However, the options a request instance offers depend strongly on the different request kinds. Kindly check the example section or consult the provided ABAP doc to get an overview over the different functionalities.



<a name="loio7bda4718f8b84ec4ae04396822c9105a__section_byw_2zm_4tb"/>

## Example

Examples on how to create and work with requests are given in the corresponding How-To section \[LINK\].

