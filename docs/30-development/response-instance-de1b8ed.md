<!-- loiode1b8edfaaef44b39cc10625503b3e52 -->

# Response Instance

In this chapter, we'll learn the meaning of a Client Proxy response as well as how to create and use a Client Proxy response instance.



<a name="loiode1b8edfaaef44b39cc10625503b3e52__section_b4c_czm_4tb"/>

## Overview

Most OData requests return a corresponding response body after \(successful\) execution \(an exception would, for example, be a successful `DELETE` request with HTTP return code `204` – No content\).

The Client Proxy response instance contains information that has been returned by the request execution and can be used by a client to read all relevant response information \(e.g. the business data of an entity\).

A response instance is always created by the corresponding request instance as a result of a request execution.

> ### Note:  
> The responses aren't OData protocol \(V2 or V4\) specific.



<a name="loiode1b8edfaaef44b39cc10625503b3e52__section_osh_dzm_4tb"/>

## Creating an Instance

Response instances are always created on the request instance when executing an OData request.



### Response Types

The following kinds of responses are available to users:

-   `/IWBEP/IF_CP_RESPONSE_ACTION`The response of an ACTION request.
-   `/IWBEP/IF_CP_RESPONSE_CREATE`: The response of a CREATE entity request.
-   `/IWBEP/IF_CP_RESPONSE_DELETE`: The response of a DELETE entity request.
-   `/IWBEP/IF_CP_RESPONSE_FUNCTION`: The response of a FUNCTION request.
-   `/IWBEP/IF_CP_RESPONSE_READ`: The response of a READ entity request.
-   `/IWBEP/IF_CP_RESPONSE_READ_01`: The response of a READ entity \(via zero-to-one navigation\) request.
-   `/IWBEP/IF_CP_RESPONSE_READ_LST`: The response of a READ entity list request.
-   `/IWBEP/IF_CP_RESPONSE_UPDATE` The response of an UPDATE entity request.
-   `/IWBEP/IF_CP_RESPONSE_UPDATE_L` The response of an UPDATE entity list request.



<a name="loiode1b8edfaaef44b39cc10625503b3e52__section_us5_dzm_4tb"/>

## Functionality

The main functionality of response instances is to return the response business data of a successful OData request execution to the user. However, the options a response instance offers depend on the different response kinds. Consult the provided ABAP doc to get an overview over the different functionalities.



<a name="loiode1b8edfaaef44b39cc10625503b3e52__section_byw_2zm_4tb"/>

## Example

Examples on how to create and work with responses are given in the corresponding How-To section \[LINK\].

