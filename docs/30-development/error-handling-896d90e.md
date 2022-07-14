<!-- loio896d90e2a1384cfdb29b2607fd1a9108 -->

# Error Handling

In this chapter, we will introduce the different exceptions that might be raised when executing Client Proxy related coding and how to properly react on these.



<a name="loio896d90e2a1384cfdb29b2607fd1a9108__section_kyp_s5w_stb"/>

## Overview

There are two types of exceptions in the Client Proxy context: `/IWBEP/CX_GATEWAY` and `/IWBEP/CX_CP_REMOTE`.

`/IWBEP/CX_GATEWAY` is raised for issues on the Client side, e.g. if the provided entity set name is unknown or if you try to fetch business data from a response instance that does not have any response data.

`/IWBEP/CX_CP_REMOTE` is raised for problems on the Server side, i.e. when the returned HTTP status code is not 2xx \(e.g. in case of internal server errors \[500\] or missing authorizations \[401\] \). This exception is only raised in remote scenarios, i.e. when using the remote Client Proxy. It will not be thrown for local scenarios. If available, this exception will contain the following information:

-   HTTP Status Code

-   HTTP Status Reason Message

-   OData Error Details

-   HTTP Client Error Details

-   HTTP error body

-   Content type

-   HTTP method




<a name="loio896d90e2a1384cfdb29b2607fd1a9108__section_i1q_nvw_stb"/>

## How-To



### Overview

If you are using the remote Client Proxy, it is recommended to always catch both exceptions \(`/IWBEP/CX_GATEWAY` and `/IWBEP/CX_CP_REMOTE`\) separately and implement a corresponding exception handling for these.

If you are using the local Client Proxy, you only need to catch `/IWBEP/CX_GATEWAY`, since the remote exception will not be raised in such a scenario.



### Example

You want to use the remote Client Proxy to consume an OData request and include proper exception handling in your coding:

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



### Step-by-step

**Step 1:** Catching the remote exception and fetching the information about the raised exception \(followed by your own exception handling\)

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

**Step 2:** Catching the Gateway exception and fetching the corresponding error text \(followed by your own exception handling\)

```

  DATA: lx_gateway           TYPE REF TO /iwbep/cx_gateway,
        lv_client_error_text TYPE string.


CATCH /iwbep/cx_gateway INTO lx_gateway.
  lv_client_error_text = lx_gateway->get_text( ).

  “Further error handling
   ...

```

