<!-- loio8ad7ee8d7a4f4816a00008afdc4a60db -->

# OData Request: Delete Entity

You want to execute an OData request to delete an entity using the Client Proxy.



<a name="loio8ad7ee8d7a4f4816a00008afdc4a60db__section_yn3_clg_rtb"/>

## OData Specification



### OData V2

See also: [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata)

Entities are instances of Entity Types \(for example, Customer or Employee\) which are richly structured records with a key. The structure of an Entity Type is provided by its Properties. An entity key is formed from a subset of the properties of the Entity Type. The key \(for example, CustomerId or EmployeeId\) is a fundamental concept to uniquely identify and persist entity instances and to allow entity instances to participate in relationships or associations. Entities are grouped in Entity Sets; for example, the EntitySet Customers is a set of Customer instances.

The purpose of the DeleteEntity Request is to enable an EntityType instance to be deleted from a data service. The base rules and semantics of this request type are defined by AtomPub, as specified in [RFC5023](https://www.rfc-editor.org/rfc/rfc5023.txt) section 9.4 -- Deleting Resources with DELETE.



### OData V4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html)

Entities are instances of entity types \(e.g. Customer, Employee, etc.\). Entity types are named structured types with a key. They define the named properties and relationships of an entity. Entity types may derive by single inheritance from other entity types. The key of an entity type is formed from a subset of the primitive properties \(e.g. CustomerId, OrderId, LineId, etc.\) of the entity type.

To delete an individual entity, the client makes a DELETE request to a URL that identifies the entity. \(...\)

On successful completion of the delete, the response MUST \(...\) contain an empty body.



<a name="loio8ad7ee8d7a4f4816a00008afdc4a60db__section_y4j_34g_rtb"/>

## Example Requests



### V4

Delete the employee with id ‘007’ of entity set “Employees”

```
DELETE /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees(‘007’)
```



### V2

Delete the employee with id ‘007’ of entity set “Employees”

```
DELETE /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Employees(‘007’)
```



<a name="loio8ad7ee8d7a4f4816a00008afdc4a60db__section_ggm_r4g_rtb"/>

## How-To



### Overview

> ### Note:  
> As the coding itself is independent of the OData version, we will just present one general example on how to create a DELETE request on an entity.

Starting point for a DELETE request on an entity is the Client Proxy instance. There, it is possible to create an entity resource based on an entity list resource, which can then be used to create a delete request.



### Example

You want to delete the employee with key “id = ‘007’” of the V4 entity set ‘Employees’:

```
DELETE /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees(‘007’) with IF-MATCH header W/"MI6".
```

```

  DATA: lo_client_proxy    TYPE REF TO /iwbep/if_cp_client_proxy,
        lo_delete_request  TYPE REF TO /iwbep/if_cp_request_delete,
        lo_entity_resource TYPE REF TO /iwbep/if_cp_resource_entity.


  lo_entity_resource = lo_client_proxy->create_resource_for_entity_set( 'EMPLOYEES')->navigate_with_key(value /iwbep/if_v4_tea_busi_types=>ty_s_employee_key( id = ‘007’) ).
  lo_delete_request = lo_entity_resource->create_request_for_delete( ).
  lo_delete_request->set_if_match( ‘mi6’ ).
  lo_delete_request->execute( ).
  lo_delete_request->check_execution( ).
```



### Step-by-step

**Step 1:** Creation of the entity resource for the employee with the key “Id=‘007’” of entity set ‘Employees’ \(with **internal** name ‘EMPLOYEES’\). Type “ty\_s\_employee\_key” in interface /iwbep/if\_v4\_tea\_busi\_types” is a structure containing the key property “id”:

```

  DATA: lo_client_proxy    TYPE REF TO /iwbep/if_cp_client_proxy,
        lo_entity_resource TYPE REF TO /iwbep/if_cp_resource_entity.


  lo_entity_resource = lo_client_proxy->create_resource_for_entity_set( 'EMPLOYEES')->navigate_with_key(value /iwbep/if_v4_tea_busi_types=>ty_s_employee_key( id = ‘007’) ).
```

**Step 2:** Now you create the delete request instance. This is done on the entity resource:

```

  DATA: lo_delete_request  TYPE REF TO /iwbep/if_cp_request_delete,
        lo_entity_resource TYPE REF TO /iwbep/if_cp_resource_entity.

  lo_delete_request = lo_entity_resource->create_request_for_delete( ).
```

**Step 3:** You set the If-Match header to provide an \(weak\) ETag \(if needed for this request\). If the corresponding request header would e.g. be if-match: W/"MI6", the needed input for SET\_IF\_MATCH would be ‘MI6’:

```

  DATA: lo_delete_request TYPE REF TO /iwbep/if_cp_request_delete.

  lo_delete_request->set_if_match( ‘mi6’ ).
```

**Step 4:** You execute the delete request:

```

  DATA: lo_delete_request TYPE REF TO /iwbep/if_cp_request_delete.

  lo_delete_request->execute( ).
```

> ### Note:  
> A successful delete request does not have response data, so the EXECUTE method does not return a delete response object.

**Step 5:** You check if the execution was successful:

```

  DATA: lo_delete_request TYPE REF TO /iwbep/if_cp_request_delete.

  lo_delete_request->check_execution( ).
```

> ### Note:  
> Normally, any issue during request execution should raise an exception in method EXECUTE; this method call is therefore optional.

