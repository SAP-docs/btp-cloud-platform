<!-- loio56be82d78dc14e41b5935c878c72fec3 -->

# OData Request: Create Entity

You want to execute an OData request to create an entity using the Client Proxy.



<a name="loio56be82d78dc14e41b5935c878c72fec3__section_bcw_pb3_ptb"/>

## OData Specification



### OData V2

See also: [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata)

Entities are instances of Entity Types \(for example, Customer or Employee\) which are richly structured records with a key. The structure of an Entity Type is provided by its Properties. An entity key is formed from a subset of the properties of the Entity Type. The key \(for example, Customerid or EmployeeId\) is a fundamental concept to uniquely identify and persist entity instances and to allow entity instances to participate in relationships or associations. Entities are grouped in Entity Sets; for example, the EntitySet Customers is a set of Customer instances.

The purpose of the InsertEntity Request is to enable a new EntityType instance, potentially with new related entities, to be inserted into an EntitySet.



### OData V4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html)

Entities are instances of entity types \(e.g. Customer, Employee, etc.\).Entity types are named structured types with a key. They define the named properties and relationships of an entity. Entity types may derive by single inheritance from other entity types.The key of an entity type is formed from a subset of the primitive properties \(e.g. CustomerId, OrderId, LineId, etc.\) of the entity type.

To create an entity in a collection, the client sends a POST request to that collection's URL. The POST body MUST contain a single valid entity representation.



<a name="loio56be82d78dc14e41b5935c878c72fec3__section_ccv_zc3_ptb"/>

## Example Requests



### V4

Create the employee with id ‘007’ of entity set “Employees”

```
POST /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees
```

```


With request body

{ 
	"Id" : "007", 
	"Name" : "James Bond", 
	"Gun" : "Walther PPK", 
	"Car" : "Aston Martin DB5"
}
 
```



### V2

Create the employee with id ‘007’ of entity set “Employees”

```
POST /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Employees
```

```

With request body

{ 
	"Id" : "007", 
	"Name" : "James Bond", 
	"Gun" : "Walther PPK", 
	"Car" : "Aston Martin DB5"
}

```



<a name="loio56be82d78dc14e41b5935c878c72fec3__section_hpb_kv2_rtb"/>

## How-To



### Overview

> ### Note:  
> As the coding itself is independent of the OData version, we will just present one general example on how to create a CREATE request on an entity.

Starting point for a POST request on an entity list is the Client Proxy instance. There, it is possible to create an entity list resource, which can then be used to create a create request.

Executing the create request finally provides the create response instance, which can return the business data of the CREATE entity request.



### Example

You want to create the employee with key “id = ‘007’” of the V4 entity set ‘Employees’:

```
POST /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees
```

```


With request body

{ 
	"Id" : "007", 
	"Name" : "James Bond", 
	"Age" : 38, 
	"Entrydate" : "1962-10-05", 
	"ManagerId" : "001", 
	"RoomId" : "1", 
	"TeamId" : "TEAM_BRITANIA",
	"IsManager" : false, 
	"Status" : "Available" 
}

  TYPES: BEGIN OF tys_entity_data,
           Id         TYPE i,
           Name       TYPE string,
           age        TYPE i,
           entry_date TYPE dats,
           manager_id TYPE i,
           room_id    TYPE i,
           team_id    TYPE string,
           is_manager TYPE abap_bool,
           status     TYPE string,
         END OF tys_entity_data.

  DATA: lo_client_proxy         TYPE REF TO /iwbep/if_cp_client_proxy,
        lo_create_request       TYPE REF TO /iwbep/if_cp_request_create,
        lo_create_response      TYPE REF TO /iwbep/if_cp_response_create,
        lo_entity_list_resource TYPE REF TO /iwbep/if_cp_resource_list,
        ls_entity_data          TYPE tys_entity_data,
        ls_employee             TYPE /iwbep/s_v4_tea_employee.


  lo_entity_list_resource = lo_client_proxy->create_resource_for_entity_set( 'EMPLOYEES' ).
  lo_create_request = lo_entity_list_resource->create_request_for_create( ).
  ls_entity_data = VALUE #( id = 007
                            name = ‘James Bond’
                            age = 38
                            entry_date = ‘19621005’
                            manager_id = 001
                            room_id = 1
                            team_id = ‘team_britania’
                            is_manager = abap_false
                            status = ‘Available’     ).


  lo_create_request->set_business_data( is_business_data = ls_entity_data
                                        It_provided_property = VALUE #( ( |ID| )
                                                                        ( |NAME| )
                                                                        ( |AGE| )
                                                                        ( |ENTRY_DATE| )
                                                                        ( |MANAGER_ID| )
                                                                        ( |ROOM_ID| )
                                                                        ( |TEAM_ID| )
                                                                        ( |IS_MANAGER| )
                                                                        ( |STATUS| ) ).

  lo_create_response = lo_create_request->execute( ).
  lo_create_response->get_business_data( IMPORTING es_business_data = ls_employee ).
```



