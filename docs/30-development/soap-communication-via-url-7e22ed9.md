<!-- loio7e22ed9979a34a61afdeaee7c49e3711 -->

# SOAP Communication via URL

Instead of setting the *Additional Properties* as in the destination service approach, you can set them programmatically:

-   `set_soap_version( )`: Sets the SOAP version. Valid values for the SOAP version are provided by the constants `if_soap_destination=>soap_version_11` and `if_soap_destination=>soap_version_12`.
-   `set_max_wait_time( )`: Sets the maximum waiting time for the consumer \(in seconds\).
-   `set_compress_message( )`: Enables compression of messages if parameter `i_compress_message` is set to `true`. Disables compression if the parameter is set to `false`.
-   `set_soap_action( )`: Sets the SOAP action for a given operation. Parameters are the name of the operation and the value of the SOAP action.
-   `set_url( )`: Sets the URL of the endpoint.
-   `set_basic_authentication( )`: Sets the authentication method to basic authentication and sets user and password.
-   `use_client_certificate( )`: Sets the authentication method to client certificate authentication. The default client certificate is used.

> ### Note:  
> An existing service consumption model \(SRVC\) is required.

> ### Note:  
> Using `create_by_url` is only suitable for public services or test purposes, because credentials should be stored in the communication management in SAP Fiori launchpad.

Call the SOAP service as described in the example. As described in [SOAP Communication via Communication Arrangements](soap-communication-via-communication-arrangements-2133e15.md), copy the code snippet from the *Overview* tab in your SRVC. Replace the `CREATE_BY_COMM_ARRANGEMENT` method with the `CREATE_BY_URL` method and pass the required URL to the method.

> ### Sample Code:  
> ```abap
> TRY.
> 
> "replace create_by_comm_arrangement with create_by_url
>     DATA(soap_destination) = cl_soap_destination_provider=>create_by_url( 
> 						'https://<host>/sap/bc/srt/xip/sap/<provider>/000/<service>/<binding>').
>  
>     soap_destination->use_client_certificate( ).
> 
> "generated code snippet 
>     DATA(proxy) = NEW zsc_co_service( destination = soap_destination ).
>  
>     DATA(request) = VALUE zsc_req_msg_type( req_msg_type-product = '<product name>' ).
>     proxy->get_price(
>       EXPORTING
>         input = request
>       IMPORTING
>         output = DATA(response) ).
>  
>     "handle response
>   CATCH cx_soap_destination_error.
>     "handle error
>   CATCH cx_ai_system_fault.
>     "handle error
>   CATCH zsc_cx_fault_msg_type.
>     "handle error
>  
> ENDTRY.
> ```

**Related Information**  


[Enable SOAP Communication in Your ABAP Code](enable-soap-communication-in-your-abap-code-6ab460e.md "")

[Tutorial: Consume SOAP-Based Web Services with SAP BTP ABAP Environment](https://developers.sap.com/tutorials/abap-environment-soap-web-services.html)

