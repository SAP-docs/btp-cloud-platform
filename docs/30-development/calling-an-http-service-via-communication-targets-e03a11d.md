<!-- loioe03a11db11554cb0a81d2f60b5095686 -->

# Calling an HTTP Service via Communication Targets



<a name="loioe03a11db11554cb0a81d2f60b5095686__prereq_jxc_c3y_pbc"/>

## Prerequisites

You've created a communication scenario as described in [Defining a Communication Scenario Including Authorization Values](defining-a-communication-scenario-including-authorization-values-bba0fd2.md).



## Context

To call an HTTP service via communication targets, proceed as follows.



## Procedure

1.  Create a communication target as described in [Working With Communication Targets](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide/working-with-communication-targets?locale=en-US).

2.  Create a corresponding outbound service of type communication target as described in [Creating Outbound Services](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide/creating-outbound-services).

3.  Add the relevant communication target to the newly created outbound service.

4.  Add the newly created outbound service to your scenario.

5.  Publish the communication scenario. The administrator can then create the required communication management objects as described in [Next Steps](calling-an-http-service-via-communication-targets-e03a11d.md#loioe03a11db11554cb0a81d2f60b5095686__postreq_vcb_cjy_pbc).

6.  If the communication target has multiple assigned application destinations, create an implementation of the `communication_management` BAdI as described in the example. The BAdI implementation stores the name of the application destinations in a e.

7.  Adapt the service call according to your needs as described in the example.




## Example

**Create a Customizing table to store the name of the application destination.**

> ### Sample Code:  
> ```abap
> @EndUserText.label : 'Cota Custom Table'
> @AbapCatalog.enhancement.category : #NOT_EXTENSIBLE
> @AbapCatalog.tableCategory : #TRANSPARENT
> @AbapCatalog.deliveryClass : #C
> @AbapCatalog.dataMaintenance : #RESTRICTED
> define table zcota_custom {
> 
>   key client  : abap.clnt not null;
>   key usecase : abap.int1 not null;
>   appldest    : abap.sstring(50) not null;
> 
> }
> ```

**Retrieve the name of the relevant application destination.**

> ### Sample Code:  
> ```abap
> METHOD if_com_arrangement_badi~during_save.
> *
> *      !io_com_arrangement TYPE REF TO if_com_arrangement
> *      !io_com_system      TYPE REF TO if_com_system
> *      !io_com_user        TYPE REF TO if_com_user
> *      !io_com_scenario    TYPE REF TO if_com_scenario
> 
>     DATA ls_custom TYPE zcota_custom.
>     DATA(lt_out_srv) = io_com_scenario->get_outbound_services( ).
>     DATA(lt_out_srv_a) = io_com_arrangement->get_outbound_services( ).
>     FIELD-SYMBOLS: <ls_out_srv> LIKE LINE OF lt_out_srv_a.
>     DATA(lt_properties) = io_com_arrangement->get_properties( ).
> 
>     DATA lv_scenarioid TYPE i VALUE 1.
>     LOOP AT lt_properties INTO DATA(ls_property).
>       IF ls_property-name EQ 'USECASE'.
>         lv_scenarioid = ls_property-values[ 1 ].
>       ENDIF.
>     ENDLOOP.
> 
>   " save the application destination to an application-specific persistence
>     LOOP AT lt_out_srv_a ASSIGNING <ls_out_srv>.
>       ls_custom-usecase = lv_scenarioid.
>       ls_custom-appldest = <ls_out_srv>-destination_name.
> 
>       MODIFY zcota_custom FROM @ls_custom.
> 
>     ENDLOOP.
> ENDMETHOD.
> 
> 
> METHOD if_com_arrangement_badi~before_delete.
> *	! @parameter io_com_arrangement | <p class="shorttext synchronized" lang="en">Communication arrangement reference</p>
> *	! @parameter io_com_system      | <p class="shorttext synchronized" lang="en">Communication system reference</p>
> *	! @parameter io_com_user        | <p class="shorttext synchronized" lang="en">Communication user reference</p>
> *	! @parameter io_com_scenario    | <p class="shorttext synchronized" lang="en">Communication scenario reference</p>
> *	! @parameter et_message         | <p class="shorttext synchronized" lang="en">Messages</p>  
>   
>     DATA(lt_out_srv) = io_com_arrangement->get_outbound_services( ).
>     FIELD-SYMBOLS: <ls_out_srv> LIKE LINE OF lt_out_srv.
>     
>     LOOP AT lt_out_srv ASSIGNING <ls_out_srv>.
>       DELETE FROM zcota_custom WHERE appldest = @<ls_out_srv>-destination_name.
>     ENDLOOP.
>   
> ENDMETHOD.
> ```

**HTTP service call**

> ### Sample Code:  
> ```abap
> METHOD if_oo_adt_classrun~main.
> 
>     DATA lo_cota TYPE REF TO z_cota_http.
>     DATA lt_output TYPE STANDARD TABLE OF string.
>     DATA lv_appl_dest TYPE sappdestname.
> 
>     DATA(lv_scen) = '1'.
> 
> 
>     " select the relevant application destination from the Customizing table
>     
>     SELECT SINGLE appldest
>     FROM zcota_custom
>     WHERE usecase = @lv_scen
>     INTO @lv_appl_dest.
> 
> 
>     TRY.
>         lo_cota = NEW z_cota_http( lv_appl_dest ).
>         DATA(lo_client) = lo_cota->create_web_http_client( ).
>         DATA(lo_response) = lo_client->execute( if_web_http_client=>get ).
>         DATA(ls_status) = lo_response->get_status( ).
> 
> 
>       CATCH cx_appdestination INTO DATA(lx_appdestination).
>         APPEND lx_appdestination->get_text( ) TO lt_output.
>       CATCH cx_communication_target_error INTO DATA(lx_communication_target_error).
>         APPEND lx_communication_target_error->get_text( ) TO lt_output.
>       CATCH cx_web_http_client_error INTO DATA(lx_web_http_client_error).
>         APPEND lx_web_http_client_error->get_text( ) TO lt_output.
> 
>     ENDTRY.
> 
> 
>     out->write( lo_response->get_text( ) ).
> 
> 
>   ENDMETHOD.
> ```



<a name="loioe03a11db11554cb0a81d2f60b5095686__postreq_vcb_cjy_pbc"/>

## Next Steps

To test your outbound call, you have to provide a configuration for the outbound service you want to call in your code.

Create a communication system and communication arrangement for the communication scenario and maintain the required data, such as host name and credentials in the Communication Systems and Communication Arrangements apps. For more information, see [Communication Management](communication-management-5b8ff39.md#loio5b8ff39ddb6741a29ddfcf587939e8f4).

These tasks are performed by the administrator. For more information, see [Set Up HTTP Communication](set-up-http-communication-3884bc3.md).

