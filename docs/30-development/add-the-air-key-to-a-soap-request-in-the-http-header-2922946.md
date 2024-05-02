<!-- loio29229464873a4357922d5e290ea4e9e4 -->

# Add the AIR Key to a SOAP Request in the HTTP Header

With the web services HTTP header protocol, you can programmatically add the Application Interface Key \(AIR key\) field to the HTTP header of a SOAP request.



## Context

If your application calls an SAP SOAP API, the Application Interface Key must be part of the request. The Application Interface Key is passed in the HTTP header. For SOAP requests, you can do this with the HTTP header protocol. To add this field, you can use the method `SET_FIELD` of the interface `IF_WS_HTTP_HEADER_FACADE`.

> ### Note:  
> -   It isn't possible to add a field other than the Application Interface Key field.
> -   Once a web service call is performed, the custom HTTP header is reset. If you want to use the same value again, you must set the value again.



## Procedure

1.  Create a consumer proxy by instantiating the generated class with a SOAP destination object. See [Enable SOAP Communication in Your ABAP Code](enable-soap-communication-in-your-abap-code-6ab460e.md) for more information.

2.  Pass the proxy object to the factory method `cl_ws_protocol_factory=>get_http_header_protocol( )`. The factory method returns a \(proxy-specific\) WS protocol object to adjust the HTTP header.

3.  Pass the name of the HTTP header field and value as string to the method `set_field`.

    > ### Sample Code:  
    > ```
    > DATA(header) = cl_ws_protocol_factory=>get_http_header_protocol( io_proxy = proxy ).
    > header->set_field( iv_name = if_ws_http_header_facade=>co_field_appl_interface_key iv_value = '0123abcd' ).
    > 
    > ```




## Example

> ### Note:  
> After executing a service call, the field value is initialized by the SOAP runtime. Therefore, you have to set the HTTP field values for each service call with the `SET_FIELD` method.

> ### Sample Code:  
> ```abap
> " Get destination object
> 
> TRY.
> 
>     DATA(destination) = cl_soap_destination_provider=>create_by_comm_arrangement(
>     comm_scenario = 'HTTP_HEADER' ).
> 
>     DATA(proxy) = NEW zco_srt_test_provider( destination = destination ).
> 
>   " Pass the proxy object to factory method to obtain an instance of the HTTP header protocol
>     DATA(header) = cl_ws_protocol_factory=>get_http_header_protocol( io_proxy = proxy ).
> 
>   " First service call
>   " Add HTTP field to the SOAP request.
>     header->set_field( iv_name = if_ws_http_header_facade=>co_field_appl_interface_key iv_value = '0123abcd' ).
> 
>   " Call service
>     DATA(request) = VALUE zrfc_system_info( ).
>     proxy->rfc_system_info( EXPORTING input = request IMPORTING output = DATA(response) ).
> 
>   " Second service call
>   " Add HTTP field to the SOAP request.
>     header->set_field( iv_name = if_ws_http_header_facade=>co_field_appl_interface_key iv_value = '9876wxyz' ).
> 
>   " Call service
>     DATA(request) = VALUE zrfc_system_info( ).
>     proxy->rfc_system_info( EXPORTING input = request IMPORTING output = DATA(response) ).
> 
>   CATCH cx_ws_protocol_error INTO DATA(lx_protocol_error).
>     " Handle protocol error
>   CATCH cx_soap_destination_error INTO DATA(lx_error).
>     " Handle destination error
>   CATCH cx_ai_system_fault INTO DATA(lx_fault).
>     " Handle system fault
> 
> ENDTRY.
> ```

