<!-- loio896d90e2a1384cfdb29b2607fd1a9108 -->

# Handling Exceptions

Handling exceptions when running Client Proxy-related coding.



<a name="loio896d90e2a1384cfdb29b2607fd1a9108__section_kyp_s5w_stb"/>

## Overview

There are two types of exceptions in the Client Proxy context:

-   `/IWBEP/CX_GATEWAY`: for client issues \(for example, if the provided entity set name is unknown or if you try to fetch business data from a response instance that doesn't have any response data\).
-   `/IWBEP/CX_CP_REMOTE`: for server issues in remote scenarios \(for example, the returned HTTP status code is not `2xx` \(internal server errors \[500\] or missing authorizations \[401\]\).

    The remote server exception contains this information:

    -   HTTP Status Code

    -   HTTP Status Reason Message

    -   OData Error Details

    -   HTTP Client Error Details

    -   HTTP error body

    -   Content type

    -   HTTP method





<a name="loio896d90e2a1384cfdb29b2607fd1a9108__section_i1q_nvw_stb"/>

## Handling Exceptions



### Overview

For the **remote** client proxy: always catch both exceptions \(`/IWBEP/CX_GATEWAY` and `/IWBEP/CX_CP_REMOTE`\) separately and implement corresponding exception handling.

For the **local** client proxy: catch `/IWBEP/CX_GATEWAY`. The remote exception isn't raised in the local scenario.



### Example

Use remote client proxy to consume an OData request. Include proper exception handling in your coding:

```

  DATA: lv_http_status_code    TYPE /iwbep/cx_gateway=>ty_http_status_code,
        lv_http_status_message TYPE string,
        lv_error_body          TYPE string,
        ls_odata_error         TYPE /iwbep/cx_cp_remote=>ty_s_odata_error,
        lv_client_error_text   TYPE string,
        lx_remote              TYPE REF TO /iwbep/cx_cp_remote,
        lx_gateway             TYPE REF TO /iwbep/cx_gateway.

  TRY.

      “Your Client Proxy Coding
      catch /iwbep/cx_cp_remote into lx_remote.
      lv_http_status_code = lx_remote->http_status_code.
      lv_http_status_message = lx_remote->http_status_message.
      lv_error_body = lx_remote->http_error_body.
      ls_odata_error = lx_remote->s_odata_error.

      “Further error handling
      catch /iwbep/cx_gateway into lx_gateway.
      lv_client_error_text = lx_gateway->get_text( ).

      “Further error handling
      ...
```



### Steps

**Step 1:** Catch the remote exception and fetch the information on the exception \(in addition to your own exception handling\):

```

  DATA: lv_http_status_code    TYPE /iwbep/cx_gateway=>ty_http_status_code,
        lv_http_status_message TYPE string,
        lv_error_body          TYPE string,
        ls_odata_error         TYPE /iwbep/cx_cp_remote=>ty_s_odata_error,
        lx_remote              TYPE REF TO /iwbep/cx_cp_remote.

  CATCH /iwbep/cx_cp_remote INTO lx_remote.

  lv_http_status_code = lx_remote->http_status_code.
  lv_http_status_message = lx_remote->http_status_message.
  lv_error_body = lx_remote->http_error_body.
  ls_odata_error = lx_remote->s_odata_error.

  “Further error handling
  ...
```

**Step 2:** Catch the gateway exception and fetch the corresponding error text \(in addition to your own exception handling\):

```

  DATA: lx_gateway           TYPE REF TO /iwbep/cx_gateway,
        lv_client_error_text TYPE string.


CATCH /iwbep/cx_gateway INTO lx_gateway.
  lv_client_error_text = lx_gateway->get_text( ).

  “Further error handling
   ...

```

