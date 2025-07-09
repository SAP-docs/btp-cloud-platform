<!-- loio56be82d78dc14e41b5935c878c72fec3 -->

# OData Request: Create Entity

Create an entity in the Client Proxy instance with insert entity request.



<a name="loio56be82d78dc14e41b5935c878c72fec3__section_bcw_pb3_ptb"/>

## OData Specification



### OData Version 2

See [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata).

The `InsertEntity` request enables a new EntityType instance with new related entities you add to an EntitySet.



### OData Version 4

See [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html).

To create an entity in a collection, the client sends a `POST` request to the collection's URL. The `POST` body MUST contain a single valid entity representation.



<a name="loio56be82d78dc14e41b5935c878c72fec3__section_ccv_zc3_ptb"/>

## Example Requests



### Version 4

Create the employee with id ‘`007`’ in the entity set “`Employees`”

```
POST /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees
```

With request body

```

{ 
	"Id" : "007", 
	"Name" : "James Bond", 
	"Gun" : "Walther PPK", 
	"Car" : "Aston Martin DB5"
}
 
```



### Version 2

Create the employee with id ‘`007`’ in the entity set “`Employees`”

```
POST /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Employees
```

With request body

```

{ 
	"Id" : "007", 
	"Name" : "James Bond", 
	"Gun" : "Walther PPK", 
	"Car" : "Aston Martin DB5"
}

```



<a name="loio56be82d78dc14e41b5935c878c72fec3__section_hpb_kv2_rtb"/>

## Create Entity Request



### Overview

> ### Note:  
> As the coding is independent of the OData version, we're presenting a general example on how to create a `CREATE` request on an entity..

The starting point for a `POST` request on an entity list is the Client Proxy instance. It's possible to create an entity list resource, which can then be used to create a create request.

Running the create request provides the create response instance, which can return the business data for the `CREATE` entity request.



### Example

Create the employee with key id = '`007` 'of the Version 4 entity set ‘`Employees`':

```
POST /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees
```

With request body

```

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


```

```

DATA:	lo_client_proxy         TYPE REF TO /iwbep/if_cp_client_proxy,
         lo_create_request       TYPE REF TO /iwbep/if_cp_request_create,
         lo_create_response      TYPE REF TO /iwbep/if_cp_response_create,
         lo_entity_list_resource TYPE REF TO /iwbep/if_cp_resource_list,
         ls_entity_data          TYPE tys_entity_data, ls_employee
		 TYPE /iwbep/s_v4_tea_employee.


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



### Steps

**Step 1:** Create the entity list resource for entity set ‘`Employees`’ \(with **internal** name ‘`EMPLOYEES’`'\):

```

DATA:	lo_client_proxy         TYPE REF TO /iwbep/if_cp_client_proxy,
         lo_entity_list_resource TYPE REF TO /iwbep/if_cp_resource_list.

		 lo_entity_list_resource = lo_client_proxy->create_resource_for_entity_set( 'EMPLOYEES' ).
```

**Step 2:** Run the create request instance on the entity list resource.

```

DATA:	lo_update_request       TYPE REF TO /iwbep/if_cp_request_create,
         lo_entity_list_resource TYPE REF TO /iwbep/if_cp_resource_list.

		 lo_create_request = lo_entity_list_resource->create_request_for_create( ).
```

**Step 3:** Set the business data for your create request. In our example, the create request properties are:


<table>
<tr>
<th valign="top">

Properties

</th>
<th valign="top">

Internal Names

</th>
</tr>
<tr>
<td valign="top">

Id

</td>
<td valign="top">

`ID`

</td>
</tr>
<tr>
<td valign="top">

Name

</td>
<td valign="top">

`NAME`

</td>
</tr>
<tr>
<td valign="top">

Age

</td>
<td valign="top">

`AGE`

</td>
</tr>
<tr>
<td valign="top">

EntryDate

</td>
<td valign="top">

`ENTRY_DATE`

</td>
</tr>
<tr>
<td valign="top">

ManagerId

</td>
<td valign="top">

`MANAGER_ID`

</td>
</tr>
<tr>
<td valign="top">

RoomId

</td>
<td valign="top">

`ROOM_ID`

</td>
</tr>
<tr>
<td valign="top">

TeamId

</td>
<td valign="top">

`TEAM_ID`

</td>
</tr>
<tr>
<td valign="top">

Status

</td>
<td valign="top">

`STATUS`

</td>
</tr>
<tr>
<td valign="top">

IsManager

</td>
<td valign="top">

`IS_MANAGER`

</td>
</tr>
</table>

Define the values and set the business data into the create request:

```

TYPES: 	BEGIN OF tys_entity_data,
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

DATA: 	lo_update_request TYPE REF TO /iwbep/if_cp_request_create,
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
> \(Optional\) Provide the properties when calling `SET_BUSINESS_DATA`. If you provide properties, only the properties you set are considered. If you don't provide properties, all properties are considered for the `CREATE` request.

> ### Note:  
> If the entity has value control or VCS properties, these properties **should** also be part of the provided data container \(`ls_entity_data` in this example\). If the value control/VCS properties are not provided, the behavior \(for example: conversion exits\) is undefined and can cause unexpected side-effects.

**Step 4:** Run the `create` request and get the create response instance:

```

DATA: 	lo_update_request  TYPE REF TO /iwbep/if_cp_request_create,
          lo_update_response TYPE REF TO /iwbep/if_cp_response_create.

		  lo_create_response = lo_create_request->execute( ).
```

**Step 5:** You fetch the business data from the response object:

```

DATA:	 lo_update_response TYPE REF TO /iwbep/if_cp_response_create,ls_employee   
	      TYPE /iwbep/s_v4_tea_employee.

		  lo_create_response->get_business_data( IMPORTING es_business_data = ls_employee ).
```

> ### Note:  
> When you're using the Version 4 local client proxy, the business data you receive from the local consumption response isn't converted again for outbound processing.

**Related Information**  


[OData Request Terms](odata-request-terms-a3b0e95.md "An overview of some OData Request terminology.")

