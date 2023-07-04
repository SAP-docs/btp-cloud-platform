<!-- loio070b75a800854687b774b3c8ddb85b66 -->

# OData Request: Custom Query Option

Create an OData request using a custom query option that isn't one of the OData-defined system query options in the Client Proxy instance.



<a name="loio070b75a800854687b774b3c8ddb85b66__section_n4s_2df_rtb"/>

## OData Specification



### OData Version 2

See also: [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata).

Custom Query Options enable you to include data service-specific information in a data service URI query string.



### OData Version 4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html).

Services can support additional custom query options that are not defined in the OData specification. The custom query options:

-   can't begin with the "`$`" or "`@`" character
-   can't conflict with any OData-defined system query options defined in the OData version that the service supports



<a name="loio070b75a800854687b774b3c8ddb85b66__section_fxj_zdf_rtb"/>

## Example Requests



### Version 4

Use custom query option “`sap-statistics`”:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Teams?sap-statistics=true
```



### Version 2

Use custom query option “`sap-statistics`”:

```
GET /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Prices?sap-statistics=true
```



<a name="loio070b75a800854687b774b3c8ddb85b66__section_h5p_pff_rtb"/>

## Custom Query Option Request



### Overview

> ### Note:  
> As the coding is independent of the OData version, we're presenting a general example on how to use `$count`.

The starting point for a custom query option request is an entity list read request. You can set a custom query option on the entity list read request.



### Example

Use custom query option “`sap-statistics`”

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



### Steps

**Step 1:** Set the custom query option directly at the request instance:

```

  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list.

  lo_read_list_request->set_custom_query_options( VALUE #( ( name = ‘sap-statistics’ value = ‘true’ ) ) ).
```

**Step 2:** Run the read request and fetch the sap statistics result from the HTTP client instance:

```

  DATA: lo_read_list_request     TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_http_client           TYPE REF TO if_http_client,
        lv_sap_statistics_result TYPE string.

  lo_read_list_request->execute( ).
  lv_sap_statistics_result = lo_http_client->response->get_header_field( name = ‘sap-statistics’ ).
```

> ### Note:  
> `lo_http_client` must be the **same** HTTP client instance as the one used for creating the Client Proxy.



<a name="loio070b75a800854687b774b3c8ddb85b66__section_b5w_yhf_rtb"/>

## Constraints

-   Regardless of the Client Proxy OData version, input MUST conform with the more stricter OData Version 4 specification.

-   You can only use custom query options for remote consumption. Custom query options are not supported in local consumption scenarios.


**Related Information**  


[OData Request Terms](odata-request-terms-a3b0e95.md "An overview of some OData Request terminology.")

[Client Proxy Instance Types](client-proxy-instance-types-079517f.md "Create remote and local Client Proxy instances in OData Version 2 or Version 4.")

