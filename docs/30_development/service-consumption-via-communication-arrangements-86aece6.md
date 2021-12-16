<!-- loio86aece6b6a154075b3d30eee54d35abd -->

# Service Consumption via Communication Arrangements

You as a developer can create and expose services for external outbound consumption to a communication partner by creating an outbound service of the required type \(HTTP, SOAP or RFC\) and specifying the necessary information. To consume these services, you need to create a communication scenario and assign these services to it.

An administrator then creates a communication system and user for the communication partner, maintains a communication arrangement for the scenario using the created communication system, and specifies the authentication method and URLs.

To consume such an external service, you implement the call of the service. Therefore, you need to implement a logical receiver determination in your runtime coding to find the correct target for the outbound call.

The following options are available to establish logical receiver determination provided by communication arrangements:

-   *Allowed Scenarios instances: One instance per client*

    Only one active communication arrangement can be maintained for the communication scenario in the system. The generated destination can be retrieved by providing the communication scenario ID and the respective outbound service ID.

-   *Allowed Scenarios instances: One instance per scenario & communication system*

    Multiple active communication arrangements for one communication scenario for different communication systems in one system are enabled. To determine the correct receiver, you must use additional information to find the correct target. You can either do this based on:

    -   Standard attributes such as *Communication System ID*, or *Business System ID*

    -   Your own properties, such as plant, country, or company, which can be derived from the business context during runtime. You can define your own properties for the communication scenario and maintain them in the communication arrangements.



The sample codes below show how to find the correct reference to a destination and how to use it when calling a service.



Find the destination based on the communication scenario only:

> ### Sample Code:  
> ```
> data: lr_cscn type if_com_scenario_factory=>ty_query-cscn_id_range.
> 
> * Find CA by Scenario ID
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
> * get destination based on Communication Arrangement and the service ID
>     try.
>         data(lo_dest) = cl_http_destination_provider=>create_by_comm_arrangement(
>             comm_scenario  = '<Scenario ID>'
>             service_id     = '<Outbound Service ID>'
>             comm_system_id = lo_ca->get_comm_system_id( ) ).
>                 
>       catch cx_http_dest_provider_error into data(lx_http_dest_provider_error).
>         out->write( lx_http_dest_provider_error->get_text( ) ).
>         exit.       
>     endtry.
> 
> ```



Find the destination based on the communication scenario and business system:

> ### Sample Code:  
> ```
> data: lr_cscn  type if_com_scenario_factory=>ty_query-cscn_id_range,
>       lr_bs_id type if_com_system_factory=>ty_query-cs_business_system_id_range.
> 
> * Find CA by Scenario ID & Business System ID
>     lr_cscn = value #( ( sign = 'I' option = 'EQ' low = '<Scenario ID>' ) ).
>     lr_bs_id = value #( ( sign = 'I' option = 'EQ' low = '<Business System ID>' ) ).
> 
>     data(lo_factory) = cl_com_arrangement_factory=>create_instance( ).
>     lo_factory->query_ca(
>       exporting
>         is_query = value #( cscn_id_range = lr_cscn 
>                             cs_business_system_id_range = lr_bs_id )
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
> * get destination based on Communication Arrangement and the service ID
>     try.
>         data(lo_dest) = cl_http_destination_provider=>create_by_comm_arrangement(
>             comm_scenario  = '<Scenario ID>'
>             service_id     = '<Outbound Service ID>'
>             comm_system_id = lo_ca->get_comm_system_id( ) ).
> 
>       catch cx_http_dest_provider_error into data(lx_http_dest_provider_error).
>         out->write( lx_http_dest_provider_error->get_text( ) ).
>         exit.
>     endtry.
> 
> ```



Find the destination based on the communication scenario and a customer-defined property:

> ### Sample Code:  
> ```
> data: lr_cscn type if_com_scenario_factory=>ty_query-cscn_id_range,
>       lt_prpn type if_com_arrangement_factory=>ty_query-ca_property.
> 
> * Find CA by Scenario ID & property name/value
>     lr_cscn = value #( ( sign = 'I' option = 'EQ' low = '<Scenario ID>' ) ).
> 
>     append initial line to lt_prpn assigning field-symbol(<fs_prp>).
>     <fs_prp>-name = '<Property Name>'.
>     append '<Property Value>' to <fs_prp>-values.
>     
>     data(lo_factory) = cl_com_arrangement_factory=>create_instance( ).
>     lo_factory->query_ca(
>       exporting
>         is_query           = value #( cscn_id_range = lr_cscn ca_property = lt_prpn )
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
> * get destination based on Communication Arrangement and the service ID
>     try.
>         data(lo_dest) = cl_http_destination_provider=>create_by_comm_arrangement(
>             comm_scenario  = '<Scenario ID>'
>             service_id     = '<Outbound Service ID>'
>             comm_system_id = lo_ca->get_comm_system_id( ) ).
> 
>       catch cx_http_dest_provider_error into data(lx_http_dest_provider_error).
>         out->write( lx_http_dest_provider_error->get_text( ) ).
>         exit.
>     endtry.
> 
> ```

