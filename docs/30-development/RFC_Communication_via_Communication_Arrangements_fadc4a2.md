<!-- loiofadc4a223fb346b89052b94b8811d9b6 -->

# RFC Communication via Communication Arrangements

To establish communication via RFC, you need to create an outbound service of the type RFC and use the `CALL FUNCTION ... DESTINATION` statement to call other systems from the ABAP environment.

Alternatively, you can use proxies for RFC communication. See [Generating Proxies for Remote Function Call \(RFC\)](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/32812d950d3848359ce391dae477f201.html)

1.  Launch ABAP Development Tools.

2.  In your ABAP project, select the relevant package node in the *Project Explorer*.

3.  Open the context menu and choose *File* \> *New* \> *Other ABAP Repository Object* \> *Cloud Communication Management* \> *Outbound Service* \> *Next*to launch the creation wizard.

4.  Enter the name of the outbound service.

    > ### Note:  
    > The name of the outbound service needs to follow the naming convention to end with the suffix SRFC: <service\>\_SRFC.

5.  Select *RFC* in the *Service Type* dropdown list.

6.  Choose *Next* and select a transport request.

    > ### Note:  
    > To call an RFC function module in your communication scenario, it is sufficient to define one outbound service of the type RFC that can be used to call multiple RFC function modules. For this outbound service, you need to tick the *Generate Destination* checkbox in the *Outbound Service Destination*.

    To document which RFC function modules are called by a communication scenario, you can define separate outbound services and define the name of the function modules but do not tick *Generate Destination*.

7.  Add the newly created outbound service to a communication scenario.

8.  Create a communication system and communication arrangement for the communication scenario and maintain the required data, such as host name, and credentials in the *Communication Systems* and *Communication Arrangements* apps.


**Enable RFC Communication in your ABAP Code**

> ### Sample Code:  
> ```
>    data: lr_cscn type if_com_scenario_factory=>ty_query-cscn_id_range.
> 
> * Find CA by scenario ID
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
>         data(lo_dest) = cl_rfc_destination_provider=>create_by_comm_arrangement(
>           exporting
>             comm_scenario     = '<Scenario ID>'
>             service_id        = '<Outbound Service ID>'
>             comm_system_id    = lo_ca->get_comm_system_id( ) ).
> 
>         data(lv_dest) = lo_dest->get_destination_name( ).
> 
> * call function module 
>         call function 'BAPI_ACTIVITYTYPE_GETLIST' destination lv_dest
>           importing
>             return            = lt_return
>           tables
>             activitytype_list = lt_acttype_list.
>       catch cx_rfc_dest_provider_error into data(lx_error).
>     endtry.
> 
> ```



Using the `create_by_comm_arrangement` method of the `cl_rfc_destination_provider` class, the information is passed via 3 parameters:

-   `comm_scenario` \(mandatory\): ID of the developed communication scenario.
-   `comm_system_id` \(optional\): ID of the configured communication system.
-   `service_id` \(optional\): ID of the developed outbound service.