### Step-by-step

**Step 1:** Creation of the entity list resource for entity set ‘Employees’ \(with **internal** name ‘EMPLOYEES’\):

```

  DATA: lo_client_proxy         TYPE REF TO /iwbep/if_cp_client_proxy,
        lo_entity_list_resource TYPE REF TO /iwbep/if_cp_resource_list.

  lo_entity_list_resource = lo_client_proxy->create_resource_for_entity_set( 'EMPLOYEES' ).
```

**Step 2:** Now you create the create request instance on the entity list resource.

```

  DATA: lo_update_request       TYPE REF TO /iwbep/if_cp_request_create,
        lo_entity_list_resource TYPE REF TO /iwbep/if_cp_resource_list.

  lo_create_request = lo_entity_list_resource->create_request_for_create( ).
```

**Step 3:** You set the business data for your create request. In our example, the provided properties for the create request are “Id”, “Name”, “Age”, “EntryDate”, “ManagerId”, “RoomId”, “TeamId”, “Status” and “IsManager” \(with **internal** names “ID, “NAME”, “AGE”, “ENTRY\_DATE”, “MANAGER\_ID”, “ROOM\_ID”, “TEAM\_ID”, “STATUS” and “IS\_MANAGER”\). We define the values and set the business data into the create request:

```

  TYPES: BEGIN OF tys_entity_data,
           Id         TYPE i,
           Name       TYPE string,
           age        TYPE i,
           entry_date TYPE dats,
           manager_id TYPE i,
           room_id    TYPE i,
           team_id    TYPE string,
           is_manager TYPE abap_bool,
           status     TYPE string,
         END OF tys_entity_data.

  DATA: lo_update_request TYPE REF TO /iwbep/if_cp_request_create,
        ls_entity_data    TYPE tys_entity_data,
        ls_employee       TYPE /iwbep/s_v4_tea_employee.


  ls_entity_data = VALUE #( id = 007
                            name = ‘James Bond’
                            age = 38
                            entry_date = ‘19621005’
                            manager_id = 001
                            room_id = 1
                            team_id = ‘team_britania’
                            is_manager = abap_false
                            status = ‘Available’ ).

  lo_create_request->set_business_data( is_business_data = ls_entity_data
                                        it_provided_property = VALUE #( ( |ID| )
                                                                        ( |NAME| )
                                                                        ( |AGE| )
                                                                        ( |ENTRY_DATE| )
                                                                        ( |MANAGER_ID| )
                                                                        ( |ROOM_ID| )
                                                                        ( |TEAM_ID| )
                                                                        ( |IS_MANAGER| )
                                                                        ( |STATUS| ) ).


```

> ### Note:  
> Providing the provided properties when calling SET\_BUSINESS\_DATA is optional; if no provided properties are set, all properties are considered for the CREATE request \(otherwise, only the provided properties are considered\).

> ### Note:  
> If the underlying entity has value control or VCS properties, these properties**should** also be part of the provided data container \(ls\_entity\_data in this example\). Otherwise, the behavior for e.g. conversion exits is undefined and might lead to unexpected side-effects in case of non-provided value control/VCS properties.

**Step 4:** You execute the create request and gain the create response instance:

```

  DATA: lo_update_request  TYPE REF TO /iwbep/if_cp_request_create,
        lo_update_response TYPE REF TO /iwbep/if_cp_response_create.

  lo_create_response = lo_create_request->execute( ).
```

**Step 5:** You fetch the business data from the response object:

```

  DATA: lo_update_response TYPE REF TO /iwbep/if_cp_response_create,
        ls_employee        TYPE /iwbep/s_v4_tea_employee.

  lo_create_response->get_business_data( IMPORTING es_business_data = ls_employee ).
```

> ### Note:  
> When using the V4 local client proxy, the business data received from the \(local consumption\) response will not be re-converted for outbound processing.

