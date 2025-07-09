<!-- loio1f353cdf00f44f23bd8a8006bef2cd4e -->

# OData Request: Update Entity List

Create an OData request to update an entity list in the Client Proxy instance.

You want



<a name="loio1f353cdf00f44f23bd8a8006bef2cd4e__section_cg3_vsc_vtb"/>

## OData Specification



### OData Version 2

An update request for an entity list is not supported in OData Version 2.



### OData Version 4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html).

You can update entity collections by submitting a `PATCH` request to the collection's resource path. The body of the request:

-   **MUST** be a `delta payload`.
-   the resource path of the collection **MUST NOT** include type cast or filter segments.
-   **MUST NOT** include any system query options that affect the shape of the result.

Added/changed entities are applied as upserts. Deleted entities are applied as deletions.



<a name="loio1f353cdf00f44f23bd8a8006bef2cd4e__section_w5n_ftc_vtb"/>

## Example Requests



### Version 4

Update the complete entity set “`Teams`”:

```
PATCH /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Teams
```

With request body

```

{ 
	"@context" : "#$delta", 
	"value" : [ 
		{ 
		  "Id" : "NEW 1", 
		  "Name" : "Created", 
		  "MemberCount" : 2, 
		  "ManagerId" : "3", 
		  "BudgetCurrency" : "USD",
		  "Budget" : 555.55
		},
		{ 
		  "Id" : "TEAM_02", 
		  "Name" : "Update?" 
		}, 
		{ 
		  "Id" : "New 3", 
		  "Name" : "Created" 
		} 
	] 
}
```



<a name="loio1f353cdf00f44f23bd8a8006bef2cd4e__section_ixg_15c_vtb"/>

## Updata Entity List Request



### Overview

The starting point for a `PATCH` entity request is the Client Proxy instance. You can create an `entity resource` based on an `update list` request, and use it to create an update request.

Running the `update list` provides the update list response, which can return the business data of the `UPDATE` entity list request.



### Example

Update the entity set “`Teams`”:

```
PATCH /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Teams
```

With request body

```

{ 
	"@context" : "#$delta", 
	"value" : [ 
	    { 
		  "Id" : "New Team",
		  "Name" : "Created",
		  "BudgetCurrency" : "USD",
		  "Budget" : 555 
	    },
		{ 
		  "Id" : "TEAM_02",
		  "Name" : "New Team Name" 
		} 
	] 
}
```

```

DATA:	lo_client_proxy TYPE REF TO /iwbep/if_cp_client_proxy,
         lo_update_list_request TYPE REF TO /iwbep/if_cp_request_update_l,
         lo_update_list_response TYPE REF TO /iwbep/if_cp_response_update_l,
         lo_list_resource TYPE REF TO /iwbep/if_cp_resource_list,
         lt_response_data TYPE STANDARD TABLE OF /iwbep/s_v4_tea_team,
         lt_request_data TYPE STANDARD TABLE OF /iwbep/s_v4_tea_team.


		 lo_list_resource = lo_client_proxy->create_resource_for_entity_set( 'TEAMS’ ).
		 lo_update_list_request = lo_list_resource->create_request_for_update( ).


		 lt_request_data = value #( ( id =‘New team’ name =‘Created’ budget =555 budget_currency =‘USD’ )
		 	( id = ‘TEAM_02’ name = ‘New Team Name’ ) ) .


		 lo_update_list_request->set_business_data( it_business_data = lt_request_data ).
		 lo_update_list_request->request_continue_on_error( ).
		 lo_update_list_response = lo_update_list_request->execute( ).
		 lo_update_list_response->get_business_data( IMPORTING et_business_data = lt_response_data )
```



### Steps

**Step 1:** Create the entity list resource for entity set ‘`Teams`’ \(with **internal** name ‘`TEAMS`’\):

```

DATA:	lo_client_proxy TYPE REF TO /iwbep/if_cp_client_proxy,
		 lo_list_resource TYPE REF TO /iwbep/if_cp_resource_list.

         lo_list_resource = lo_client_proxy->create_resource_for_entity_set( 'TEAMS’ ).
```

**Step 2:** Create the update list request instance on the entity list resource:

```

DATA:	lo_update_list_request TYPE REF TO /iwbep/if_cp_request_update_l,
         lo_list_resource       TYPE REF TO /iwbep/if_cp_resource_list.

		 lo_update_list_request = lo_list_resource->create_request_for_update( ).
```

**Step 3:** Set the business data \(for example, update\) for your update list request. Define the corresponding business data and set it into the update list request:

```

DATA:	lo_update_list_request TYPE REF TO /iwbep/if_cp_request_update_l,
         lt_request_data        TYPE STANDARD TABLE OF /iwbep/s_v4_tea_team.


		 lt_request_data = VALUE #( ( id = ‘New team’ name = ‘Created’ budget = 555 budget_currency = ‘usd’ )
		 ( id = ‘team_02’ name = ‘New Team Name’ ) ) .

		 lo_update_list_request->set_business_data( it_business_data = lt_request_data ).
```

**Step 4:** \(Optional\) Request that the request processing continues even when there is an error \(if supported\).

If the server supports this setting, a failed operation for one entity doesn't cause the complete request to fail. The failed entity is marked with the instance annotation **`Core.DataModificationException:`** 

```

DATA:	lo_update_list_request TYPE REF TO /iwbep/if_cp_request_update_l.

		 lo_update_list_request->request_continue_on_error( ).
```

> ### Note:  
> This information is mapped into the request header **`prefer:odata.continue-on-error`**. This preference is optional. The consumed OData service does **not** have to follow this preference.

**Step 5:** Run the update list request and get the update list response instance:

```

DATA:    lo_update_list_request  TYPE REF TO /iwbep/if_cp_request_update_l,
		 lo_update_list_response TYPE REF TO /iwbep/if_cp_response_update_l.

		 lo_update_list_response = lo_update_list_request->execute( ).
```

**Step 6:** Fetch the business data from the response list object:

```

DATA:    lo_update_list_response TYPE REF TO /iwbep/if_cp_response_update_l,
         lt_response_data        TYPE STANDARD TABLE OF /iwbep/s_v4_tea_team.

		 lo_update_list_response->get_business_data( IMPORTING et_business_data = lt_response_data ).
```



<a name="loio1f353cdf00f44f23bd8a8006bef2cd4e__section_hbp_zxc_vtb"/>

## Constraints

-   Updating an entity list is only supported for OData Version 4

-   This feature is not supported for local consumption

-   Only `PATCH` is supported. `PUT` is not supported.

-   `IF-MATCH` handling is not supported

-   Query options are not supported

-   Updating an entity list within a $batch is not supported


**Related Information**  


[OData Request Terms](odata-request-terms-a3b0e95.md "An overview of some OData Request terminology.")

