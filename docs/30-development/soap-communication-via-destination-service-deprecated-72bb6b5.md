<!-- loio72bb6b5208b641a1b19672459bbfbc11 -->

# SOAP Communication via Destination Service \(Deprecated\)

To configure a SOAP-specific destination, create an HTTP destination as described in [Set Up HTTP Communication](set-up-http-communication-3884bc3.md).

> ### Note:  
> You can use the destination service. However, this approach is deprecated. We recommend using the communication arrangement approach instead. See [SOAP Communication via Communication Arrangements](soap-communication-via-communication-arrangements-2133e15.md) for more information.

You can set Web service-specific properties by maintaining the following *Additional Properties* in the destination:

-   `ws.soapVersion`: Sets the SOAP version.
-   `ws.maxWaitTime`: Sets the maximum waiting time for the consumer \(in seconds\).
-   `ws.compressMessage`: Enables compression of the message.
-   `ws.soapAction.<operationName>`: Sets the SOAP action for a given operation with name `<operationName>`.

> ### Sample Code:  
> ```abap
> TRY.
>     DATA(lo_soap_dest) = cl_soap_destination_provider=>create_by_cloud_destination(
>                            i_name                   = '<destination name>'
>                            i_service_instance_name  = '<destination service instance name>').
> 
>     DATA(proxy) = NEW zco_appointment_activity_reque(
>                       destination = destination ).
> 
>     DATA(request) = VALUE zsc_req_msg_type(
>               req_msg_type-product = '<product name>' ).
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


[Enable SOAP Communication in Your ABAP Code](enable-soap-communication-in-your-abap-code-6ab460e.md "SOAP-based Web service outbound communication within the ABAP environment is enabled by using SOAP destination objects.")

