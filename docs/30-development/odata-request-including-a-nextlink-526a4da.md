<!-- loio526a4da8ff9e469f9e31803119693cb5 -->

# OData Request: Including a Nextlink

You want to execute an OData request to read an entity list \(a.k.a. an entity collection\) including a next link using the Client Proxy.



<a name="loio526a4da8ff9e469f9e31803119693cb5__section_vxg_3g2_ttb"/>

## OData Specification



### OData V4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html)

Responses that include only a partial set of the items identified by the request URL MUST contain a link that allows retrieving the next partial set of items. This link is called a next link; its representation is format-specific. The final partial set of items MUST NOT contain a next link.



<a name="loio526a4da8ff9e469f9e31803119693cb5__section_x5s_532_ttb"/>

## How-To



### Overview

Starting point for using the next link within the Client Proxy is a read list response instance. Kindly refer to the corresponding chapter about reading an entity list for further details on how to create a read list response instance.



### Example

You have executed a read list request using the Client Proxy and want to handle possible next links:

```

  DATA: lo_read_list_response TYPE REF TO /iwbep/if_cp_response_read_lst,
        lt_employee           TYPE STANDARD TABLE OF /iwbep/s_v4_tea_employee.


  lo_read_list_response->get_business_data( IMPORTING et_business_data = lt_employee ).

  WHILE lo_read_list_response->has_next( ).
    lo_read_response = lo_read_response->get_next( ).
    lo_read_list_response->get_business_data( IMPORTING et_business_data = lt_employee ).
  ENDWHILE.
```



### Step-by-step

**Step 1:**You fetch the first batch of entities from the read list response instance:

```

  DATA: lo_read_list_response TYPE REF TO /iwbep/if_cp_response_read_lst,
        lt_employee           TYPE STANDARD TABLE OF /iwbep/s_v4_tea_employee.

  lo_read_list_response->get_business_data( IMPORTING et_business_data = lt_employee ).
```

**Step 2:** As long as there is still a next links \(checked via method HAS\_NEXT on the response instance\), you can fetch the next batch of entities. To do so, get the corresponding response instance by calling GET\_NEXT method on the previous response instance and get the business data from this new instance:

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



-   Next links are only supported for OData V4 requests

-   Next links are only supported for remote consumption


