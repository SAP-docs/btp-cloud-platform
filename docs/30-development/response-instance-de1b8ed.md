<!-- loiode1b8edfaaef44b39cc10625503b3e52 -->

# Response Instance

A response instance includes information that the request returns.



<a name="loiode1b8edfaaef44b39cc10625503b3e52__section_b4c_czm_4tb"/>

## Overview

Most OData requests return a corresponding response body after the request is successful \(an exception can be a successful `DELETE` request with HTTP return code `204` with no content\).

The Client Proxy response instance contains information returned by the request. You can use it to read all relevant response information \(for example. the entity business data\).

> ### Note:  
> The responses aren't OData protocol-specific \(Version 2 or Version 4\).



<a name="loiode1b8edfaaef44b39cc10625503b3e52__section_osh_dzm_4tb"/>

## Creating an Instance

A response instance is always created by the corresponding request instance when a request is created.



### Response Types

These response types are available:

-   `/IWBEP/IF_CP_RESPONSE_ACTION`: ***ACTION*** request response.
-   `/IWBEP/IF_CP_RESPONSE_CREATE`: ***CREATE*** request response.
-   `/IWBEP/IF_CP_RESPONSE_DELETE`: ***DELETE*** entity request response.
-   `/IWBEP/IF_CP_RESPONSE_FUNCTION`: ***FUNCTION*** request response.
-   `/IWBEP/IF_CP_RESPONSE_READ`: ***READ*** entity request response.
-   `/IWBEP/IF_CP_RESPONSE_READ_01`: ***READ*** entity \(with zero-to-one navigation\) request response.
-   `/IWBEP/IF_CP_RESPONSE_READ_LST`: ***READ*** entity list request response.
-   `/IWBEP/IF_CP_RESPONSE_UPDATE`: ***UPDATE*** entity request response.
-   `/IWBEP/IF_CP_RESPONSE_UPDATE_L`: ***UPDATE*** entity list request response.



<a name="loiode1b8edfaaef44b39cc10625503b3e52__section_us5_dzm_4tb"/>

## Functionality

Response instances return the response business data of a successful OData request execution. The options a response instance offers depend on the different response types.



<a name="loiode1b8edfaaef44b39cc10625503b3e52__section_byw_2zm_4tb"/>

## Example

For examples of how to create and work with responses, see the [OData Requests](odata-requests-bbaf7a4.md).

