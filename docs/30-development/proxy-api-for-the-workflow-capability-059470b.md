<!-- loio059470b6349d482f89eb9993be14ec00 -->

# Proxy API for the Workflow Capability

With the proxy API, you can start workflows of the workflow capability within SAP Workflow Management out of your ABAP Environment.



The overall starting point is the class CL\_SWF\_CPWF\_API\_FACTORY\_A4C. Once you have the API object of interface IF\_SWF\_CPWF\_API, see the ABAP documentation on supported actions.



<a name="loio059470b6349d482f89eb9993be14ec00__section_xvd_tl1_qjb"/>

## Prerequisites

You've executed the integration steps in your ABAP environment. See [Integrating Workflow](../50-administration-and-ops/integrating-workflow-b7931f7.md).



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



<a name="loio059470b6349d482f89eb9993be14ec00__section_cgl_4mq_qtb"/>

## ABAP RESTful Application Programming Model \(RAP\)

**Early Numbering**

In the RAP version of the Workflow Service API, workflows can be registered using the following command:

> ### Sample Code:  
> Example: EML Create
> 
> ```
> 
> MODIFY ENTITIES OF i_cpwf_inst
>       ENTITY CPWFInstance
>       EXECUTE registerWorkflow
>       FROM VALUE #( ( %key = '<a UUID which is mandatory for mass enabled callers>'
>                       %param-RetentionTime = '<retention time in days>'
>                       %param-CpWfDefId = '<SAP Workflow Service Definition ID>'
>                       %param-CallbackClass = '<Callback class for final state handling>'
>                       %param-Consumer = '<SAP Workflow Scenario ID>') ).
> ```

> ### Note:  
> It's not allowed to call the `registerWorkflow` method multiple times with an identical set of parameters. This also applies to cases where the otherwise optional %key parameter stays empty. Therefore, if you want to use the `registerWorkflow` method in a mass-enabled context you must provide the unique %key parameter.

The parameters `RetentionTime`, `CpWfDefId`, and `Consumer` must be provided.

The workflow context can be provided using the following EML statement:

> ### Sample Code:  
> Example: EML Create
> 
> ```
> 
> MODIFY ENTITIES OF i_cpwf_inst
>       ENTITY CPWFInstance
>       EXECUTE setPayload
>       FROM VALUE #( ( %key-CpWfHandle = '<required key (UUID) of the CPWF instance>'
>                       %param-context = '<workflow context in JSON format>' ) ).
> ```

Both commands should be part of a determination on save. During the save sequence, the workflow is started with the provided data.



**Late Numbering**

As for early numbering, the `registerWorkflow` method can be called in a determination on save for late numbering, too.

The workflow context can be set even later in the `adjust_numbers` method of your business object using the `setPayload` method.

> ### Sample Code:  
> Example: EML Create
> 
> ```
> 
> MODIFY ENTITIES OF i_cpwf_inst
>       ENTITY CPWFInstance
>       EXECUTE setPayload
>       FROM VALUE #( ( %key-CpWfHandle = <required key (UUID) of the CPWF instance>
>                       %param-context = <workflow context in JSON format> ) ).
> ```

During the save sequence, the workflow is started with the provided data. The instance is removed from the draft table and is entered into the active table.

Note, that in the `adjust_numbers` method you must fill the key of each line of the mapped table to make sure the save sequence is executed successfully.

Note also that if you have multiple workflows per instance of your business object you might need to store the assignments yourself in an internal table to be able to call the `set_payload` method during `adjust_numbers` method with the correct data.



> ### Sample Code:  
> This coding sample shows reading the workflow instance context.
> 
> ```abap
> 
> TYPES: BEGIN OF ty_context,
>          attr1 TYPE string,
>          attr2 TYPE int4,
>          attr3 TYPE string,
>        END OF ty_context.
>  
> DATA(lo_cpwf_api) = cl_swf_cpwf_api_factory=>get_api_instance( 'DEFAULT' ).
> DATA(lo_cp_json_with_empty) = lo_cpwf_api->get_json_converter( ).
> DATA(lo_wf_inst_ctxt) = lo_cpwf_api->if_swf_cpwf_capi~workflow_instance_context( ).
>  
> DATA ls_context TYPE ty_context.
> lo_wf_inst_ctxt->get_instance_context( EXPORTING iv_cpwf_handle = <cpwf_handle> io_cp_json = lo_cp_json IMPORTING data = ls_context ).
> 
> ```



**Cancel Workflow Capability Instances**

To register a running workflow capability instance for cancelation, use the `registerWorkflowCancel` action using the command:

> ### Sample Code:  
> Example: EML Cancel
> 
> ```
> 
> MODIFY ENTITIES OF i_cpwf_inst
>       ENTITY CPWFInstance
>       EXECUTE registerWorkflowCancel
>       FROM VALUE #( ( %key = '<a UUID which is mandatory for mass enabled callers>' ) ).
> 
> ```

Note, that this action should be part of the interaction phase.

During the save sequence, the workflow instance is canceled in a background unit..

