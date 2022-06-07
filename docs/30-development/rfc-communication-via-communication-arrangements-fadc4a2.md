<!-- loiofadc4a223fb346b89052b94b8811d9b6 -->

# RFC Communication via Communication Arrangements



To establish communication via RFC, you need to create an outbound service of type RFC and use a Service Consumption Model \(SCM\) or the `CALL FUNCTION ... DESTINATION` statement to call other systems from the ABAP environment.



<a name="loiofadc4a223fb346b89052b94b8811d9b6__section_sbh_3nz_qsb"/>

## Prerequisites

-   You've created a communication scenario as described in [Defining a Communication Scenario Including Authorization Values](defining-a-communication-scenario-including-authorization-values-bba0fd2.md).
-   If you want to call other systems via SCM, you must have created an SCM of type RFC as described in [Generating Proxies for Remote Function Call \(RFC\)](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/32812d950d3848359ce391dae477f201.html).



<a name="loiofadc4a223fb346b89052b94b8811d9b6__section_ij2_pnz_qsb"/>

## Procedure

1.  Create a corresponding outbound service of type RFC.

    1.  In your ABAP project, select the relevant package node in the Project Explorer.

    2.  Open the context menu and choose *File* \> *New* \> *Other ABAP Repository Object* \> *Cloud Communication Management* \> *Outbound Service* \> *Next* to launch the creation wizard.
    3.  Enter the name of the outbound service.
    4.  Select RFC in the *Service Type* dropdown list.
    5.  Choose *Next* and select a transport request.
    6.  In field *RFC Function Module*, enter the name of the relevant RFC function module.
    7.  Save the outbound service.

2.  Add the newly created outbound service to a communication scenario. See [Service Consumption via Communication Arrangements](service-consumption-via-communication-arrangements-86aece6.md) for more information. According to your developed communication scenario, add the following:


    <table>
    <tr>
    <td valign="top">

    `comm_scenario`


    
    </td>
    <td valign="top">

    mandatory


    
    </td>
    <td valign="top">

    ID of the developed communication scenario


    
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

    ID of the configured communication system


    
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

    ID of the developed outbound service


    
    </td>
    </tr>
    </table>
    
    > ### Note:  
    > To call an RFC function module in your communication scenario, it's sufficient to define one outbound service of type RFC that can be used to call multiple RFC function modules. For this outbound service, go to the corresponding communication scenario. On the *Outbound* tab in the *Outbound Service* section, select *Generate Destination*.
    > 
    > To document which RFC function modules are called by a communication scenario, you can define separate outbound services and define the name of the function modules without selecting *Generate Destination*.

3.  Call the RFC service as described in the example. Copy the code from the *Overview* tab in your SCM and add the `comm_system_id` and `service_id` parameters if necessary.



**Using a Service Consumption Model**

This example shows how to use RFC communication with an SCM.

