<!-- loio3047582e5c744bd9839a98c99bd224fa -->

# HTTP Communication via Communication Arrangements

To establish communication via HTTP, you need to create an outbound service of the type HTTP and use the HTTP client to enable HTTP communication from the ABAP environment.

1.  Launch ABAP Development Tools.

2.  In your ABAP project, select the relevant package node in the Project Explorer.

3.  Open the context menu and choose *File* \> *New* \> *Other ABAP Repository Object* \> *Cloud Communication Management* \> *Outbound Service* \> *Next*to launch the creation wizard.

4.  Enter the name of the outbound service.

    > ### Note:  
    > The name of the outbound service needs to the follow the naming convention to end with the suffix HTTP: <service\>\_HTTP.

5.  Select *HTTP Service* in the *Service Type* dropdown list.

6.  Choose *Next* and select a transport request.

7.  Add the newly created outbound service to a communication scenario.

8.  Maintain the URL to call the service in the communication scenario.

9.  Create a communication system and communication arrangement for the communication scenario and maintain the required data, such as host name, and credentials in the *Communication Systems* and *Communication Arrangements* apps.


**Enable HTTP Communication in your ABAP Code**

> ### Sample Code:  
> ```
>   data: lr_cscn type if_com_scenario_factory=>ty_query-cscn_id_range.
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
> * get destination based to Communication Arrangement
>     try.
>         data(lo_dest) = cl_http_destination_provider=>create_by_comm_arrangement(
>             comm_scenario  = '<Scenario ID>'
>             service_id     = '<Outbound Service ID>'
>             comm_system_id = lo_ca->get_comm_system_id( ) ).
>                    
>         data(lo_http_client) = cl_web_http_client_manager=>create_by_http_destination( lo_dest ).
>         
> * Execute the request         
>         data(lo_request) = lo_http_client->get_http_request( ).       
>         data(lo_response) = lo_http_client->execute( if_web_http_client=>get ).
>         
>       catch cx_http_dest_provider_error into data(lx_http_dest_provider_error).
>         out->write( lx_http_dest_provider_error->get_text( ) ).
>         exit.
>         
>       catch cx_web_http_client_error.
>         "handle exception here
>     endtry.
>   endmethod.
> 
> ```

