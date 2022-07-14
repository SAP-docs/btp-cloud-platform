<!-- loio215cca8d5c7c4e27b775271d4cb6e24c -->

# OData Request: System Query Option $expand

You want to execute an OData request using the system query option $expand within the Client Proxy.



<a name="loio215cca8d5c7c4e27b775271d4cb6e24c__section_dnd_2zw_stb"/>

## OData Specification



### OData V2

See also: [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata)

The presence of the $expand System Query Option indicates that entities associated with the EntityType instance or EntitySet, identified by the Resource Path section of the URI, MUST be represented inline \(…\)



### OData V4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html)

The $expand system query option indicates the related entities and stream values that MUST be represented inline. The service MUST return the specified content, and MAY choose to return additional information.

The value of the $expand query option is a comma-separated list of navigation property names, stream property names, or $value indicating the stream content of a media-entity.



<a name="loio215cca8d5c7c4e27b775271d4cb6e24c__section_xgz_b1x_stb"/>

## Example Requests



### V4

Get the team ‘TEAM\_03’ and also retrieve its manager via navigation property “Team2Manager”:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Teams('TEAM_03')?$expand=Team2Manager
```



### V2

Get the manager with id ‘0004’ and also retrieve the information about his team via navigation property “My\_Team”:

```
GET /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Managers('0001')?$expand=My_Team
```



<a name="loio215cca8d5c7c4e27b775271d4cb6e24c__section_jg3_41x_stb"/>

## How-To



### Overview

> ### Note:  
> As the coding itself is independent of the OData version, we will just present general examples on how to use $expand.

Starting point for a request with $expand is an entity \(list\) read request. Kindly check e.g. the chapter about reading an entity or an entity list on how to create an entity \(list\) read request instance. On the entity \(list\) read request, it is possible to set the $expand.



### Example

You want to get all entities of entity set “Teams” and – for each team- also fetch the corresponding manager via navigation property “Team2Manager”. Furthermore, you only want to retrieve the Id of each manager:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Teams?$expand=Team2Manager($select=Id)
```



### Step-by-step

```

  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_expand_node_root  TYPE REF TO /iwbep/if_cp_expand_node,
        lo_expand_node       TYPE REF TO /iwbep/if_cp_expand_node.

  lo_expand_node_root = lo_read_list_request->create_expand_node( ).
  lo_expand_node = lo_expand_node_root->add_expand( ‘team_2_manager’ ).
  lo_expand_node->set_select_properties( VALUE #( ( CONV #( ‘id’ ) ) ) ).
```

> ### Note:  
> See the chapter about reading an entity list for further details about how to create a read list request instance.

> ### Note:  
> It is not necessary any more to explicitly set the expand node into the request; method SET\_EXPAND is obsolete.

**Step 1:** Create the root expand node on the request instance:

```

  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_expand_node_root  TYPE REF TO /iwbep/if_cp_expand_node.

  lo_expand_node_root = lo_read_list_request->create_expand_node( ).
```

**Step 2:** Add the expand path by using the **internal** name of the navigation property \(“TEAM\_2\_MANAGER”\). This will create a new expand node:

```

  DATA: lo_expand_node_root TYPE REF TO /iwbep/if_cp_expand_node,
        lo_expand_node      TYPE REF TO /iwbep/if_cp_expand_node.

  lo_expand_node = lo_expand_node_root->add_expand( ‘team_2_manager’ ).
```

**Step 3:** Set the selected properties \(using **internal** names\) on the select node. “ID” is the internal name of property “Id”:

```

  DATA: lo_expand_node TYPE REF TO /iwbep/if_cp_expand_node.

  lo_expand_node->set_select_properties( VALUE #( ( CONV #( ‘id’ ) ) ) ).
```

