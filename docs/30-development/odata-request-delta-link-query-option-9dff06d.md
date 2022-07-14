<!-- loio9dff06d2e0e14afba17d56953d1ad9a6 -->

# OData Request: Delta Link Query Option

You want to execute an OData request including query option $deltatoken via the Client Proxy.



<a name="loio9dff06d2e0e14afba17d56953d1ad9a6__section_jsp_4rg_rtb"/>

## OData Specification



### OData V4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html)

Delta links are opaque, service-generated links that the client uses to retrieve subsequent changes to a result.

Delta links are based on a defining query that describes the set of results for which changes are being tracked; for example, the request that generated the results containing the delta link. The delta link encodes the collection of entities for which changes are being tracked, along with a starting point from which to track changes.



<a name="loio9dff06d2e0e14afba17d56953d1ad9a6__section_myv_vrg_rtb"/>

## Example Requests



### V4

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_tech/0001/PagedDeltaEntities?$deltatoken=20170612000000
```



<a name="loio9dff06d2e0e14afba17d56953d1ad9a6__section_rr4_4sg_rtb"/>

## How-To



### Overview

Starting point for using the delta link within the Client Proxy is either a Client Proxy instance or a read list request instance – depending on your use case. Kindly refer to the corresponding chapters for further details on how to create a Client Proxy or a read list request instance.



### Example 1 – Creating a new delta link

You have executed a read list request using the Client Proxy and want to save a delta link for this response, in order to be able to determine the changes to the current response for future requests:

**Step 1:** You save the current response as delta link \(in this example under the name ‘DELTA\_LINK\_NAME’\):

```

  DATA: lo_read_list_response TYPE REF TO /iwbep/if_cp_response_read_lst.

  lo_read_list_response->save_delta_link ( ‘delta_link_name’ ).
```



### Example 2 – Create a delta request from an existing delta link

You have an existing delta link and want to use it to create a corresponding delta request:

```

  DATA: lo_client_proxy       TYPE REF TO /iwbep/if_cp_client_proxy,
        lo_delta_read_request TYPE REF TO /iwbep/if_cp_request_read_dlta,
        lo_read_list_response TYPE REF TO /iwbep/if_cp_response_read_lst.


  CHECK lo_client_proxy->does_delta_link_exist( ‘delta_link_name’ ) = abap_true.
  CHECK lo_client_proxy->can_delta_request_be_created( ‘delta_link_name’ ) = abap_true.

  lo_delta_read_request = lo_client_proxy->create_request_for_delta( ‘delta_link_name’ ).
  lo_read_list_response = lo_delta_read_request->execute( ).
```



### Step-by-step

**Step 1:** You check that a\) the delta link to be used \(here: ‘DELTA\_LINK\_NAME’\) does indeed exist and b\) it can be used to create a delta request. The latter would be false if e.g. the stored delta link was manually changed \(see corresponding section in this chapter\):

```

  DATA: lo_client_proxy       TYPE REF TO /iwbep/if_cp_client_proxy,
        lo_delta_read_request TYPE REF TO /iwbep/if_cp_request_read_dlta,
        lo_read_list_response TYPE REF TO /iwbep/if_cp_response_read_lst.

  CHECK lo_client_proxy->does_delta_link_exist( ‘delta_link_name’ ) = abap_true.
  CHECK lo_client_proxy->can_delta_request_be_created( ‘delta_link_name’ ) = abap_true.
```

> ### Note:  
> You are only able to find and use delta links created by your own user!

**Step 2:** You use the stored delta link to create a delta link request instance:

```

  DATA: lo_client_proxy       TYPE REF TO /iwbep/if_cp_client_proxy,
        lo_delta_read_request TYPE REF TO /iwbep/if_cp_request_read_dlta.

  lo_delta_read_request = lo_client_proxy->create_request_for_delta( ‘delta_link_name’ ).
```

**Step 3:** You execute the delta link request and fetch the corresponding response instance:

```

  DATA: lo_delta_read_request TYPE REF TO /iwbep/if_cp_request_read_dlta,
        lo_read_list_response TYPE REF TO /iwbep/if_cp_response_read_lst.

  lo_read_list_response = lo_delta_read_request->execute( ).
```

> ### Note:  
> See the corresponding chapter about reading an entity list for more details on how to handle read list response instances.



### Example 3 – Inject an existing delta link into an existing request

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



### Step-by-step

**Step 1:** You check that a\) the delta link to be used \(here: ‘DELTA\_LINK\_NAME’\) does indeed exist and b\) it can **not** be used to create a delta request \(if it could be used to create a delta request, you had to use method CREATE\_REQUEST\_FOR\_DELTA, as shown in example 2 above\):

```

DATA: lo_client_proxy TYPE REF TO /iwbep/if_cp_client_proxy.

CHECK lo_client_proxy->does_delta_link_exist( ‘DELTA_LINK_NAME’ ) = abap_true.
CHECK lo_client_proxy->can_delta_request_be_created( ‘DELTA_LINK_NAME’ ) = abap_false.
```

> ### Note:  
> You are only able to find and use delta links created by your own user.

**Step 2:**You inject the delta link into the existing read list request:

```


  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list.

  lo_read_list_request->use_delta_link( ‘delta_link_name’ ).
```

> ### Note:  
> See the corresponding chapter about reading an entity list for more details about creating and using and entity read list request instance.

**Step 3:** You get the read list response instance by executing the read list request

```

  DATA: lo_read_list_request  TYPE REF TO /iwbep/if_cp_request_read_list,

        lo_read_list_response TYPE REF TO /iwbep/if_cp_response_read_lst.

  lo_read_list_response = lo_read_list_request->execute( ).
```

> ### Note:  
> See the corresponding chapter about reading an entity list for more details on how to handle read list response instances.