> ### Sample Code:  
> ```abap
> DATA: lr_cscn TYPE if_com_scenario_factory=>ty_query-cscn_id_range.
>  
>  
> " find Communication Arrangement by scenario ID
> lr_cscn = VALUE #( ( sign = 'I' option = 'EQ' low = '<Scenario ID>' ) ).DATA(lo_factory) = cl_com_arrangement_factory=>create_instance( ).lo_factory->query_ca(
>   EXPORTING
>     is_query = VALUE #( cscn_id_range = lr_cscn )
>   IMPORTING
>     et_com_arrangement = DATA(lt_ca) ).
>  
> IF lt_ca IS INITIAL.
>   EXIT.
> ENDIF.
>  
> " take the first one
> READ TABLE lt_ca INTO DATA(lo_ca) INDEX 1.
>  
> " get destination based on Communication Arrangement
> TRY.
>   DATA(lo_dest) = cl_rfc_destination_provider=>create_by_comm_arrangement(
>     EXPORTING
>       comm_scenario = '<Scneario ID>'
>       service_id = '<Outbound Service ID>'
>       comm_system_id = lo_ca->get_comm_system_id( )
>       ).
>   CATCH cx_rfc_dest_provider_error.
>     " handle CX_RFC_DEST_PROVIDER_ERROR
> ENDTRY.
>  
> " Service Consumption Model:
> TRY.
>   CREATE OBJECT myobj
>     EXPORTING
>       destination = lo_dest.
>   myobj->bapi_activitytype_getlist(
>     IMPORTING
>        return            = lt_return
>     CHANGING
>        activitytype_list = lt_acttype_list.
>   ).
> CATCH cx_aco_communication_failure INTO DATA(lcx_comm).
>     " handle CX_ACO_COMMUNICATION_FAILURE (sy-msg* in lcx_comm->IF_T100_MESSAGE~T100KEY)
>   CATCH cx_aco_system_failure INTO DATA(lcx_sys).
>      " handle CX_ACO_SYSTEM_FAILURE (sy-msg* in lcx_sys->IF_T100_MESSAGE~T100KEY)
>   CATCH cx_aco_application_exception INTO DATA(lcx_appl).
>     " handle APPLICATION_EXCEPTIONS (sy-msg* in lcx_appl->IF_T100_MESSAGE~T100KEY)
> ENDTRY.
> ```

**Using `CALL FUNCTION ... DESTINATION`**

To use the `CALL FUNCTION ... DESTINATION` statement, use the following code:

> ### Sample Code:  
> ```abap
> DATA: lr_cscn TYPE if_com_scenario_factory=>ty_query-cscn_id_range.
>  
>  
> " find Communication Arrangement by scenario ID
> lr_cscn = VALUE #( ( sign = 'I' option = 'EQ' low = '<Scenario ID>' ) ).DATA(lo_factory) = cl_com_arrangement_factory=>create_instance( ).lo_factory->query_ca(
>   EXPORTING
>     is_query = VALUE #( cscn_id_range = lr_cscn )
>   IMPORTING
>     et_com_arrangement = DATA(lt_ca) ).
>  
> IF lt_ca IS INITIAL.
>   EXIT.
> ENDIF.
>  
> " take the first one
> READ TABLE lt_ca INTO DATA(lo_ca) INDEX 1.
>  
> " get destination based on Communication Arrangement
> TRY.
>   DATA(lo_dest) = cl_rfc_destination_provider=>create_by_comm_arrangement(
>     EXPORTING
>       comm_scenario = '<Scneario ID>'
>       service_id = '<Outbound Service ID>'
>       comm_system_id = lo_ca->get_comm_system_id( )
>       ).
>   CATCH cx_rfc_dest_provider_error.
>     " handle CX_RFC_DEST_PROVIDER_ERROR
> ENDTRY.
>  
> " CALL FUNCTION
>       DATA msg TYPE c LENGTH 255.
>       CALL FUNCTION 'BAPI_ACTIVITYTYPE_GETLIST' DESTINATION lo_dest->get_destination_name( )
>           IMPORTING
>             return            = lt_return
>           TABLES
>             activitytype_list = lt_acttype_list
>       EXCEPTIONS
>         system_failure        = 1  MESSAGE msg
>         communication_failure = 2  MESSAGE msg
>         OTHERS                = 3.
>     CASE sy-subrc.
>       WHEN 1.
>       " handle system failure     
>       WHEN 2.
>       " handle communication failure
>       WHEN 3.
>       " handle application failure
>     ENDCASE.
> ```



<a name="loiofadc4a223fb346b89052b94b8811d9b6__section_jz4_v4z_qsb"/>

## Test Your Outbound Call

To test your outbound call, you have to provide a configuration for the outbound service you want to call in your code.

Create a communication system and communication arrangement for the communication scenario in the Communication Systems and Communication Arrangements apps and maintain the required data.

**Related Information**  


[Service Consumption via Communication Arrangements](service-consumption-via-communication-arrangements-86aece6.md "")

