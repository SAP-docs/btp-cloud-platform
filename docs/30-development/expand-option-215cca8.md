<!-- loio215cca8d5c7c4e27b775271d4cb6e24c -->

# $expand Option

Use the $expand system query option to represent associated EntityType instance or EntitySet inline.



<a name="loio215cca8d5c7c4e27b775271d4cb6e24c__section_dnd_2zw_stb"/>

## OData Specification



### OData Version 2

See [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata).

The ***$expand*** System Query Option indicates that entities associated with the EntityType instance or EntitySet \(identified by the Resource Path section of the URI\) must be represented inline.



### OData Version 4

See [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html).

The ***$expand*** system query option indicates the related entities and stream values that MUST be represented inline. The service MUST return the specified content and can choose to return additional information.

The value of the ***$expand*** query option is a comma-separated list of navigation property names, stream property names, or ***$value*** that indicate the stream content of a media-entity.



<a name="loio215cca8d5c7c4e27b775271d4cb6e24c__section_xgz_b1x_stb"/>

## Example Requests



### Version 4

Get the team ‘***TEAM\_03***’ and its manager with navigation property “***Team2Manager***”:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Teams('TEAM_03')?$expand=Team2Manager
```



### Version 2

Get the manager with id ‘***0004***’ and the information about his team with navigation property “***My\_Team***”:

```
GET /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Managers('0001')?$expand=My_Team
```



<a name="loio215cca8d5c7c4e27b775271d4cb6e24c__section_jg3_41x_stb"/>

## $expand System Query Option



### Overview

> ### Note:  
> As the coding is independent of the OData version, we're presenting a general example on how to use the ***$expand*** option.

The starting point for a request with the ***$expand*** option is an entity list read request. On the entity list read request, you can set the ***$expand*** option.



### Example

Get all entities from the entity set “***Teams***”. For each term, fetch the corresponding manager using the navigation property “***Team2Manager***”. You want to retrieve only the Id of each manager:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Teams?$expand=Team2Manager($select=Id)
```



### Steps

```

  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_expand_node_root  TYPE REF TO /iwbep/if_cp_expand_node,
        lo_expand_node       TYPE REF TO /iwbep/if_cp_expand_node.

  lo_expand_node_root = lo_read_list_request->create_expand_node( ).
  lo_expand_node = lo_expand_node_root->add_expand( ‘team_2_manager’ ).
  lo_expand_node->set_select_properties( VALUE #( ( CONV #( ‘id’ ) ) ) ).
```

> ### Note:  
> The ***SET\_EXPAND*** method is obsolete. It's not necessary to explicitly set the expand node in the request.

**Step 1:** Create the root expand node on the request instance:

```

  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_expand_node_root  TYPE REF TO /iwbep/if_cp_expand_node.

  lo_expand_node_root = lo_read_list_request->create_expand_node( ).
```

**Step 2:** Add the expand path by using the **internal** name of the navigation property \(“***TEAM\_2\_MANAGER***”\). This step creates a new expand node:

```

  DATA: lo_expand_node_root TYPE REF TO /iwbep/if_cp_expand_node,
        lo_expand_node      TYPE REF TO /iwbep/if_cp_expand_node.

  lo_expand_node = lo_expand_node_root->add_expand( ‘team_2_manager’ ).
```

**Step 3:** Set the selected properties \(using **internal** names\) on the select node. “***ID***” is the internal name of property “***Id***”:

```

  DATA: lo_expand_node TYPE REF TO /iwbep/if_cp_expand_node.

  lo_expand_node->set_select_properties( VALUE #( ( CONV #( ‘id’ ) ) ) ).
```

**Related Information**  




[OData Request: Read Entity](odata-request-read-entity-9d7dde4.md "To create an OData request to read an entity in the Client Proxy instance.")

[OData Request: Read Entity List](odata-request-read-entity-list-b810028.md "Create an OData request to read an entity list (entity collection) in the Client Proxy instance.")

