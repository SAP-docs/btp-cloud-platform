<!-- loio3047582e5c744bd9839a98c99bd224fa -->

# HTTP Communication via Communication Arrangements



<a name="loio3047582e5c744bd9839a98c99bd224fa__section_c5x_3vx_qsb"/>

## Prerequisites

You've created a communication scenario as described in [Defining a Communication Scenario Including Authorization Values](defining-a-communication-scenario-including-authorization-values-bba0fd2.md).



<a name="loio3047582e5c744bd9839a98c99bd224fa__section_igc_wvx_qsb"/>

## Procedure

1.  Create a corresponding outbound service of type HTTP.

    1.  In your ABAP project, select the relevant package node in the Project Explorer.

    2.  Open the context menu and choose *File* \> *New* \> *Other ABAP Repository Object* \> *Cloud Communication Management* \> *Outbound Service* \> *Next*.
    3.  Enter the name of the outbound service.
    4.  Select *HTTP Service* in the *Service Type* dropdown list.
    5.  Choose *Next* and select a transport request.
    6.  Optional: Go to your outbound service and enter the URL in the field *Default Path Prefix*.
    7.  Save the outbound service.

2.  Add the newly created outbound service to your scenario.
3.  Adapt the communication arrangement check according to your needs as described in the example. See [Service Consumption via Communication Arrangements](service-consumption-via-communication-arrangements-86aece6.md) for more information. According to your developed communication scenario, add the following:


    <table>
    <tr>
    <td valign="top">
    
    `comm_scenario`


    
    </td>
    <td valign="top">
    
    mandatory


    
    </td>
    <td valign="top">
    
    ID of the developed communication scenario.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `comm_system_id`


    
    </td>
    <td valign="top">
    
    optional


    
    </td>
    <td valign="top">
    
    ID of the configured communication system. Use method `query_ca` of class`cl_com_arrangement_factory` to derive it dynamically.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `service_id`


    
    </td>
    <td valign="top">
    
    optional


    
    </td>
    <td valign="top">
    
    ID of the developed outbound service.


    
    </td>
    </tr>
    </table>
    

> ### Note:  
> You can't use the `create_by_comm_arrangement` method for SAP-delivered scenarios.



## Example

> ### Sample Code:  
> ```abap
> DATA: lr_cscn type if_com_scenario_factory=>ty_query-cscn_id_range.
>  
> " find CA by scenario
>     lr_cscn = value #( ( sign = 'I' option = 'EQ' low = '<Scenario ID>' ) ).
>     DATA(lo_factory) = cl_com_arrangement_factory=>create_instance( ).
>     lo_factory->query_ca(
>       EXPORTING
>         is_query           = value #( cscn_id_range = lr_cscn )
>       IMPORTING
>         et_com_arrangement = data(lt_ca) ).
>  
>     IF lt_ca is initial.
>       EXIT.
>     ENDIF.
>  
> " take the first one
>     READ TABLE lt_ca INTO DATA(lo_ca) INDEX 1.
>  
> " get destination based to Communication Arrangement
>     TRY.
>         DATA(lo_dest) = cl_http_destination_provider=>create_by_comm_arrangement(
>             comm_scenario  = '<Scenario ID>'
>             service_id     = '<Outbound Service ID>'
>             comm_system_id = lo_ca->get_comm_system_id( ) ).
>                     
>         DATA(lo_http_client) = cl_web_http_client_manager=>create_by_http_destination( lo_dest ).
>          
> " execute the request        
>         DATA(lo_request) = lo_http_client->get_http_request( ).      
>         DATA(lo_response) = lo_http_client->execute( if_web_http_client=>get ).
>          
>       CATCH cx_http_dest_provider_error.
>         " handle exception here
>          
>       CATCH cx_web_http_client_error.
>         " handle exception here
>     ENDTRY.
> ```



<a name="loio3047582e5c744bd9839a98c99bd224fa__section_tgg_1xx_qsb"/>

## Test Your Outbound Call

To test your outbound call, you have to provide a configuration for the outbound service you want to call in your code.

Create a communication system and communication arrangement for the communication scenario and maintain the required data, such as host name and credentials in the Communication Systems and Communication Arrangements apps.

**Related Information**  


[Set Up HTTP Communication](set-up-http-communication-3884bc3.md "The HTTP client allows to connect to HTTP endpoints.")

