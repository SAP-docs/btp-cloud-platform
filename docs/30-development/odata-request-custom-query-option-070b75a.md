<!-- loio070b75a800854687b774b3c8ddb85b66 -->

# OData Request: Custom Query Option

You want to execute an OData request using a custom query option \(i.e. a query option that is none of the OData-defined system query option\) within the Client Proxy.



<a name="loio070b75a800854687b774b3c8ddb85b66__section_n4s_2df_rtb"/>

## OData Specification



### OData V2

See also: [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata)

Custom Query Options provide an extensible mechanism for data service-specific information to be placed in a data service URI query string.



### OData V4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html)

Services may support additional custom query options not defined in the OData specification, but they MUST NOT begin with the "$" or "@" character and MUST NOT conflict with any OData-defined system query options defined in the OData version supported by the service.



<a name="loio070b75a800854687b774b3c8ddb85b66__section_fxj_zdf_rtb"/>

## Example Requests



### V4

Use custom query option “sap-statistics”:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Teams?sap-statistics=true
```



### V2

Use custom query option “sap-statistics”:

```
GET /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Prices?sap-statistics=true
```



<a name="loio070b75a800854687b774b3c8ddb85b66__section_h5p_pff_rtb"/>

## How-To



### Overview

> ### Note:  
> As the coding itself is independent of the OData version, we will just present general examples on how to use $count.

Starting point for a request with a custom query option is an entity list read request. Kindly check e.g. the chapter about reading an entity list on how to create an entity list read request instance. On the entity list read request, it is possible to set a custom query option.



### Example

You want to use custom query option “sap-statistics”

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Teams?sap-statistics=true
```

```

  DATA: lo_read_list_request     TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_http_client           TYPE REF TO if_http_client,
        lv_sap_statistics_result TYPE string.


  lo_read_list_request->set_custom_query_options( VALUE #( ( name = ‘sap-statistics’ value = ‘true’ ) ) ).
  lo_read_list_request->execute( ).
  lv_sap_statistics_result = lo_http_client->response->get_header_field( name = ‘sap-statistics’ ).
```



### Step-by-step

**Step 1:** Set the custom query option directly at the request instance:

```

  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list.

  lo_read_list_request->set_custom_query_options( VALUE #( ( name = ‘sap-statistics’ value = ‘true’ ) ) ).
```

> ### Note:  
> See the chapter about reading an entity list for further details about how to create a read list request instance.

**Step 2:** Execute the read request and fetch the sap statistics result from the HTTP client instance:

```

  DATA: lo_read_list_request     TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_http_client           TYPE REF TO if_http_client,
        lv_sap_statistics_result TYPE string.

  lo_read_list_request->execute( ).
  lv_sap_statistics_result = lo_http_client->response->get_header_field( name = ‘sap-statistics’ ).
```

> ### Note:  
> lo\_http\_client must be the **same** HTTP client instance that was used for creating the Client Proxy \(see the chapter about how to create a Client Proxy instance.



<a name="loio070b75a800854687b774b3c8ddb85b66__section_b5w_yhf_rtb"/>

## Constraints

-   Independently of the OData version of the client proxy, input MUST conform with the \(stricter\) OData v4 specification

-   Custom Query Options can only be used for remote consumption; they are not supported in local consumption scenarios


