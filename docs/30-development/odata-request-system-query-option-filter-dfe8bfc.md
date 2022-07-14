<!-- loiodfe8bfca9b5c4792859480d224f4403a -->

# OData Request: System Query Option $filter

You want to execute an OData request using the system query option $filter within the Client Proxy.



<a name="loiodfe8bfca9b5c4792859480d224f4403a__section_rcf_g2x_stb"/>

## OData Specification



### OData V2

See also: [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata)

A data service URI with a $filter System Query Option identifies a subset of the entities in the EntitySet, identified by the Resource Path section of the URI, by only selecting the entities that satisfy the predicate expression specified by the query option.



### OData V4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html)

The `$filter` system query option restricts the set of items returned.



<a name="loiodfe8bfca9b5c4792859480d224f4403a__section_tb2_4fx_stb"/>

## Example Requests



### V4

Get the entities in entity set “Employees” that have the Id “0006” and the Postalcode “69190”:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees?$filter=Location/City/Postalcode eq '69190' and Id eq '0006'
```



### V2

Get the entities in entity set “Employees” that have the Id “0006” and the PostalCode “69190”:

```
GET /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Employees?$filter=Location/City/PostalCode eq '69190' and Id eq '0006'
```



<a name="loiodfe8bfca9b5c4792859480d224f4403a__section_ucv_4pd_ttb"/>

## How-To



### Overview

> ### Note:  
> As the coding itself is independent of the OData version, we will just present general examples on how to use $filter.

Starting point for a request with $filter is an entity list read request. Kindly check e.g. the chapter about reading an entity list on how to create an entity list read request instance. On the entity list read request, it is possible to create a filter factory instance, which can be used to create a filter node instance. Kindly refer to the corresponding chapter for further details about the filter node. The filter node can then be set into the request.



### Example

You want to get all entities of entity set “Buildings” that have the BuildingID “ROT05” and whose Cityname is not “Walldorf”:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Buildings?$filter=Location/City/Cityname ne 'Walldorf' and BuildingID eq 'ROT05'
```



### Step-by-step

```

  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list,
        lt_range             TYPE RANGE OF string,
        lo_filter_factory    TYPE REF TO /iwbep/if_cp_filter_factory,
        lo_filter_node_1     TYPE REF TO /iwbep/if_cp_filter_node,
        lo_filter_node_2     TYPE REF TO /iwbep/if_cp_filter_node,
        lo_filter_node_final TYPE REF TO /iwbep/if_cp_filter_node.


  lo_filter_factory = lo_read_list_request->create_filter_factory( ).

  lt_range = VALUE #( ( option = ‘ne’ sign = ‘i’ low = ‘Walldorf’ ) ).

  lo_filter_node_1 = lo_filter_factory->create_by_range( iv_property_path = ‘location-city-cityname‘
                                                         it_range = lt_range ).


  lt_range = VALUE #( ( option = ‘eq’ sign = ‘i’ low = ‘rot05’ ) ).

  lo_filter_node_2 = lo_filter_factory->create_by_range( iv_property_path = ‘building_id‘
                                                         it_range = lt_range ).


  lo_filter_node_final = lo_filter_node_1->and( lo_filter_node_2 ).
  lo_read_list_request->set_filter( lo_filter_node_final ).
.
```

> ### Note:  
> See the chapter about reading an entity list for further details about how to create a read list request instance.

**Step 1:** Create an instance of the filter factory at the read list request instance:

```

  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_filter_factory    TYPE REF TO /iwbep/if_cp_filter_factory.

  lo_filter_factory = lo_read_list_request->create_filter_factory( ).
```

**Step 2:** Create a filter node for the first filter expression \(`Location/City/Cityname ne 'Walldorf'` \). The internal names of the primitive property “Cityname” and the complex properties “Location” \(which contains “City”\) and “City” \(which contains “Cityname”\) are “CITYNAME”, “LOCATION” and “CITY”. The filter expression has to be expressed via a range:

```

  DATA: lt_range          TYPE RANGE OF string,
        lo_filter_factory TYPE REF TO /iwbep/if_cp_filter_factory,
        lo_filter_node_1  TYPE REF TO /iwbep/if_cp_filter_node.

  lo_filter_factory = lo_read_list_request->create_filter_factory( ).

  lt_range = VALUE #( ( option = ‘ne’ sign = ‘i’ low = ‘Walldorf’ ) ).

  lo_filter_node_1 = lo_filter_factory->create_by_range( iv_property_path = ‘location-city-cityname‘
                                                         it_range = lt_range                        ).
```

**Step 3:** Create a filter node for the second filter expression \( `BuildingID eq 'ROT05'` \). The internal name of the primitive property “BuildingID” is “BUILDING\_ID”. The filter expression has to be expressed via a range:

```

  DATA: lt_range          TYPE RANGE OF string,
        lo_filter_factory TYPE REF TO /iwbep/if_cp_filter_factory,
        lo_filter_node_2  TYPE REF TO /iwbep/if_cp_filter_node.

  lt_range = VALUE #( ( option = ‘eq’ sign = ‘i’ low = ‘rot05’ ) ).

  lo_filter_node_2 = lo_filter_factory->create_by_range( iv_property_path = ‘building_id‘
                                                         it_range = lt_range              ).
```

**Step 4:**Connect the two filter nodes via AND into the final filter node:

```

  DATA: lo_filter_node_1     TYPE REF TO /iwbep/if_cp_filter_node,
        lo_filter_node_2     TYPE REF TO /iwbep/if_cp_filter_node,
        lo_filter_node_final TYPE REF TO /iwbep/if_cp_filter_node.

  lo_filter_node_final = lo_filter_node_1->and( lo_filter_node_2 ).
```

**Step 5:** Set the final filter node into the request instance:

```

  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_filter_node_final TYPE REF TO /iwbep/if_cp_filter_node.

  lo_read_list_request->set_filter( lo_filter_node_final ).
```



### Negation

Negation can be achieved by calling the NOT method on a filter node instance \(for e.g. $filter=not\(BuildingID eq 'WDF03'\)\). This will create a new filter node, the negated filter node:

```

  DATA: lo_filter_node     TYPE REF TO /iwbep/if_cp_filter_node,
        lo_filter_node_not TYPE REF TO /iwbep/if_cp_filter_node.

  lo_filter_node_not = lo_filter_node->not( ).
```



<a name="loiodfe8bfca9b5c4792859480d224f4403a__section_wtc_p5d_ttb"/>

## Constraints

-   $filter is only supported for primitive and complex properties

-   Only EQ, NE, GT, GE, LT, and LE are supported as range option

-   Only range signs “I” and “E” are allowed

-   Conversions in combination with range option “CP” are not allowed

-   Only the following functions can be used in combination with CP: startswith, endswith and substringof \(for OData V2\) / contains \(for OData V4\)

-   Not all filter expression are supported for local consumption

-   If the addressed property has a reference to a currency property, the currency code has to be provided

-   If the addressed property has a reference to a unit property, the Unit of measurement has to be supplied

-   It is not possible to set a $filter for an $expand, i.e.

    ```
    GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/TEAMS?$expand=TEAM_2_EMPLOYEES($filter=AGE eq 56)
    ```


