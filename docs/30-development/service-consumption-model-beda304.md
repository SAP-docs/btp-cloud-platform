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


[OData Client Proxy Configurations](odata-client-proxy-configurations-0d92f49.md "There are several consumption types and OData versions for your OData Client Proxy configurations, depending on your use case.")

[Set Up SOAP Communication](set-up-soap-communication-8b6723b.md "Developers can consume SOAP-based Web services for outbound communication from the ABAP environment.")

