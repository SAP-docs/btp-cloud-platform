<!-- loioa9459ec8a4674e1c9ef6c0370fc8de0d -->

# OData Request: System Query Option $search

You want to execute an OData request using the system query option $search within the Client Proxy.



<a name="loioa9459ec8a4674e1c9ef6c0370fc8de0d__section_qcc_w4v_5tb"/>

## OData Specification



### OData V4

See also: [Data Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html)

The $search system query option restricts the result to include only those items matching the specified search expression. The definition of what it means to match is dependent upon the implementation.



<a name="loioa9459ec8a4674e1c9ef6c0370fc8de0d__section_oty_fpv_5tb"/>

## Example Requests



### V4

Get all entities of Entity Set “Employees” with “Peter” or “Smith” in their name:

```
GET/sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/EMPLOYEES?$search=Peter OR Smith
```



<a name="loioa9459ec8a4674e1c9ef6c0370fc8de0d__section_o5r_lpv_5tb"/>

## How-To



### Overview

Starting point for a request with $search is an entity list read request. Kindly check e.g. the chapter about reading an entity list on how to create an entity list read request instance. On the entity list read request, it is possible to set the $search expression.

> ### Note:  
> It depends on the underlying implementation on which property the $search acts upon. In our example, $search acts on property “Name”.



### Example

You want to all entities of Entity Set “Employees” with “Peter” or “Smith” in their name:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/EMPLOYEES?$search=Peter OR Smith 
```



### Step-by-step – Option 1

**Step 1:** Set the search expression at the request instance:

```

  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list.

  lo_read_list_request->set_search( ‘Peter OR Smith’ ).
```

> ### Note:  
> This approach is only supported for remote consumption, not for local consumption!

> ### Note:  
> See the chapter about reading an entity list for further details about how to create a read list request instance.



### Step-by-step – Option 2

```

  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_search_node       TYPE REF TO /iwbep/if_cp_search_node.

  lo_search_node = lo_read_list_request->create_search_node( ‘Peter’ ).
  lo_search_node->or( ‘Smith’ ).
  lo_read_list_request->set_search_node( lo_search_node ).
```

> ### Note:  
> See the chapter about reading an entity list for further details about how to create a read list request instance.

**Step 1:** Create the search node on the request instance. For this, you already provide the first part of your $search expression \(here: “Peter” from “Peter OR Smith”\):

```

  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_search_node       TYPE REF TO /iwbep/if_cp_search_node.

  lo_search_node = lo_read_list_request->create_search_node( ‘Peter’ ).
```

**Step 2:** Insert the second expression \(“Smith”\) and connect it via “OR” to the first expression:

```

  DATA: lo_search_node TYPE REF TO /iwbep/if_cp_search_node.

lo_search_node->or( ‘Smith’ ).
```

**Step 3:** Set the search node into the request:

```

  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_search_node       TYPE REF TO /iwbep/if_cp_search_node.

  lo_read_list_request->set_search_node( lo_search_node ).
```



### Negation

Negation of the above expression, i.e. the following request:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/EMPLOYEES?$search=NOT (Peter OR Smith)
```

This can be done by calling method NOT on the search node instance:

```

  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_search_node       TYPE REF TO /iwbep/if_cp_search_node.

  lo_search_node = lo_read_list_request->create_search_node( ‘Peter’ ).
  lo_search_node->or( ‘Smith’ ).
  lo_search_node->not( ).
  lo_read_list_request->set_search_node( lo_search_node ).
```



### Connection of two search nodes

It is also possible to connect two search nodes. Consider e.g. the request

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

-   $search is only available for OData V4 requests

-   SET\_SEARCH is not supported for local consumption


