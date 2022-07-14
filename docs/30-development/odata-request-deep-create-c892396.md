<!-- loioc8923967410d4a9e8ed475e2569d8be1 -->

# OData Request: Deep Create

You want to execute an OData request to execute a “deep create” \(aka “deep insert”\) using the Client Proxy.



<a name="loioc8923967410d4a9e8ed475e2569d8be1__section_pgm_cjf_rtb"/>

## OData Specification



### OData V2

See also: [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata)

In addition to supporting the insertion of a new EntityType instance \(E1\) into an EntitySet, this request type allows inserting new entities related to E1 \(described by a NavigationProperty on the EntityType associated with E1\) using a single InsertEntity Request. For example, in a customer relationship management focused data service, a new customer entity and new related order entities could be inserted using a single InsertEntity Request. This form of an InsertEntity Request is also known as a "deep insert".



### OData V4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html)

A request to create an entity that includes related entities, represented using the appropriate inline representation, is referred to as a “deep insert”.



<a name="loioc8923967410d4a9e8ed475e2569d8be1__section_h5p_5jf_rtb"/>

## Example Requests



### V4

Create a new team \(entity set “TEAMS”\) and a new manager \(entity set “MANAGERS”\) via navigation property “TEAM\_2\_MANAGER”:

```
POST /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/TEAMS
```

```

With request body
{ 
	"Name" : "Business Suite", 
	"MEMBER_COUNT" : 2, 
	"MANAGER_ID" : "8", 
	"BudgetCurrency" : "USD", 
	"Budget" : 555.55, 
	"TEAM_2_MANAGER" : {
	 "ID" : "8", 
	 "TEAM_ID" : "" 
	} 
}
```



### V2

Create the employee with id ‘1’ \(entity set “EMPLOYEES”\) and his corresponding team \(entity set “TEAMS”\) via navigation property “My\_Team”:

```
POST /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Employees
```

```

With request body

{
	 "Location" : { 
		"Country" : "Germany", 
		"City" : { 
			"PostalCode" : "69124",
		 	"CityName" : "Heidelberg", 
			"VeryLongPropertyNameForOrderBy" : "" 
	} 
}, 
"Id" : "1", 
"Name" : "Walter Winter", 
"Age" : " 52", 
"EntryDate" : "\/Date(915148800000)\/", 
"Manager_ID" : "1", 
"Room_ID" : "1", 
"Team_ID" : "TEAM_01", 
"My_Team" : { 
	"Team_Identifier" : "TEAM_01", 
	"Name" : "Business Suite" 
	} 
}
```



<a name="loioc8923967410d4a9e8ed475e2569d8be1__section_yp2_3mf_rtb"/>

## How-To



### Overview

> ### Note:  
> As the coding itself is independent of the OData version, we will just present one general example on how to create a execute a deep create request.

The main difference between a create and a deep create request within the Client Proxy is the need for a data description node for the latter. A data description node is created at the create request instance and later used when setting the deep business data.

> ### Note:  
> See the chapter about creating an entity via the client proxy for more details about CREATE requests.



### Example

You want to create a new team \(entity set “Teams”\) and a new manager \(entity set “Managers”\):

```
POST /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Team
```

```


With request body

{ 
	"Id" : "TEAM_04", 
	"MemberCount" : 2, 
	"Team2Manager" : { 
	 "Id" : "0009" 
	} 
}
```

```


  DATA: lo_create_request       TYPE REF TO /iwbep/if_cp_request_create,
        lo_create_response      TYPE REF TO /iwbep/if_cp_response_create,
        lo_data_des_node_root   TYPE REF TO /iwbep/if_cp_data_desc_node,
        lo_data_desc_node_child TYPE REF TO /iwbep/if_cp_data_desc_node,
        ls_deep_busi_data       TYPE /iwbep/if_v4_tea_busi_types=>ty_s_team_and_manager,
        ls_response_data        TYPE /iwbep/if_v4_tea_busi_types=>ty_s_team_and_manager.


  lo_data_desc_node_root = lo_create_request->create_data_description_node( ).
  lo_data_desc_node_root->set_properties( VALUE #( ( |ID| ) ( |MEMBER_COUNT| ) ) ).

  lo_data_desc_node_child = lo_data_desc_node_root->add_child( ‘team_2_manager’ ).
  lo_data_desc_node_child->set_properties( VALUE #( ( |ID| ) ) ).

  ls_deep_busi_data = VALUE #( id = ‘team_04’
                               member_count = 2
                               team_2_manager = VALUE #( id = ‘0009’ ) ).


  lo_create_request->set_deep_business_data( is_business_data = ls_deep_busi_data
                                             io_data_description_node = lo_data_desc_node_root ).

  lo_create_response = lo_create_request->execute( ).

  lo_create_response->get_business_data( IMPORTING es_business_data = ls_response_data ).

lo_create_response->get_business_data( IMPORTING es_business_data = ls_response_data ).
```



