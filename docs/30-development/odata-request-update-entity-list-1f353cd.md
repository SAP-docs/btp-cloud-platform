<!-- loio1f353cdf00f44f23bd8a8006bef2cd4e -->

# OData Request: Update Entity List

You want to execute an OData request to update an entity list using the Client Proxy.



<a name="loio1f353cdf00f44f23bd8a8006bef2cd4e__section_cg3_vsc_vtb"/>

## OData Specification



### OData V2

\(An update request for an entity list is not supported in OData V2\).



### OData V4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html)

Collections of entities can be updated by submitting a PATCH request to the resource path of the collection. The body of the request MUST be a delta payload, and the resource path of the collection MUST NOT contain type cast or filter segments, and MUST NOT contain any system query options that affect the shape of the result.

Added/changed entities are applied as upserts, and deleted entities as deletions.



<a name="loio1f353cdf00f44f23bd8a8006bef2cd4e__section_w5n_ftc_vtb"/>

## Example Requests



### V4

Update the complete entity set “Teams”:

```
PATCH /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Teams
```

```


With request body

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

## How-To



### Overview

Starting point for a PATCH request on an entity list is the Client Proxy instance. There, it is possible to create an entity list resource, which can then be used to create an update list request.

Executing the update list request finally provides the update list response, which can return the business data of the UPDATE entity list request.



### Example

You want to update the entity set “Teams”:

```
PATCH /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Teams
```

```


With request body

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

  DATA: lo_client_proxy TYPE REF TO /iwbep/if_cp_client_proxy,
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



### Step-by-step

**Step 1:** Creation of the entity list resource for entity set ‘Teams’ \(with **internal** name ‘TEAMS’\):

```

  DATA: lo_client_proxy TYPE REF TO /iwbep/if_cp_client_proxy,
        lo_list_resource TYPE REF TO /iwbep/if_cp_resource_list.

        lo_list_resource = lo_client_proxy->create_resource_for_entity_set( 'TEAMS’ ).
```

**Step 2:** Now you create the update list request instance on the entity list resource:

```

  DATA: lo_update_list_request TYPE REF TO /iwbep/if_cp_request_update_l,
        lo_list_resource       TYPE REF TO /iwbep/if_cp_resource_list.

  lo_update_list_request = lo_list_resource->create_request_for_update( ).
```

**Step 3:** You set the business \(i.e. update\) data for your update list request. Define the corresponding business data and set it into the update list request:

```

  DATA: lo_update_list_request TYPE REF TO /iwbep/if_cp_request_update_l,
        lt_request_data        TYPE STANDARD TABLE OF /iwbep/s_v4_tea_team.


  lt_request_data = VALUE #( ( id = ‘New team’ name = ‘Created’ budget = 555 budget_currency = ‘usd’ )
                             ( id = ‘team_02’ name = ‘New Team Name’ ) ) .

  lo_update_list_request->set_business_data( it_business_data = lt_request_data ).
```

**Step 4:** You request that the request processing continues even in case of an error \(this step is not mandatory\).

If this is supported by the server then a failed operation for one of the entities will not cause the complete request to fail. Instead only that entity is marked with the instance annotation **`Core.DataModificationException:`** 

```

  DATA: lo_update_list_request TYPE REF TO /iwbep/if_cp_request_update_l.

  lo_update_list_request->request_continue_on_error( ).
```

> ### Note:  
> This information is mapped into the request header**`prefer:odata.continue-on-error`**. This preference is optional. The consumed OData service does **not** have to follow this preference.

**Step 5:** You execute the update list request and gain the update list response instance:

```

  DATA: lo_update_list_request  TYPE REF TO /iwbep/if_cp_request_update_l,
        lo_update_list_response TYPE REF TO /iwbep/if_cp_response_update_l.

  lo_update_list_response = lo_update_list_request->execute( ).
```

**Step 6:** You fetch the business data from the response list object:

```

  DATA: lo_update_list_response TYPE REF TO /iwbep/if_cp_response_update_l,
        lt_response_data        TYPE STANDARD TABLE OF /iwbep/s_v4_tea_team.

  lo_update_list_response->get_business_data( IMPORTING et_business_data = lt_response_data ).
```



<a name="loio1f353cdf00f44f23bd8a8006bef2cd4e__section_hbp_zxc_vtb"/>

## Constraints

-   Updating an entity list is only supported for OData V4

-   This feature is not supported for local consumption

-   Only PATCH is supported, not PUT

-   IF-MATCH handling is not supported

-   Query options are not supported

-   Updating an entity list within a $batch is not supported


