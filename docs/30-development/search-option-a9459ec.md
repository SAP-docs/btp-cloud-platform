<!-- loioa9459ec8a4674e1c9ef6c0370fc8de0d -->

# $search Option

Use the $search system query option to restrict results to include items you specify in the expression..



<a name="loioa9459ec8a4674e1c9ef6c0370fc8de0d__section_qcc_w4v_5tb"/>

## OData Specification



### OData Version 4

See [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata).

The `$search` system query option restricts the result to include only the items that match the specified search expression. The type of match depends on your implementation.



<a name="loioa9459ec8a4674e1c9ef6c0370fc8de0d__section_oty_fpv_5tb"/>

## Example Requests



### Version 4

Get all entities of Entity Set “`Employees`” with “`Peter`” or “`Smith`” in their name:

```
GET/sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/EMPLOYEES?$search=Peter OR Smith
```



<a name="loioa9459ec8a4674e1c9ef6c0370fc8de0d__section_o5r_lpv_5tb"/>

## $search System Query Option



### Overview

The starting point for a request with the `$search` option is an entity list read request. You can set the`$search` expression on the entity list read request.

> ### Note:  
> Depending on your implementation, the result of the `$search` option on a property can vary. In our example, `$search` acts on property “`Name`”.



### Example

Search all entities of Entity Set “`Employees`” with “`Peter`” or “`Smith`” in their name:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/EMPLOYEES?$search=Peter OR Smith 
```



### Steps: Option 1

**Step 1:** Set the search expression at the request instance:

```

  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list.

  lo_read_list_request->set_search( ‘Peter OR Smith’ ).
```

> ### Note:  
> This approach is only supported for remote consumption, not for local consumption



### Steps: Option 2

```

  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_search_node       TYPE REF TO /iwbep/if_cp_search_node.

  lo_search_node = lo_read_list_request->create_search_node( ‘Peter’ ).
  lo_search_node->or( ‘Smith’ ).
  lo_read_list_request->set_search_node( lo_search_node ).
```

**Step 1:** Create the search node on the request instance. For this step, you already provided the first part of your `$search` expression \(“`Peter`” from “`Peter OR Smith`”\):

```

  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_search_node       TYPE REF TO /iwbep/if_cp_search_node.

  lo_search_node = lo_read_list_request->create_search_node( ‘Peter’ ).
```

**Step 2:** Insert the second expression \(“`Smith`”\) and connect it with “`OR`” to the first expression:

```

  DATA: lo_search_node TYPE REF TO /iwbep/if_cp_search_node.

lo_search_node->or( ‘Smith’ ).
```

**Step 3:** Set the search node in the request:

```

  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_search_node       TYPE REF TO /iwbep/if_cp_search_node.

  lo_read_list_request->set_search_node( lo_search_node ).
```



### Negation

Negate the previous expression. For example, this request:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/EMPLOYEES?$search=NOT (Peter OR Smith)
```

Call the method "`NOT`" on the search node instance:

```

  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_search_node       TYPE REF TO /iwbep/if_cp_search_node.

  lo_search_node = lo_read_list_request->create_search_node( ‘Peter’ ).
  lo_search_node->or( ‘Smith’ ).
  lo_search_node->not( ).
  lo_read_list_request->set_search_node( lo_search_node ).
```



### Connect Two Search Nodes

You can connect two search nodes. For example, this request:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/EMPLOYEES?$search=(Peter OR Smith) AND (John AND Mary)
```

```

  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_search_node_1     TYPE REF TO /iwbep/if_cp_search_node,
        lo_search_node_2     TYPE REF TO /iwbep/if_cp_search_node.

  lo_search_node_1 = lo_read_list_request->create_search_node( ‘Peter’ ).
  lo_search_node_1->or( ‘Smith’ ).
  lo_search_node_2 = lo_read_list_request->create_search_node( ‘John’ ).
  lo_search_node_2->and( ‘Mary’ ).
  lo_search_node_1->and_node( lo_search_node_2 ).
  lo_read_list_request->set_search_node( lo_search_node_1 ).
```



<a name="loioa9459ec8a4674e1c9ef6c0370fc8de0d__section_skp_jsv_5tb"/>

## Constraints

-   `$search` is only available for OData Version 4 requests.

-   `SET_SEARCH` is not supported for local consumption.


**Related Information**  


[OData Request Terms](odata-request-terms-a3b0e95.md "An overview of some OData Request terminology.")

[OData Request: Create Entity](odata-request-create-entity-56be82d.md "Create an entity in the Client Proxy instance with insert entity request.")

[OData Request: Read Entity](odata-request-read-entity-9d7dde4.md "To create an OData request to read an entity in the Client Proxy instance.")