### Step-by-step

**Step 1:** Creation of the data description node for the root entity \(here: “Teams”\) on the create request instance:

```

  DATA: lo_create_request     TYPE REF TO /iwbep/if_cp_request_create,
        lo_data_des_node_root TYPE REF TO /iwbep/if_cp_data_desc_node.

  lo_data_desc_node_root = lo_create_request->create_data_description_node( ).
```

> ### Note:  
> See the corresponding chapter on how to build a create request instance.

**Step 2:** You set the provided properties for the root entity . In our example, these are “Id” \(internal name “ID”\) and “MemberCount” \(internal name “MEMBER\_COUNT”\):

```

  DATA: lo_data_des_node_root TYPE REF TO /iwbep/if_cp_data_desc_node.

  lo_data_desc_node_root->set_properties( VALUE #( ( |ID| ) ( |MEMBER_COUNT| ) ) ).
```

**Step 3:** You create the data description node for the child entity \(here: “Managers”\) on the root data description node. “TEAM\_2\_MANAGER” is the **internal** name of navigation property “Team2Manager”:

```

  DATA: lo_data_des_node_root   TYPE REF TO /iwbep/if_cp_data_desc_node,
        lo_data_desc_node_child TYPE REF TO /iwbep/if_cp_data_desc_node.

  lo_data_desc_node_child = lo_data_desc_node_root->add_child( ‘team_2_manager’ ).
```

**Step 4:** You set the provided properties for the child entity \(here: “Managers”\). Only property “Id” \(with internal name “ID” \) is provided:

```

  DATA: lo_data_desc_node_child TYPE REF TO /iwbep/if_cp_data_desc_node.

  lo_data_desc_node_child->set_properties( VALUE #( ( |ID| ) ) ).
```

**Step 5:** You define the request data for the deep create and set the deep business data into the request instance \(using the root data description node\):

```

  DATA: lo_create_request     TYPE REF TO /iwbep/if_cp_request_create,
        lo_data_des_node_root TYPE REF TO /iwbep/if_cp_data_desc_node,
        ls_deep_busi_data     TYPE /iwbep/if_v4_tea_busi_types=>ty_s_team_and_manager.


  ls_deep_busi_data = VALUE #( id = ‘team_04’
                               member_count = 2
                               team_2_manager = VALUE #( id = ‘0009’ ) ).


  lo_create_request->set_deep_business_data( is_business_data = ls_deep_busi_data
                                             io_data_description_node = lo_data_desc_node_root ).
ENDCLASS.
```

> ### Note:  
> The property referencing the child entity business data MUST be named like the **internal** name of the corresponding navigation property \(in this example, that property is “TEAM\_2\_MANAGER”, which describes the business data for the child entity “Managers”\)!

> ### Note:  
> If the underlying entity has value control or VCS properties, these properties**should** also be part of the provided data container \(`ls_deep_busi_data` in this example\). Otherwise, the behavior for e.g. conversion exits is undefined and might lead to unexpected side-effects in case of non-provided value control/VCS properties.

**Step 6:**You execute the deep create request and fetch the response business data from the create response instance:

```

  DATA: lo_create_request  TYPE REF TO /iwbep/if_cp_request_create,
        lo_create_response TYPE REF TO /iwbep/if_cp_response_create,
        ls_response_data   TYPE /iwbep/if_v4_tea_busi_types=>ty_s_team_and_manager.


  lo_create_response = lo_create_request->execute( ).
  lo_create_response->get_business_data( IMPORTING es_business_data = ls_response_data ).
```

> ### Note:  
> This part is identical to handling a “normal” create request within the Client Proxy. See the chapter for creating an entity for a more detailed description.

