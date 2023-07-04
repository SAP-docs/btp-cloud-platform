<!-- loioc8923967410d4a9e8ed475e2569d8be1 -->

# OData Request: Deep Create

Create an OData request to execute a “deep create” \(deep insert\) in the Client Proxy instance.



<a name="loioc8923967410d4a9e8ed475e2569d8be1__section_pgm_cjf_rtb"/>

## OData Specification



### OData Version 2

See also: [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata).

In the Deep Create request, you can insert a new EntityType instance \(E1\) into an EntitySet and insert new entities related to E1. This is described by a NavigationProperty on the EntityType associated with E1\) in a single InsertEntity Request. For example, in a customer relationship management-focused data service, you can insert a new customer entity and new related order entities in a single `InsertEntity` Request. This type of an InsertEntity Request is also known as a "deep insert".



### OData Version 4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html).

A "deep insert" request creates an entity that includes related entities using the appropriate inline representation



<a name="loioc8923967410d4a9e8ed475e2569d8be1__section_h5p_5jf_rtb"/>

## Example Requests



### Version 4

Create a new team \(entity set “`TEAMS`”\) and a new manager \(entity set “`MANAGERS`”\) via navigation property “`TEAM_2_MANAGER`”:

```
POST /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/TEAMS
```

With request body

```
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



### Version 2

Create the employee with id ‘`1`’ \(entity set “`EMPLOYEES`”\) and the corresponding team \(entity set “`TEAMS`”\) with navigation property “`My_Team`”:

```
POST /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Employees
```

With request body

```

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

## Deep Create Request



### Overview

> ### Note:  
> As the coding itself is independent of the OData version, we will just present one general example on how to create a execute a deep create request.
> 
> As the coding is independent of the OData version, we're presenting a general example on how to create a `deep create`request on an entity.

The main difference between a `create` and a `deep create` request in the Client Proxyinstance is that the `deep create` request requires a data description node. You create a data description node at the create request instance and it is used later when setting the deep business data.

> ### Note:  
> See [OData Request: Create Entity](odata-request-create-entity-56be82d.md) for more information.



### Example

Create a new team \(entity set “`Teams`”\) and a new manager \(entity set “`Managers`”\):

```
POST /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Team
```

With request body

```

{ 
		"Id" : "TEAM_04", 
		"MemberCount" : 2, 
		"Team2Manager" : { 
		"Id" : "0009" 
	} 
}
```

```

DATA:   lo_create_request       TYPE REF TO /iwbep/if_cp_request_create,
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



### Steps

**Step 1:** Creation of the data description node for the root entity \(here: “Teams”\) on the create request instance:

```

DATA:   lo_create_request     TYPE REF TO /iwbep/if_cp_request_create,
		lo_data_des_node_root TYPE REF TO /iwbep/if_cp_data_desc_node.

		lo_data_desc_node_root = lo_create_request->create_data_description_node( ).
```

> ### Note:  
> See [OData Request: Create Entity](odata-request-create-entity-56be82d.md) for more information.

**Step 2:** Set the properties for the root entity. In our example, the properties are “`Id`” \(internal name “`ID`”\) and “`MemberCount`” \(internal name “`MEMBER_COUNT`”\):

```

DATA:   lo_data_des_node_root TYPE REF TO /iwbep/if_cp_data_desc_node.

		lo_data_desc_node_root->set_properties( VALUE #( ( |ID| ) ( |MEMBER_COUNT| ) ) ).
```

**Step 3:** Create the data description node for the child entity \(in this example, “`Managers`”\) on the root data description node. “`TEAM_2_MANAGER`” is the **internal** name of navigation property “`Team2Manager`”:

```

DATA:   lo_data_des_node_root   TYPE REF TO /iwbep/if_cp_data_desc_node,
		lo_data_desc_node_child TYPE REF TO /iwbep/if_cp_data_desc_node.

		lo_data_desc_node_child = lo_data_desc_node_root->add_child( ‘team_2_manager’ ).
```

**Step 4:** Set the properties for the child entity \(in this example, “`Managers`”\). Only property “`Id`” \(with internal name “`ID`” \) is included:

```

DATA:   lo_data_desc_node_child TYPE REF TO /iwbep/if_cp_data_desc_node.

		lo_data_desc_node_child->set_properties( VALUE #( ( |ID| ) ) ).
```

**Step 5:** Define the request data for the deep create and set the deep business data into the request instance \(in the root data description node\):

```

DATA:   lo_create_request     TYPE REF TO /iwbep/if_cp_request_create,
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
> The property that references the child entity business data MUST be named using the **internal** name of the corresponding navigation property \(in this example, the property is “T`EAM_2_MANAGER`”, which describes the business data for the child entity “`Managers`”\).

> ### Note:  
> If the underlying entity has value control or VCS properties. The VCS properties **should** also be part of the provided data container \(in this example, `ls_deep_busi_data`\). If the properties aren't part of the data container, the behavior \(for example conversion exits\) is undefined and can cause nexpected errors.

**Step 6:** Run the deep create request and fetch the response business data from the create response instance:

```

DATA:   lo_create_request  TYPE REF TO /iwbep/if_cp_request_create,
        lo_create_response TYPE REF TO /iwbep/if_cp_response_create,
        ls_response_data   TYPE /iwbep/if_v4_tea_busi_types=>ty_s_team_and_manager.


		lo_create_response = lo_create_request->execute( ).
		lo_create_response->get_business_data( IMPORTING es_business_data = ls_response_data ).
```

> ### Note:  
> This part is identical to handling a typical create request in the Client Proxy instance.

**Related Information**  


[OData Request Terms](odata-request-terms-a3b0e95.md "An overview of some OData Request terminology.")

[OData Request: Using Navigation](odata-request-using-navigation-57f2139.md "Create an OData request using a navigation in the Client Proxy instance.")

[OData Request: Create Entity](odata-request-create-entity-56be82d.md "Create an entity in the Client Proxy instance with insert entity request.")

