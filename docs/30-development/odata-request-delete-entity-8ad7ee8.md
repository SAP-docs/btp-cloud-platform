<!-- loio8ad7ee8d7a4f4816a00008afdc4a60db -->

# OData Request: Delete Entity

Create an OData request to delete an entity in the Client Proxy instance.



<a name="loio8ad7ee8d7a4f4816a00008afdc4a60db__section_yn3_clg_rtb"/>

## OData Specification



### OData Version 2

See also: [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata).

The ***DeleteEntity Request*** enables an ***EntityType*** instance to be deleted from a data service. The base rules and semantics of this request type are defined by AtomPub, as specified in [RFC5023](https://www.rfc-editor.org/rfc/rfc5023.txt) section 9.4 -- Deleting Resources with ***DELETE***.



### OData Version 4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html).

To delete an individual entity, the client makes a ***DELETE*** request to a URL that identifies the entity.

When the delete is successfully completed, the response MUST be *<response code and name\>* and contain an empty body.



<a name="loio8ad7ee8d7a4f4816a00008afdc4a60db__section_y4j_34g_rtb"/>

## Example Requests



### Version 4

Delete the employee with id ‘***007***’ of entity set “***Employees***”

```
DELETE /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees(‘007’)
```



### Version 2

Delete the employee with id ‘***007***’ of entity set “***Employees***”

```
DELETE /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Employees(‘007’)
```



<a name="loio8ad7ee8d7a4f4816a00008afdc4a60db__section_ggm_r4g_rtb"/>

## Delete Entity Request



### Overview

> ### Note:  
> As the coding is independent of the OData version, we're presenting a general example on how to create a ***DELETE*** entity request.

The starting point for a ***DELETE*** entity request is the Client Proxy instance. You can create an entity resource based on an entity list resource, which you can use to create a delete request.



### Example

Delete the employee with key “id = ‘***007’***” of the Version 4 entity set ‘***Employees’***:

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



### Steps

**Step 1:** Create the entity resource for the employee with the key “Id=‘***007***’” of entity set ‘***Employees***’ \(with **internal** name ‘***EMPLOYEES***’\). Type “***ty\_s\_employee\_key***” in interface "***/iwbep/if\_v4\_tea\_busi\_types***” is a structure containing the key property “id”:

```

  DATA: lo_client_proxy    TYPE REF TO /iwbep/if_cp_client_proxy,
        lo_entity_resource TYPE REF TO /iwbep/if_cp_resource_entity.


  lo_entity_resource = lo_client_proxy->create_resource_for_entity_set( 'EMPLOYEES')->navigate_with_key(value /iwbep/if_v4_tea_busi_types=>ty_s_employee_key( id = ‘007’) ).
```

**Step 2:** Create the delete request instance on the entity resource:

```

  DATA: lo_delete_request  TYPE REF TO /iwbep/if_cp_request_delete,
        lo_entity_resource TYPE REF TO /iwbep/if_cp_resource_entity.

  lo_delete_request = lo_entity_resource->create_request_for_delete( ).
```

**Step 3:** Set the If-Match header to provide an ETag \(if needed for this request\). If the corresponding request header is, for example, ***if-match: W/"MI6"***, the required input for ***SET\_IF\_MATCH*** is ‘***MI6’***:

```

  DATA: lo_delete_request TYPE REF TO /iwbep/if_cp_request_delete.

  lo_delete_request->set_if_match( ‘mi6’ ).
```

**Step 4:** Run the delete request:

```

  DATA: lo_delete_request TYPE REF TO /iwbep/if_cp_request_delete.

  lo_delete_request->execute( ).
```

> ### Note:  
> A successful delete request doesn't have response data, which means that the ***EXECUTE*** method doesn't return a delete response object.

**Step 5:** Check if the execution was successful:

```

  DATA: lo_delete_request TYPE REF TO /iwbep/if_cp_request_delete.

  lo_delete_request->check_execution( ).
```

> ### Note:  
> Normally, any issues during the request execution raises an exception in method ***EXECUTE***. This method call is optional.

**Related Information**  


[OData Request Terms](odata-request-terms-a3b0e95.md "An overview of some OData Request terminology.")

