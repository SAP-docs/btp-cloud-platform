<!-- loio2133e15cbf8747dbad81dff41a14e139 -->

# SOAP Communication via Communication Arrangements

To enable SOAP \(Simple Object Access Protocol\) communication, you need to create an outbound service of the type SOAP and use the proxy to call the respective web service from the ABAP environment.

1.  Launch the ABAP Development Tools.

2.  In your ABAP project, select the relevant package node in the *Project Explorer*.

3.  Open the context menu and choose *File* \> *New* \> *Other ABAP Repository Object* \> *Cloud Communication Management* \> *Outbound Service* \> *Next*to launch the creation wizard.

4.  Enter the name of the outbound service.

    Note: The name of the outbound service needs to the follow the naming convention to end with the suffix SPRX: <service\>\_SPRX.

5.  Select *SOAP* in the *Service Type* dropdown list.

6.  Choose *Next* and select a transport request.

7.  In the detail screen, select the required SOAP proxy class.

8.  Add the newly created outbound service to a communication scenario

9.  Maintain the URL to call the service in the communcation scenario.

10. Create a communication system and communication arrangement for the communication scenario and maintain the required data, such as host name, and credentials in the *Communication Systems* and *Communication Arrangements* apps.


**SOAP Communication in your ABAP Code**

> ### Sample Code:  
> ```
>    data: lr_cscn type if_com_scenario_factory=>ty_query-cscn_id_range.
> 
> * Find CA by scenario
>     lr_cscn = value #( ( sign = 'I' option = 'EQ' low = '<Scenario ID>' ) ).
>     data(lo_factory) = cl_com_arrangement_factory=>create_instance( ).
>     lo_factory->query_ca(
>       exporting
>         is_query           = value #( cscn_id_range = lr_cscn )
>       importing
>         et_com_arrangement = data(lt_ca) ).
> 
>     if lt_ca is initial.
>       exit.
>     endif.
> 
> * take the first one
>     read table lt_ca into data(lo_ca) index 1.
> 
> * get destination based on Communication Arrangement
>     try.
>         data(lv_cs_id) = lo_ca->get_comm_system_id( ).
>         data(lo_dest) = cl_soap_destination_provider=>create_by_comm_arrangement(
>                                          comm_scenario  = '<Scenario ID>'
>                                          service_id     = '<Outbound Service ID>'
>                                          comm_system_id = lv_cs_id ).
> 
>         data(proxy) = new zco_proxy_class( destination = lo_dest ).
> 
>         proxy->query(
>           exporting
>             input = ls_request
>           importing
>             output = data(ls_response) ).
> 
>       catch cx_soap_destination_error.
>         "handle error
>       catch cx_ai_system_fault.
>         "handle error
>       catch zjbcx_standard_message_fault.
>         "handle error
>       catch cx_rfc_dest_provider_error into data(lx_error).
> 
> ```

