<!-- loioe79a5b768e7a4d94b7aad204653475c6 -->

# Development in Classic ABAP

The starting point is the class `CL_SWF_CPWF_API_FACTORY_A4C`. Once you have the API object of interface`IF_SWF_CPWF_API`, see the ABAP documentation on supported actions.



<a name="loioe79a5b768e7a4d94b7aad204653475c6__section_yws_n3g_42c"/>

## Starting SAP Build Process Automation process instances

Instances can be created with the following snippet:

> ### Sample Code:  
> Start a SAP Cloud Platform Workflow
> 
> ```abap
> TYPES: BEGIN OF ty_context,
>          some_property TYPE string,
>        END OF ty_context.
>  
> DATA(lo_cpwf_api) = cl_swf_cpwf_api_factory_a4c...=>get_api_instance( ... ).
>  
> DATA(ls_context) = VALUE ty_context(
>   some_property = 'someValue'
> ).
> DATA(lv_context_json) = lo_cpwf_api->get_start_context_from_data(
>   iv_data = ls_context
> ).
>  
> DATA(lv_cpwf_handle) = lo_cpwf_api->start_workflow(
>   iv_cp_workflow_def_id = '<SAP Workflow Service Process Definition Identifier>'
>   iv_context            = lv_context_json
>   iv_retention_time     = 30
>   iv_callback_class     = '<Callback class for final state handling>'
> ).
> ```



<a name="loioe79a5b768e7a4d94b7aad204653475c6__section_j54_y3g_42c"/>

## Registering SAP Build Process Automation process instances

If there is a running process instance in SAP Build Process automation which you would like to handle from within your S/4 Hana Application, you can register the instance in the following way:

> ### Sample Code:  
> Register a SAP Cloud Platform Workflow
> 
> ```
> 
> " Get a Instance for the CPWF Integration API
> DATA(lo_cpwf_api) = cl_swf_cpwf_api_factory_a4c...=>get_api_instance( ... ).
>  
> DATA(lv_cpwf_handle) = lo_cpwf_api->register_workflow(
>     iv_cp_workflow_inst_id = '<SAP Workflow Service Instance Identifier>'
>     iv_retention_time     = 30
>     iv_callback_class     = '<Callback class for final state handling>'
> ).
>  
> COMMIT WORK.
> ```



<a name="loioe79a5b768e7a4d94b7aad204653475c6__section_wjy_hjg_42c"/>

## Handling the result of SAP Build Process Automation process instances

As shown in the above snippets, a callback class can be provided that allows processing the result of the process. For example, it is possible to read the context of the completed instance.

> ### Sample Code:  
> Completion callback with reading context
> 
> ```
> METHOD if_swf_cpwf_callback~workflow_instance_completed.
>   TYPES: BEGIN OF ty_context,
>            some_result TYPE string,
>          END OF ty_context.
>  
>   TRY.
>       DATA(lo_cpwf_api) = cl_swf_cpwf_api_factory_a4c...=>get_api_instance( ... ).
>       data(lv_context_json) = lo_cpwf_api->get_workflow_context( iv_cpwf_handle = iv_cpwf_handle ).
>  
>       DATA ls_context TYPE ty_context.
>  
>       lo_cpwf_api->get_context_data_from_json(
>         EXPORTING
>           iv_context = lv_context_json
>        IMPORTING
>           ev_data = ls_context
>       ).
>     CATCH cx_swf_cpwf_api INTO DATA(lx_exc).
>       " Exception handling
>   ENDTRY.
>  
>   " your business coding
> ENDMETHOD.
> ```



<a name="loioe79a5b768e7a4d94b7aad204653475c6__section_jbb_wjg_42c"/>

## Raising an intermediate message event for a SAP Build Process Automation process instance

If the process expects a intermediate message event, this can be raised via the following code.

> ### Sample Code:  
> Raise an intermediate message event
> 
> ```
> TYPES: BEGIN OF ty_example_context,
>          value TYPE int4,
>        END OF ty_example_context.
>  
> " Get a Instance for the CPWF Integration API
> DATA(lo_cpwf_api) = cl_swf_cpwf_api_factory_a4c...=>get_api_instance( ... ).
>  
> " provide relevant event context data => in this case a meaningful integer
> DATA(lv_event_context_data) = VALUE ty_example_context( value = 4711 ).
> DATA(lv_event_context) = lo_cpwf_api->get_context_from_data( iv_data = lv_event_context_data ).
>  
> " actually raise the event
> lo_cpwf_api->raise_event(
>   EXPORTING
>     iv_cpwf_handle   = lv_cpwf_handle
>     iv_event_def_id  = '<Event Definition Identifier>'
>     iv_event_context = lv_event_context
> ).
>  
> COMMIT WORK.
> ```



<a name="loioe79a5b768e7a4d94b7aad204653475c6__section_wyg_3kg_42c"/>

