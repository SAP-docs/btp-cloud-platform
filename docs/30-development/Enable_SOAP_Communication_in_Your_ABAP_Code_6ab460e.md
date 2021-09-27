<!-- loio6ab460e1a59e4890b8faa3fcc35f3343 -->

# Enable SOAP Communication in Your ABAP Code

SOAP-based web service outbound communication within the ABAP environment is enabled by using SOAP destinations in a corresponding destination service.



<a name="loio6ab460e1a59e4890b8faa3fcc35f3343__section_tbk_413_zkb"/>

## Context

The ABAP environment allows you to use synchronous outbound web services based on the SOAP protocol. These SOAP services can be used for the communication with S/4HANA Cloud, on-premise systems, or any other SOAP service exposed to the Internet.

The configuration of SOAP web services in the ABAP environment can be done with the help of SOAP destinations.

A SOAP destination is used to instantiate the web service consumer proxy in the coding.

You have the following options to create SOAP destinations:

-   **Communication arrangement approach**: By using a destination based on a communication arrangement. See [Communication Arrangement](Communication_Arrangement_201de48.md).
-   **URL approach**: By using a plain URL and setter methods to provide the needed configuration directly in the coding.
-   **Destination service approach**: By using a SOAP destination, which is maintained in a destination service that resides in the Cloud Foundry environment.

For more information, see [Developing External Service Consumption \(Outbound Communication\)](Developing_External_Service_Consumption_(Outbound_Communication)_f871712.md).

> ### Note:  
> In on-premise systems, SOAP services are configured by logical ports, which are maintained in transaction `SOAMANAGER`. In the ABAP environment, this concept of logical ports was replaced by the concept of SOAP destinations.



<a name="loio6ab460e1a59e4890b8faa3fcc35f3343__section_kpb_hd3_zkb"/>

## Use

**Communication Arrangement**

> ### Note:  
> For the following example, the communication arrangement has to be created in advance. Parameter `service_id` and `comm_system` are optional.

> ### Sample Code:  
> ```
> TRY.
>         DATA(lo_soap_dest) = cl_soap_destination_provider=>CREATE_BY_COMM_ARRANGMENT(
>                           comm_scenario               = 'test_scenario'
>                           service_id                  = 'service_id'
>                           comm_system                 = 'comm_system'
>                         ).
>         DATA(lo_consumer) = new CO_FOO_PROXY( destination = lo_soap_dest ).
>         lo_consumer->foo_method(
>           EXPORTING
>             input  = l_request
>           IMPORTING  
>             output = DATA(l_response)
>         ).
>       CATCH cx_soap_destination_error INTO DATA(lx_error).
>                error_handling( lx_error ).
>     ENDTRY.
> 
> ```

**Plain URL**

> ### Sample Code:  
> ```
> TRY.
> DATA(lo_dest) = cl_soap_destination_provider=>CREATE_BY_URL(
> i_url = 'https://foo_host/sap/bc/srt/rfc/sap/foo_provider/000/foo_service/foo_binding' ).
> 
> lo_dest->set_basic_authentication( i_user = p_user i_password = p_pwd ).
> 
> DATA(lo_consumer) = new CO_FOO_PROXY( destination = lo_dest ).
> lo_consumer->foo_method(
> EXPORTING
> input = l_request
> IMPORTING
> output = DATA(l_response)
> ).
> CATCH cx_soap_destination_error cx_ai_system_fault INTO DATA(lx_error).
> error_handling( lx_error ).
> ENDTRY.
> ```

**Cloud Destination**

> ### Sample Code:  
> ```
> TRY.
>         DATA(lo_soap_dest) = cl_soap_destination_provider=>CREATE_BY_CLOUD_DESTINATION(
>                           i_name                  = 'test_destination'
>                           i_service_instance_name = 'DESTINATIONSERVICE'
>                         ).
>         DATA(lo_consumer) = new CO_FOO_PROXY( destination = lo_soap_dest ).
>         lo_consumer->foo_method(
>           EXPORTING
>             input  = l_request
>           IMPORTING  
>             output = DATA(l_response)
>         ).
>       CATCH cx_soap_destination_error INTO DATA(lx_error).
>                error_handling( lx_error ).
>     ENDTRY.
> 
> ```

To set up a SOAP destination, see [Set Up a SOAP Destination](Set_Up_a_SOAP_Destination_7e22ed9.md).

**Related Information**  


[Generate a Proxy to Consume SOAP-Based Web Services](Generate_a_Proxy_to_Consume_SOAP-Based_Web_Services_8b6723b.md "Consuming synchronous SOAP-based web services for outbound communication from the ABAP environment.")

