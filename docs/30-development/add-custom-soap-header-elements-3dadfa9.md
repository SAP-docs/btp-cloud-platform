<!-- loio3dadfa903a11457d92248bccaa44fa27 -->

# Add Custom SOAP Header Elements

With the Web services SOAP header protocol, you can programmatically add custom XML elements to the SOAP request header.



<a name="loio3dadfa903a11457d92248bccaa44fa27__section_r3v_c5v_gsb"/>

## Context

Some services can require setting specific XML elements in the SOAP header. To add such custom elements, you can use method `add_soap_header_element`.



<a name="loio3dadfa903a11457d92248bccaa44fa27__section_pzt_d5v_gsb"/>

## Procedure

1.  Create a consumer proxy by instantiating the generated class with a SOAP destination object. See [Enable SOAP Communication in Your ABAP Code](enable-soap-communication-in-your-abap-code-6ab460e.md) for more information.

2.  Pass the proxy object to the factory method `CL_WS_PROTOCOL_FACTORY=>get_soap_header_protocol( )`. The factory method returns a \(proxy-specific\) WS protocol object to adjust the SOAP header.
3.  Pass the custom XML element as string to method `ADD_SOAP_HEADER_ELEMENT`.

```abap
DATA(ws_soap_header_facade) = cl_ws_protocol_factory=>get_soap_header_protocol( proxy ).
ws_soap_header_facade->add_soap_header_element( '<XML element>' ).
```

> ### Note:  
> To add multiple XML elements, call the method for each element separately.



## Exception Handling

The API raises the exception `cx_ws_protocol_error`, for example, if the code snippet is syntactically incorrect or if one of the following reserved namespaces is used:

-   `http://schemas.xmlsoap.org/ws/2004/08/addressing`
-   `http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd`
-   `http://www.w3.org/2005/08/addressing`
-   `http://www.sap.com/webas/640/soap/features/messageId`
-   `http://schemas.xmlsoap.org/ws/2005/02/rm`
-   `http://docs.oasis-open.org/ws-rx/wsrm/200702`
-   `http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512`
-   `http://schemas.xmlsoap.org/ws/2005/02/sc`
-   `http://www.sap.com/webas/630/soap/runtime/session/protocol`



<a name="loio3dadfa903a11457d92248bccaa44fa27__section_pld_35v_gsb"/>

## Example

The following example shows how to adjust the SOAP request header followed by the Web service call.

> ### Sample Code:  
> ```abap
> TRY.
>     " Create a consumer proxy.
>     DATA(soap_destination) = cl_soap_destination_provider=>create_by_comm_arrangement(
>                              comm_scenario  = '<test scenario>'
>                              service_id     = '<service id>'
>                              comm_system    = '<comm system>' ).
>     DATA(proxy) = NEW example_consumer( destination = soap_destination ).
>      
>     DATA xml_element TYPE string VALUE
>       '<n0:CustomHeaderElement xmlns:n0="http://ws.example.org/ws/">' &
>         '<n0:CustomElement>' &
>           '<n0:value>specific info</n0:value>' &
>         '</n0:CustomElement>' &
>       '</n0:CustomHeaderElement>' .
>  
>     TRY.
>       " Pass the proxy object to factory method and add XML element to the SOAP request header.
>       DATA(ws_header_facade) = cl_ws_protocol_factory=>get_soap_header_protocol( proxy ).
>       ws_header_facade->add_soap_header_element( xml_element ).
>      
>       CATCH cx_ws_protocol_error.
>       " Handle error.
>     ENDTRY.
>  
>   " Call server
>   DATA(request) = VALUE example_req_msg_type( ).
>      proxy->example_operation(
>    EXPORTING
>      input = request
>    IMPORTING
>      output = DATA(response) ).
>  
>   CATCH cx_ai_system_fault.
>   " Handle error.
>   CATCH cx_soap_destination_error.
>   " Handle error.
>  
> ENDTRY.
> ```

The resulting SOAP request looks like this:

```
<?xml version="1.0" encoding="UTF-8"?>
<env:Envelope xmlns:env="http://www.w3.org/2003/05/soap-envelope">
   <env:Header>
      ...
      <n0:CustomHeaderElement xmlns:n0="http://ws.example.org/ws/">
         <n0:CustomElement>
            <n0:value>specific info</n0:value>
         </n0:CustomElement>
      </n0:CustomHeaderElement>
      ...
   </env:Header>
   <env:Body>
      ...
   </env:Body>
</env:Envelope>
```

**Related Information**  


[Set Up SOAP Communication](set-up-soap-communication-8b6723b.md "Developers can consume SOAP-based Web services for outbound communication from the ABAP environment.")

