<!-- loioa4a4eb8c6d1045e5bd34d92a72b3cb36 -->

# OData Request: Update Entity

You want to execute an OData request to update an entity using the Client Proxy.



<a name="loioa4a4eb8c6d1045e5bd34d92a72b3cb36__section_gmk_p5w_5tb"/>

## OData Specification



### OData V2

See also: [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata)

Entities are instances of Entity Types \(for example, Customer or Employee\) which are richly structured records with a key. The structure of an Entity Type is provided by its Properties. An entity key is formed from a subset of the properties of the Entity Type. The key \(for example, CustomerId or EmployeeId\) is a fundamental concept to uniquely identify and persist entity instances and to allow entity instances to participate in relationships or associations. Entities are grouped in Entity Sets; for example, the EntitySet Customers is a set of Customer instances.

An UpdateEntity Request is used by a client to update an existing AtomPub Entry Resource, as specified in [RFC5023](https://www.rfc-editor.org/rfc/rfc5023.txt), that maps to an EntityType instance in the abstract data model.



### OData V4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html)

Entities are instances of entity types \(e.g. Customer, Employee, etc.\).Entity types are named structured types with a key. They define the named properties and relationships of an entity. Entity types may derive by single inheritance from other entity types.The key of an entity type is formed from a subset of the primitive properties \(e.g. CustomerId, OrderId, LineId, etc.\) of the entity type.

To update an individual entity, the client makes a PATCH or PUT request to a URL that identifies the entity. Services MAY restrict updates only to requests addressing the edit URL of the entity.



<a name="loioa4a4eb8c6d1045e5bd34d92a72b3cb36__section_p32_cvw_5tb"/>

## Example Requests



### V4

Update the employee with id ‘007’ of entity set “Employees

```
PATCH /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees(‘007’)
```

```

With request body

{ 
  "Car" : "Aston Martin DB5" 
}
```



### V2

Update the employee with id ‘007’ of entity set “Employees”:

```
PUT /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Employees(‘007’)
```

```

With request body

{ "Id" : "007",
  "Name" : "James Bond",
  "Gun" : "Walther PPK",
  "Car" : "Aston Martin DB5" 
}
```



<a name="loioa4a4eb8c6d1045e5bd34d92a72b3cb36__section_udg_xvw_5tb"/>

## How-To



### Overview

> ### Note:  
> As the coding itself is independent of the OData version, we will just present one general example on how to create an UPDATE request on an entity.

Starting point for a PUT/PATCH request on an entity is the Client Proxy instance. There, it is possible to create an entity resource based on an entity list resource, which can then be used to create an update request.

Executing the update request finally provides the update response, which can return the business data of the UPDATE entity request.



### Example

You want to update the employee with key “id = ‘007’” of the V4 entity set ‘Employees’:

```
PATCH /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees(‘007’)
```

```
With request body

{ 
	"Age" : 38, 
	"IsManager" : true, 
	"Status" : "Available" 
}
```

```

  TYPES: BEGIN OF tys_patch_data,
           types:     BEGIN OF tys_patch_data,
           age        TYPE i,
           is_manager TYPE abap_bool,
           status     TYPE string,
         END OF tys_patch_data.


  DATA: lo_client_proxy    TYPE REF TO /iwbep/if_cp_client_proxy,
        lo_update_request  TYPE REF TO /iwbep/if_cp_request_update,
        lo_update_response TYPE REF TO /iwbep/if_cp_response_update,
        lo_entity_resource TYPE REF TO /iwbep/if_cp_resource_entity,
        ls_patch_data      TYPE tys_patch_data,
        ls_employee        TYPE /iwbep/s_v4_tea_employee.


  lo_entity_resource = lo_client_proxy->create_resource_for_entity_set( 'EMPLOYEES')->navigate_with_key(value /iwbep/if_v4_tea_busi_types=>ty_s_employee_key( id = ‘007’) ).

  lo_update_request = lo_entity_resource->create_request_for_update( /iwbep/if_cp_request_update=>gcs_update_semantic-patch ).

  ls_patch_data = VALUE #( age = 38
                           is_manager = abap_true
                           status = ‘Available’ ).


  lo_update_request->set_business_data( is_business_data = ls_patch_data 
                                        it_provided_property = VALUE #( ( |AGE| )
                                                                        ( |IS_MANAGER| )
                                                                        ( |STATUS| ) ).

  lo_update_request->set_if_match( ‘1234’ ).
  lo_update_response = lo_update_request->execute( ).
  lo_update_response->get_business_data( IMPORTING es_business_data = ls_employee ).

```



### Step-by-step

**Step 1:** Creation of the entity resource for the employee with the key “Id=‘007’” of entity set ‘Employees’ \(with **internal** name ‘EMPLOYEES’\). Type “ty\_s\_employee\_key” in interface /iwbep/if\_v4\_tea\_busi\_types” is a structure containing the key property “id”:

```

  DATA: lo_client_proxy    TYPE REF TO /iwbep/if_cp_client_proxy,
        lo_entity_resource TYPE REF TO /iwbep/if_cp_resource_entity.

  lo_entity_resource = lo_client_proxy->create_resource_for_entity_set( 'EMPLOYEES')->navigate_with_key(value /iwbep/if_v4_tea_busi_types=>ty_s_employee_key( id = ‘007’) ).
```

**Step 2:** Now you create the update request instance on the entity resource. For this, you need to provide the desired semantic, which can either be PATCH or PUT. PUT creates a full new resource representation. This means that if some attributes are not provided, those should be removed \(i.e. set to null\) or set to their default value. PATCH is like PUT in that it updates a resource, but unlike PUT, it applies a delta rather than replacing the entire resource. The PATCH payload is of a different content-type than the entity that it is modifying. Instead of being a full resource, it is a resource that describes modifications to be made to a resource.

In our example, we use PATCH semantic. You can use the constants in structure gcs\_update\_semantic of interface /iwbep/if\_cp\_request\_update as input:

```

  DATA: lo_update_request  TYPE REF TO /iwbep/if_cp_request_update,
        lo_entity_resource TYPE REF TO /iwbep/if_cp_resource_entity.

  lo_update_request = lo_entity_resource->create_request_for_update( /iwbep/if_cp_request_update=>gcs_update_semantic-patch ). 
```

**Step 3:** You set the business \(i.e. update\) data for your update request. In our example, we want to update the three properties “Age”, “Status” and “IsManager” \(with **internal** names “AGE”, “STATUS” and “IS\_MANAGER”\). We define the new values and set the business data into the update request:

```

  TYPES: BEGIN OF tys_patch_data,
           age        TYPE i,
           is_manager TYPE abap_bool,
           status     TYPE string,
         END OF tys_patch_data.


  DATA: lo_update_request TYPE REF TO /iwbep/if_cp_request_update,
        ls_patch_data     TYPE tys_patch_data.


  ls_patch_data = VALUE #( age = 38
                           is_manager = abap_true
                           status = ‘Available’ ).


  lo_update_request->set_business_data( is_business_data = ls_patch_data
                                        it_provided_property = VALUE #( ( |AGE| )
                                                                        ( |IS_MANAGER| )
                                                                        ( |STATUS| ) ).
```

> ### Note:  
> Providing the provided properties when calling SET\_BUSINESS\_DATA is mandatory for a PATCH request.

**Step 4:** You set the If-Match header to provide an \(weak\) ETag \(if needed for this request\). If the corresponding request header would e.g. be if-match: W/"1234", the needed input for SET\_IF\_MATCH would be ‘1234’:

```

  DATA: lo_update_request TYPE REF TO /iwbep/if_cp_request_update.
 
  lo_update_request->set_if_match( ‘1234’ ).
```

**Step 5:** You execute the update request and gain the update response instance:

```

  DATA: lo_update_request  TYPE REF TO /iwbep/if_cp_request_update,
        lo_update_response TYPE REF TO /iwbep/if_cp_response_update.

  lo_update_response = lo_update_request->execute( ).
```

**Step 6:** You fetch the business data from the response object:

```

  DATA: lo_update_response TYPE REF TO /iwbep/if_cp_response_update,
        ls_employee        TYPE /iwbep/s_v4_tea_employee.

  lo_update_response->get_business_data( IMPORTING es_business_data = ls_employee ).
```

> ### Note:  
> -   When using the V4 local client proxy, the business data received from the \(local consumption\) response will not be re-converted for outbound processing.

