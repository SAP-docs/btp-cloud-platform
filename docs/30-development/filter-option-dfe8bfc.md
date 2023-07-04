<!-- loiodfe8bfca9b5c4792859480d224f4403a -->

# $filter Option

Use the $filter system query option to restrict the returned set of items.



<a name="loiodfe8bfca9b5c4792859480d224f4403a__section_rcf_g2x_stb"/>

## OData Specification



### OData Version 2

See also: [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata).

A data service URI with a `$filter` System Query Option identifies a subset of the entities in the EntitySet \(identified by the Resource Path section of the URI\) by only selecting the entities that meet the predicate expression the query option specifies.



### OData Version 4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html).

The `$filter` system query option restricts the set of items that are returned.



<a name="loiodfe8bfca9b5c4792859480d224f4403a__section_tb2_4fx_stb"/>

## Example Requests



### Version 4

Get the entities in entity set “`Employees`” that have the Id “`0006`” and the Postalcode “`69190`”:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees?$filter=Location/City/Postalcode eq '69190' and Id eq '0006'
```



### Version 2

Get the entities in entity set “`Employees`” with the Id “`0006`” and the PostalCode “`69190`”:

```
GET /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Employees?$filter=Location/City/PostalCode eq '69190' and Id eq '0006'
```



<a name="loiodfe8bfca9b5c4792859480d224f4403a__section_ucv_4pd_ttb"/>

## $filter System Query Option



### Overview

> ### Note:  
> As the coding is independent of the OData version, we're presenting a general example on how to use the `$filter` option.

The starting point for a request with the `$filter` option is an entity list read request.



### Example

Get all entities from the entity set “`Buildings`” with the BuildingID “`ROT05`” and Cityname is not “`Walldorf`”:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Buildings?$filter=Location/City/Cityname ne 'Walldorf' and BuildingID eq 'ROT05'
```



### Steps

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

**Step 1:** Create an instance of the filter factory at the read list request instance:

```

  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_filter_factory    TYPE REF TO /iwbep/if_cp_filter_factory.

  lo_filter_factory = lo_read_list_request->create_filter_factory( ).
```

**Step 2:** Create a filter node for the first filter expression \(`Location/City/Cityname ne 'Walldorf'` \). We define the new values and set the business data to the request:


<table>
<tr>
<th valign="top">

Properties



</th>
<th valign="top">

Internal Names



</th>
</tr>
<tr>
<td valign="top">

Cityname



</td>
<td valign="top">

CITYNAME



</td>
</tr>
<tr>
<td valign="top">

Location



</td>
<td valign="top">

LOCATION



</td>
</tr>
<tr>
<td valign="top">

City



</td>
<td valign="top">

CITY



</td>
</tr>
</table>

The filter expression must be expressed in a range:

```

  DATA: lt_range          TYPE RANGE OF string,
        lo_filter_factory TYPE REF TO /iwbep/if_cp_filter_factory,
        lo_filter_node_1  TYPE REF TO /iwbep/if_cp_filter_node.

  lo_filter_factory = lo_read_list_request->create_filter_factory( ).

  lt_range = VALUE #( ( option = ‘ne’ sign = ‘i’ low = ‘Walldorf’ ) ).

  lo_filter_node_1 = lo_filter_factory->create_by_range( iv_property_path = ‘location-city-cityname‘
                                                         it_range = lt_range                        ).
```

**Step 3:** Create a filter node for the second filter expression `BuildingID`' `ROT05'`. The internal name of the primitive property “`BuildingID`” is “`BUILDING_ID`”. The filter expression must be expressed in a range:

```

  DATA: lt_range          TYPE RANGE OF string,
        lo_filter_factory TYPE REF TO /iwbep/if_cp_filter_factory,
        lo_filter_node_2  TYPE REF TO /iwbep/if_cp_filter_node.

  lt_range = VALUE #( ( option = ‘eq’ sign = ‘i’ low = ‘rot05’ ) ).

  lo_filter_node_2 = lo_filter_factory->create_by_range( iv_property_path = ‘building_id‘
                                                         it_range = lt_range              ).
```

**Step 4:**Connect the two filter nodes with "`and`" in the final filter node:

```

  DATA: lo_filter_node_1     TYPE REF TO /iwbep/if_cp_filter_node,
        lo_filter_node_2     TYPE REF TO /iwbep/if_cp_filter_node,
        lo_filter_node_final TYPE REF TO /iwbep/if_cp_filter_node.

  lo_filter_node_final = lo_filter_node_1->and( lo_filter_node_2 ).
```

**Step 5:** Set the final `filter` node in the request instance:

```

  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_filter_node_final TYPE REF TO /iwbep/if_cp_filter_node.

  lo_read_list_request->set_filter( lo_filter_node_final ).
```



### Negation

To use negation call the `NOT` method on a `filter` node instance \(for example, `$filter=not`\(`BuildingID` is '`WDF03`'\). This step creates a new filter node \(the negated filter node\):

```

  DATA: lo_filter_node     TYPE REF TO /iwbep/if_cp_filter_node,
        lo_filter_node_not TYPE REF TO /iwbep/if_cp_filter_node.

  lo_filter_node_not = lo_filter_node->not( ).
```



<a name="loiodfe8bfca9b5c4792859480d224f4403a__section_wtc_p5d_ttb"/>

## Constraints

-   `$filter` is only supported for primitive and complex properties.

-   Only these range options are allowed: `EQ`, `NE`, `GT`, `GE`, `LT`, and `LE`.

-   Only range signs “`I`” and “`E`” are allowed.

-   Conversions with range option “`CP`” are not allowed.

-   Only these functions can be used with `CP`: `startswith`, `endswith`, and `substringof` \(for OData Version 2\), `contains` \(for OData Version 4\).

-   Not all filter expression are supported for local consumption.

-   The currency code must be provided when the addressed property has a reference to a currency property.

-   The unit of measurement must be provided when the addressed property has a reference to a unit property
-   You can't set a `$filter` for an `$expand`.

    ```
    GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/TEAMS?$expand=TEAM_2_EMPLOYEES($filter=AGE eq 56)
    ```


**Related Information**  


[OData Request Terms](odata-request-terms-a3b0e95.md "An overview of some OData Request terminology.")

[OData Request: Create Entity](odata-request-create-entity-56be82d.md "Create an entity in the Client Proxy instance with insert entity request.")

[OData Request: Read Entity](odata-request-read-entity-9d7dde4.md "To create an OData request to read an entity in the Client Proxy instance.")

