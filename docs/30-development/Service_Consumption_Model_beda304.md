<!-- loiobeda304ecf984c3c843be65d4cd73b02 -->

# Service Consumption Model



SAP supports various protocols and provides the corresponding clients and functions to handle requests and responses.

HTTP: `CL_WEB_HTTP_CLIENT`

RFC: `CALL FUNCTION`

To simplify the implementation of a remote call, you can create a service consumption model for the external service. The service consumption model creates proxies for the remote service. That way, you can access the service in a strictly typed manner without the need to compile requests and parse responses. The following consumption model types are supported:

-   OData
-   SOAP
-   RFC

**Related Information**  


[OData Client Proxy](OData_Client_Proxy_0d92f49.md "")

[Set Up SOAP Communication](Set_Up_SOAP_Communication_8b6723b.md "Developers can consume synchronous SOAP-based Web services for outbound communication from the ABAP environment.")

