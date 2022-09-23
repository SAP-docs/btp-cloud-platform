<!-- loioa4a4eb8c6d1045e5bd34d92a72b3cb36 -->

# OData Request: Update Entity

Create an OData request to update an entity in the Client Proxy instance.



<a name="loioa4a4eb8c6d1045e5bd34d92a72b3cb36__section_gmk_p5w_5tb"/>

## OData Specification



### OData Version 2

See also: [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata).

An ***UpdateEntity*** Request is used by a client to update an existing AtomPub Entry Resource, as specified in [RFC5023](https://www.rfc-editor.org/rfc/rfc5023.txt), that maps to an EntityType instance in the abstract data model.



### OData Version 4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html).

To update an individual entity, the client makes a ***PATCH*** or ***PUT*** request to a URL that identifies the entity. Services can be restricted to only request updates addressing the edit URL of the entity.



<a name="loioa4a4eb8c6d1045e5bd34d92a72b3cb36__section_p32_cvw_5tb"/>

## Example Requests



### Version 4

Update the employee with id ‘***007***’ of entity set “***Employees***

```
PATCH /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees(‘007’)
```

With request body

```

{ 
  "Car" : "Aston Martin DB5" 
}
```



### Version 2

Update the employee with id ‘***007***’ of entity set “***Employees***”:

```
PUT /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Employees(‘007’)
```

With request body

```

{ "Id" : "007",
  "Name" : "James Bond",
  "Gun" : "Walther PPK",
  "Car" : "Aston Martin DB5" 
}
```



<a name="loioa4a4eb8c6d1045e5bd34d92a72b3cb36__section_udg_xvw_5tb"/>

## Update Entity Request



### Overview

> ### Note:  
> As the coding is independent of the OData version, we're presenting a general example on how to create a ***UPDATE*** request on an entity.

The starting point for a ***PUT/PATCH*** entity request is the Client Proxy instance. You can create an ***entity resource*** based on an ***entity list resource***, and use it to create an update request.

Running the update request provides the update response, which can return the business data of the ***UPDATE*** entity request.



### Example

Update the employee with key “id = ‘***007***'” of the Version 4 entity set ‘***Employees***':

```
PATCH /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees(‘007’)
```

With request body

```

{ 
	"Age" : 38, 
	"IsManager" : true, 
	"Status" : "Available" 
}
```

```

TYPES:	BEGIN OF tys_patch_data,
		  types: BEGIN OF tys_patch_data,
		  age        TYPE i,
		  is_manager TYPE abap_bool,
		  status     TYPE string,
		  END OF tys_patch_data.


DATA:	 lo_client_proxy    TYPE REF TO /iwbep/if_cp_client_proxy,
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



### Steps

**Step 1:** Create the entity resource for the employee with the following:

-   key “Id=‘***007***” in the entity set ‘***Employees***’ \(**internal** name ‘***EMPLOYEES’***\)
-   type “***ty\_s\_employee\_key***” in the interface ***/iwbep/if\_v4\_tea\_busi\_types***”

```

DATA	  lo_client_proxy    TYPE REF TO /iwbep/if_cp_client_proxy,
		  lo_entity_resource TYPE REF TO /iwbep/if_cp_resource_entity.

		  lo_entity_resource = lo_client_proxy->create_resource_for_entity_set( 'EMPLOYEES')->navigate_with_key(value /iwbep/if_v4_tea_busi_types=>ty_s_employee_key( id = ‘007’) ).
```

**Step 2:** Create the update request instance on the entity resource. You need to provide the correct semantic \(either ***PATCH*** or ***PUT***\). ***PUT*** creates a full new resource representation. If some attributes are not provided, these attributes should be removed \(set to null\) or set to their default value. ***PATCH*** also updates a resource, but unlike ***PUT***, it applies a delta rather than replacing the entire resource. The ***PATCH*** payload is a different content-type than the entity that it is modifying. Instead of being a full resource, it is a resource that describes modifications that be made to a resource.

In our example, we use ***PATCH*** semantic. You can use the constants in structure ***gcs\_update\_semantic*** of interface ***/iwbep/if\_cp\_request\_update***as input:

```

DATA:	 lo_update_request  TYPE REF TO /iwbep/if_cp_request_update,
          lo_entity_resource TYPE REF TO /iwbep/if_cp_resource_entity.

		  lo_update_request = lo_entity_resource->create_request_for_update( /iwbep/if_cp_request_update=>gcs_update_semantic-patch ). 
```

**Step 3:** Set the business \(for example, update\) data for your update request. In our example, we want to update three properties. We define the new values and set the business data into the update request:


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

Age



</td>
<td valign="top">

***AGE***



</td>
</tr>
<tr>
<td valign="top">

Status



</td>
<td valign="top">

***STATUS***



</td>
</tr>
<tr>
<td valign="top">

IsManager



</td>
<td valign="top">

***IS\_MANAGER***



</td>
</tr>
</table>

```

TYPES:	BEGIN OF tys_patch_data,
          age        TYPE i,
          is_manager TYPE abap_bool,
          status     TYPE string,
          END OF tys_patch_data.


DATA: 	lo_update_request TYPE REF TO /iwbep/if_cp_request_update,
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
> Providing the properties is required when calling ***SET\_BUSINESS\_DATA*** for a ***PATCH*** request.

**Step 4:** Set the ***If-Match*** header to provide a ETag \(if needed for this request\). For example, if the corresponding request header is ***if-match***: ***W/"1234"***, the required input for ***SET\_IF\_MATCH*** is ‘***1234***’:

```

DATA: 	lo_update_request TYPE REF TO /iwbep/if_cp_request_update.
 
		  lo_update_request->set_if_match( ‘1234’ ).
```

**Step 5:** Run the update request and get the update response instance:

```

DATA:	 lo_update_request  TYPE REF TO /iwbep/if_cp_request_update,
          lo_update_response TYPE REF TO /iwbep/if_cp_response_update.
		  
		  lo_update_response = lo_update_request->execute( ).
```

**Step 6:** Fetch the business data from the response object:

```

DATA:	 lo_update_response TYPE REF TO /iwbep/if_cp_response_update,
		  ls_employee        TYPE /iwbep/s_v4_tea_employee.

		  lo_update_response->get_business_data( IMPORTING es_business_data = ls_employee ).
```

> ### Note:  
> When you're using the Version 4 local client proxy, the business data you receive from the local consumption response isn't converted again for outbound processing.

**Related Information**  




