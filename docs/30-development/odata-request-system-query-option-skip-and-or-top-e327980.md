<!-- loioe3279805db7e48c99b24b4e53fe9cec5 -->

# OData Request: System Query Option $skip and/or $top

You want to execute an OData request using the system query options $skip and/or $top within the Client Proxy.



<a name="loioe3279805db7e48c99b24b4e53fe9cec5__section_j5h_j1d_vtb"/>

## OData Specification



### OData V2

See also: [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata)

A data service URI with a $skip System Query Option identifies a subset of the entities in the collection of entities identified by the Resource Path section of the URI. That subset is defined by seeking N entities into the collection and selecting only the remaining entities \(starting with entity N+1\). N is a positive integer specified by this query option.

A data service URI with a $top System Query Option identifies a subset of the entities in the collection of entities, identified by the Resource Path section of the URI. This subset is formed by selecting only the first N items of the set, where N is a positive integer specified by this query option.



### OData V4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html)

The $top system query option specifies a non-negative integer n that limits the number of items returned from a collection. The service returns the number of available items up to but not greater than the specified value n.

The $skip system query option specifies a non-negative integer n that excludes the first n items of the queried collection from the result. The service returns items starting at position n+1.



<a name="loioe3279805db7e48c99b24b4e53fe9cec5__section_k5h_j1d_vtb"/>

## Example Requests



### V4

Skip the first entity in entity set “TEAMS” and get the following two ones:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Teams?$skip=1&$top=2
```



### V2

Skip the first entity in entity set “Managers” and get the following two ones:

```
GET /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Managers?$skip=1&$top=2
```



<a name="loioe3279805db7e48c99b24b4e53fe9cec5__section_l5h_j1d_vtb"/>

## How-To



### Overview

> ### Note:  
> As the coding itself is independent of the OData version, we will just present general examples on how to use $count.

Starting point for a request with $skip and/or $top is an entity list read request. Kindly check e.g. the chapter about reading an entity list on how to create an entity list read request instance. On the entity list read request, it is possible to set both the $skip as well as the $top.



### Example

You want to skip the first entity in entity set “TEAMS” and get the following two ones:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Teams?$skip=1&$top=2
```



### Step-by-step

```

  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list.

        lo_read_list_request->set_skip( 1 ).
        lo_read_list_request->set_top( 2 ).
```

> ### Note:  
> See the chapter about reading an entity list for further details about how to create a read list request instance.

**Step 1:** Set the $skip value at the request instance:

```

 DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list.

 lo_read_list_request->set_skip( 1 ).
```

**Step 2:** Set the $top value at the request instance:

```

  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list.

        lo_read_list_request->set_top( 2 ).
```

