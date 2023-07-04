<!-- loio9dff06d2e0e14afba17d56953d1ad9a6 -->

# OData Request: Delta Link Query Option

Create an OData request with $delta token query option in the Client Proxy instance.



<a name="loio9dff06d2e0e14afba17d56953d1ad9a6__section_jsp_4rg_rtb"/>

## OData Specification



### OData Version 4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html).

Delta links are service-generated links the client uses to access newly created, updated, or deleted entities without a full read of the target resource with every request.

Delta links are based on a defining query that tracks the changes of the set of results. For example, the request that generated the results containing the delta link. The delta link encodes the entity collection that tracks the changes. Also, it includes a starting point to begin track changes.



<a name="loio9dff06d2e0e14afba17d56953d1ad9a6__section_myv_vrg_rtb"/>

## Example Requests



### Version 4

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_tech/0001/PagedDeltaEntities?$deltatoken=20170612000000
```



<a name="loio9dff06d2e0e14afba17d56953d1ad9a6__section_rr4_4sg_rtb"/>

## Delta Link Query Request



### Overview

The starting point for a delta link in the Client Proxy instance is either a Client Proxy instance or a read list request instance \(depending on your use case\).



### Example 1: Create a new delta link

You ran a read list request in the Client Proxy instance and you want to save a delta link for this response, so you can track future changes to the current response:

**Step 1:** Save the current response as delta link \(in this example under the name ‘`DELTA_LINK_NAME`’\):

```

  DATA: lo_read_list_response TYPE REF TO /iwbep/if_cp_response_read_lst.

  lo_read_list_response->save_delta_link ( ‘delta_link_name’ ).
```



### Example 2: Create a delta request from an existing delta link

You have an existing delta link and want to use it to create a delta request:

```

  DATA: lo_client_proxy       TYPE REF TO /iwbep/if_cp_client_proxy,
        lo_delta_read_request TYPE REF TO /iwbep/if_cp_request_read_dlta,
        lo_read_list_response TYPE REF TO /iwbep/if_cp_response_read_lst.


  CHECK lo_client_proxy->does_delta_link_exist( ‘delta_link_name’ ) = abap_true.
  CHECK lo_client_proxy->can_delta_request_be_created( ‘delta_link_name’ ) = abap_true.

  lo_delta_read_request = lo_client_proxy->create_request_for_delta( ‘delta_link_name’ ).
  lo_read_list_response = lo_delta_read_request->execute( ).
```



### Steps

**Step 1:** Check that the delta link:

-   does exist \(in this example, ‘`DELTA_LINK_NAME`’\).
-   can be used to create a delta request. If the stored delta link was manually changed, the delta link can't be used\).

```

  DATA: lo_client_proxy       TYPE REF TO /iwbep/if_cp_client_proxy,
        lo_delta_read_request TYPE REF TO /iwbep/if_cp_request_read_dlta,
        lo_read_list_response TYPE REF TO /iwbep/if_cp_response_read_lst.

  CHECK lo_client_proxy->does_delta_link_exist( ‘delta_link_name’ ) = abap_true.
  CHECK lo_client_proxy->can_delta_request_be_created( ‘delta_link_name’ ) = abap_true.
```

> ### Note:  
> You can only find and use delta links that you created.

**Step 2:** Use the stored delta link to create a delta link request instance:

```

  DATA: lo_client_proxy       TYPE REF TO /iwbep/if_cp_client_proxy,
        lo_delta_read_request TYPE REF TO /iwbep/if_cp_request_read_dlta.

  lo_delta_read_request = lo_client_proxy->create_request_for_delta( ‘delta_link_name’ ).
```

**Step 3:** Run the delta link request and fetch the corresponding response instance:

```

  DATA: lo_delta_read_request TYPE REF TO /iwbep/if_cp_request_read_dlta,
        lo_read_list_response TYPE REF TO /iwbep/if_cp_response_read_lst.

  lo_read_list_response = lo_delta_read_request->execute( ).
```



### Example 3: Insert an existing delta link into an existing request

You have an existing request and want to use it in combination with an existing delta link:

```

  DATA: lo_client_proxy       TYPE REF TO /iwbep/if_cp_client_proxy,
        lo_read_list_request  TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_read_list_response TYPE REF TO /iwbep/if_cp_response_read_lst.


  CHECK lo_client_proxy->does_delta_link_exist( ‘delta_link_name’ ) = abap_true.
  CHECK lo_client_proxy->can_delta_request_be_created( ‘delta_link_name’ ) = abap_false.

  lo_read_list_request->use_delta_link( ‘delta_link_name’ ).
  lo_read_list_response = lo_read_list_request->execute( ).
```



### Steps

**Step 1:** Check that the delta link:

-   does exist \(in this example, ‘`DELTA_LINK_NAME`’\).
-   can be used to create a delta request. If it can be used to create a delta request, you use method `CREATE_REQUEST_FOR_DELTA`, in example 2.

```

DATA: lo_client_proxy TYPE REF TO /iwbep/if_cp_client_proxy.

CHECK lo_client_proxy->does_delta_link_exist( ‘DELTA_LINK_NAME’ ) = abap_true.
CHECK lo_client_proxy->can_delta_request_be_created( ‘DELTA_LINK_NAME’ ) = abap_false.
```

> ### Note:  
> You can only find and use delta links that you created.

**Step 2:** Insert the delta link into the existing read list request:

```


  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list.

  lo_read_list_request->use_delta_link( ‘delta_link_name’ ).
```

**Step 3:** Get the read list response instance using the read list request

```

  DATA: lo_read_list_request  TYPE REF TO /iwbep/if_cp_request_read_list,

        lo_read_list_response TYPE REF TO /iwbep/if_cp_response_read_lst.

  lo_read_list_response = lo_read_list_request->execute( ).
```

**Related Information**  


[OData Request Terms](odata-request-terms-a3b0e95.md "An overview of some OData Request terminology.")

[OData Request: Read Entity List](odata-request-read-entity-list-b810028.md "Create an OData request to read an entity list (entity collection) in the Client Proxy instance.")

[Client Proxy Instance Types](client-proxy-instance-types-079517f.md "Create remote and local Client Proxy instances in OData Version 2 or Version 4.")

