<!-- loio059470b6349d482f89eb9993be14ec00 -->

# Proxy API for the Workflow Capability

With the proxy API, you can start workflows of the workflow capability within SAP Workflow Management out of your ABAP Environment.



The overall starting point is the class CL\_SWF\_CPWF\_API\_FACTORY\_A4C. Once you have the API object of interface IF\_SWF\_CPWF\_API, see the ABAP documentation on supported actions.



<a name="loio059470b6349d482f89eb9993be14ec00__section_xvd_tl1_qjb"/>

## Prerequisites

You've executed the integration steps in your ABAP environment. See [Integrating SAP Workflow Management](../50-administration-and-ops/integrating-sap-workflow-management-b7931f7.md).



> ### Sample Code:  
> This coding sample shows how to start a workflow of the workflow capability.
> 
> ```abap
> 
>     TYPES: BEGIN OF ty_context,
>              some_property TYPE string,
>            END OF ty_context.
> 
>     DATA(lo_cpwf_api) = cl_swf_cpwf_api_factory_a4c=>get_api_instance( ).
> 
>     DATA(ls_context) = VALUE ty_context(
>       some_property = 'someValue'
>     ).
>     DATA(lv_context_json) = lo_cpwf_api->get_start_context_from_data(
>       iv_data = ls_context
>     ).
> 
>     DATA(lv_cpwf_handle) = lo_cpwf_api->start_workflow(
>       iv_cp_workflow_def_id = 'SAP Workflow Management Workflow Definition ID'
>       iv_context            = lv_context_json
>       iv_retention_time     = 30
>       iv_callback_class     = 'ZCL_SWF_CPWF_CALLBACK'
>     ).
> 
> ```

> ### Sample Code:  
> This coding sample shows a completion callback that includes reading the context.
> 
> ```abap
> 
>   METHOD if_swf_cpwf_callback~workflow_instance_completed.
>     TYPES: BEGIN OF ty_context,
>              some_result TYPE string,
>            END OF ty_context.
> 
>     TRY.
>         data(lo_cpwf_api) = cl_swf_cpwf_api_factory_a4c=>get_api_instance( ).
>         data(lv_context_json) = lo_cpwf_api->get_workflow_context( iv_cpwf_handle = iv_cpwf_handle ).
> 
>         DATA ls_context TYPE ty_context.
> 
>         lo_cpwf_api->get_context_data_from_json(
>           EXPORTING
>             iv_context = lv_context_json
>          IMPORTING
>             ev_data = ls_context
>         ).
>       CATCH cx_swf_cpwf_api INTO DATA(lx_exc).
>         RAISE EXCEPTION TYPE zcx_swf_cpwf_callback
>           EXPORTING
>             previous = lx_exc.
>     ENDTRY.
> 
>     " your business coding
>   ENDMETHOD.
> 
> ```

> ### Sample Code:  
> This coding sample shows the raising of an event towards SAP Business Technology Platform.
> 
> ```abap
> 
>     TYPES: BEGIN OF ty_example_context,
>              value TYPE int4,
>            END OF ty_example_context.
> 
>     CONSTANTS: lc_cp_workflow_def_id TYPE if_swf_cpwf_api=>cpwf_def_id 		VALUE '<SAP Workflow Management Workflow Definition ID>',
>                lc_event_def_id       TYPE if_swf_cpwf_api=>cpwf_evt_def_id 	VALUE '<SAP Workflow Management Event Definition ID>'.
> 
>     TRY.
>         " Get a Instance for the CPWF Integration API
>         DATA(lo_cpwf_api) = cl_swf_cpwf_api_factory_a4c=>get_api_instance( ).
> 
>         " There should be a started workflow in order to raise an event
>         DATA(lv_cpwf_handle) = lo_cpwf_api->start_workflow(
>           EXPORTING
>             iv_cp_workflow_def_id = lc_cp_workflow_def_id
>             iv_retention_time     = 30
>         ).
> 
>         COMMIT WORK.
> 
>         " provide relevant event context data => in this case a meaningful integer
>         DATA(lv_event_context_data) = VALUE ty_example_context( value = 4711 ).
>         DATA(lv_event_context) = lo_cpwf_api->get_context_from_data( iv_data = lv_event_context_data ).
> 	
> 	" actually raise the event
>         lo_cpwf_api->raise_event(
>           EXPORTING
>             iv_cpwf_handle   = lv_cpwf_handle
>             iv_event_def_id  = lc_event_def_id
>             iv_event_context = lv_event_context
>         ).
> 
>         COMMIT WORK.
> 
>       CATCH cx_swf_cpwf_api INTO DATA(lx_api).
>         WRITE: 'Exception occurred: ' && lx_api->get_longtext( ).
>     ENDTRY.
> 
> ```

