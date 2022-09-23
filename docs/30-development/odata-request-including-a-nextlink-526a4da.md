<!-- loio526a4da8ff9e469f9e31803119693cb5 -->

# OData Request: Including a Nextlink

Create an OData request to read an entity list \(entity collection\) with a next link in the Client Proxy instance.



<a name="loio526a4da8ff9e469f9e31803119693cb5__section_vxg_3g2_ttb"/>

## OData Specification



### OData Version 4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html).

In responses that include a partial set of the items identified by the request, the URL MUST include a link \(a next link\) that allows retrieving the next partial set of items.A next link representation is format-specific. The final partial set of items MUST NOT contain a next link.



<a name="loio526a4da8ff9e469f9e31803119693cb5__section_x5s_532_ttb"/>

## Nextlink Request



### Overview

The starting point for a ***next link*** request is the Client Proxy instance, is ***read list*** response instance.



### Example

You created a read list request in the Client Prox instance and want to manage potential next links:

```

  DATA: lo_read_list_response TYPE REF TO /iwbep/if_cp_response_read_lst,
        lt_employee           TYPE STANDARD TABLE OF /iwbep/s_v4_tea_employee.


  lo_read_list_response->get_business_data( IMPORTING et_business_data = lt_employee ).

  WHILE lo_read_list_response->has_next( ).
    lo_read_response = lo_read_response->get_next( ).
    lo_read_list_response->get_business_data( IMPORTING et_business_data = lt_employee ).
  ENDWHILE.
```



### Steps

**Step 1:**Fetch the first batch of entities from the read list response instance:

```

  DATA: lo_read_list_response TYPE REF TO /iwbep/if_cp_response_read_lst,
        lt_employee           TYPE STANDARD TABLE OF /iwbep/s_v4_tea_employee.

  lo_read_list_response->get_business_data( IMPORTING et_business_data = lt_employee ).
```

**Step 2:** Check that there are still next links using the ***HAS\_NEXT*** method on the response instance\). Then you can fetch the next batch of entities. Get the corresponding response instance by using the ***GET\_NEXT*** method on the previous response instance. Then get the business data from this new instance:

```

  DATA: lo_read_list_response TYPE REF TO /iwbep/if_cp_response_read_lst,
        lt_employee           TYPE STANDARD TABLE OF /iwbep/s_v4_tea_employee.


  WHILE lo_read_list_response->has_next( ).
    lo_read_response = lo_read_response->get_next( ).
    lo_read_list_response->get_business_data( IMPORTING et_business_data = lt_employee ).
  ENDWHILE.
```



<a name="loio526a4da8ff9e469f9e31803119693cb5__section_dqy_vj2_ttb"/>

## Constraints



-   Next links are only supported for OData Version 4 requests.

-   Next links are only supported for remote consumption.


**Related Information**  




[OData Request: Read Entity List](odata-request-read-entity-list-b810028.md "Create an OData request to read an entity list (entity collection) in the Client Proxy instance.")