## Retrieving the current state of SAP Build Process Automation process instances

It is also possible to synchronously retrieve data about the processes. It can be accessed via the interface `IF_SWF_CPWF_API`, which extends the core API IF\_SWF\_CPWF\_CAPI.

For example, you can query the current lifecycle status of processes.

> ### Sample Code:  
> Read Workflow Instances
> 
> ```
> " Get a Instance for the CPWF Integration API
> DATA(lo_cpwf_api) = cl_swf_cpwf_api_factory_a4c...=>get_api_instance( ... ).
> DATA(lo_wf_inst) = lo_cpwf_api->if_swf_cpwf_capi~get_workflow_instances_api( ).
>  
> DATA(lt_workflow_instance) = lo_wf_inst->query_instances(
>   iv_definition_id = '<SAP Workflow Service Process Definition Identifier>'
>   iv_status = if_swf_cpwf_capi_wf_insts=>cs_status-running
> ).
> ```

or retrieve the current context:

> ### Sample Code:  
> Read Workflow Instance Context
> 
> ```
> TYPES: BEGIN OF ty_context,
>          attr1 TYPE string,
>          attr2 TYPE int4,
>          attr3 TYPE string,
>        END OF ty_context.     
>  
> " Get a Instance for the CPWF Integration API
> DATA(lo_cpwf_api) = cl_swf_cpwf_api_factory_a4c...=>get_api_instance( ... ).  DATA(lo_cp_json) = lo_cpwf_api->get_json_converter( ).
> DATA(lo_wf_inst_ctxt) = lo_cpwf_api->if_swf_cpwf_capi~get_wf_instance_context_api( ).
>   
> DATA ls_context TYPE ty_context.
> lo_wf_inst_ctxt->get_instance_context( EXPORTING iv_cpwf_handle = <cpwf_handle> io_cp_json = lo_cp_json IMPORTING data = ls_context ).
> ```

As shown in the code there is also a JSON converter available to simplify the processing of the context.



<a name="loioe79a5b768e7a4d94b7aad204653475c6__section_tfc_rlg_42c"/>

## Restricting the retrieved process context

To allow retrieving only relevant parts of the process context the APIs `IF_SWF_CPWF_API` →get\_workflow\_context and `IF_SWF_CPWF_CAPI_WF_INST_CTXT`-\>get\_instance\_context allow to provide an additional parameter `IV_CONTEXT_PATH`, that accepts any JSON path expression \(see SBPA API description\). This expression is forwarded to the Workflow API of SAP Build Process Automation. The JSON path expression is evaluated by the SBPA Workflow Service API, which returns then only the corresponding substructure of the context.

The following examples show how the `IV_CONTEXT_PATH` parameter can be used.

> ### Sample Code:  
> Sample Context
> 
> ```
> {
>     "decision_travelRequestApproved_2": {
>         "outcome": "APPROVED"
>     },
>     "startEvent": {
>         "travelid": "1",
>         "createdby": "UserX",
>         "createdbymail": "userx@sap.com",
>         "enddate": "2025-02-28",
>         "startdate": "2025-02-01",
>         "destination": "Far Far Away"
>     },
>     "action_post_ProcessCompleted_2": {
>         "result": {
>             "notificationProcessed": true
>         }
>     },
>     "custom": {
>         "approver": "userx@sap.com",
>         "outcome": "APPROVED",
>         "destinations": [
>             {
>                 "date": "2025-02-01",
>                 "location": "here"
>             },
>             {
>                 "date": "2025-02-12",
>                 "location": "there"
>              }   
>         ]
>     },
>     "decision_determineRecipient_1": {
>         "Approver": "userx@sap.com"
>     },
>     "form_approveTravelRequest_1": {
>         "travelID": 1,
>         "requestor": "UserX",
>         "description_1": "Far Far Away",
>         "startDate": "2025-02-01",
>         "endDate": "2025-02-28"
>     }
> }
> ```

> ### Sample Code:  
> Get Context with JSONPath "custom"
> 
> ```
> {
>     "approver": "userx@sap.com",
>     "outcome": "APPROVED"
>     "destinations": [
>         {
>             "date": "2025-02-01",
>             "location": "here"
>         },
>         {
>             "date": "2025-02-12",
>             "location": "there"
>         }  
>     ]
> }
> ```

> ### Sample Code:  
> Get Context with JSONPath "custom.outcome"
> 
> ```
> "APPROVED"
> ```

> ### Sample Code:  
> Get Context with JSONPath "custom.outcome.destinations\[1\]"
> 
> ```
> {
>     "date": "2025-02-12",
>     "location": "there"
> }
> ```

> ### Sample Code:  
> Get Context with JSONPath "custom.outcome.destinations\[1\].location"
> 
> ```
> 
> "here"
> ```

