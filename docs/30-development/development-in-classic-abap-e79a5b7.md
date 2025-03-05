<!-- loioe79a5b768e7a4d94b7aad204653475c6 -->

# Development in Classic ABAP

To retrive only relevant parts of the workflow instance context the respective APIs have been enhanced with an additional parameter `IV_CONTEXT_PATH` that accepts any JSON path expression.

This expression is forwarded to the Workflow API of SAP Build Process Automation \(not supported by SAP Workflow Management\). The JSON path expression is evaluated by the SBPA Workflow Service API, which returns then only the corresponding substructure of the context.

This feature is introduced to support MDG usecase after migrating from SAP Workflow Management to SAP Build Process Automation, when the complete context became incompatible to ABAP structures used by MDG. With specifying the JSON path the stable part of the context, which is still compatible to the ABAP structure, can be extracted.

> ### Sample Code:  
> Reading context with JSON Path
> 
> ```
> ...
>     TYPES: BEGIN OF ty_context,
>              some_result TYPE string,
>            END OF ty_context.
>  
>     TRY.
>         DATA(lo_cpwf_api) = cl_swf_cpwf_api_factory...=>get_api_instance( ... ).
>         data(lv_context_json) = lo_cpwf_api->get_workflow_context( iv_cpwf_handle = iv_cpwf_handle
>                                                                    iv_context_path = 'someResult' ).
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
>         " Exception handling
>     ENDTRY.
> ...
> ```

> ### Sample Code:  
> Reading Context with JSON Path \(Core API\)
> 
> ```
> TYPES: BEGIN OF ty_context,
>          attr1 TYPE string,
>          attr2 TYPE int4,
>          attr3 TYPE string,
>        END OF ty_context.     
>  
> " Get a Instance for the CPWF Integration API
> DATA(lo_cpwf_api) = cl_swf_cpwf_api_factory...=>get_api_instance( ... ).  DATA(lo_cp_json) = lo_cpwf_api->get_json_converter( ).
> DATA(lo_wf_inst_ctxt) = lo_cpwf_api->if_swf_cpwf_capi~get_wf_instance_context_api( ).
>   
> DATA ls_context TYPE ty_context.
> lo_wf_inst_ctxt->get_instance_context( EXPORTING iv_cpwf_handle  = <cpwf_handle>
>                                                  iv_context_path = 'someJSONPath'
>                                                  io_cp_json      = lo_cp_json
>                                        IMPORTING data = ls_context ).
> ```

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
>         "outcome": "APPROVED"
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
> 
> ```

> ### Sample Code:  
> Get Context with JSONPath "custom"
> 
> ```
> {
>     "approver": "userx@sap.com",
>     "outcome": "APPROVED"
> }
> ```

> ### Sample Code:  
> Get Context with JSONPath "custom.outcome"
> 
> ```
> 
> "APPROVED"
> ```

