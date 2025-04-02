<!-- loio630ab6dcd7064ad3b9bf7d51b78711a2 -->

# Development in ABAP RESTful Application Programming Model \(RAP\)

Early Numbering: In the RAP version of the workflow service, API workflows can be registered via the command.

> ### Sample Code:  
> Example: EML Create
> 
> ```abap
> MODIFY ENTITIES OF i_cpwf_inst
>       ENTITY CPWFInstance
>       EXECUTE registerWorkflow
>       FROM VALUE #( ( %key = '<a UUID which is mandatory for mass enabled callers>'
>                       %param-RetentionTime = '<retention time in days>'
>                       %param-CpWfDefId = '<SAP Workflow Service Definition Id>'
>                       %param-CallbackClass = '<Callback class for final state handling>'                      
>                       %param-Consumer = '<SAP Workflow Scenario Id>') ).
> ```

> ### Note:  
> It's not allowed to call the `registerWorkflow` method multiple times with an identical set of parameters. This also applies to cases where the otherwise optional %key parameter stays empty. Therefore, if you want to use the `registerWorkflow` method in a mass-enabled context you must provide the unique %key parameter.

The parameters `RetentionTime`, `CpWfDefId`, and `Consumer` must be provided

The workflow context can be provided using the following EML statement:

> ### Sample Code:  
> Example: EML Create
> 
> ```abap
> MODIFY ENTITIES OF i_cpwf_inst
>       ENTITY CPWFInstance
>       EXECUTE setPayload
>       FROM VALUE #( ( %key-CpWfHandle = '<required key (UUID) of the CPWF instance>'
>                       %param-context = '<workflow context in JSON format>' ) ).
> ```

Both commands should be part of a determination on save. During save sequence the workflow is started with the provided data.

**Late Numbering**

As for early numbering, the `registerWorkflow` method can be called in a determination on save for late numbering, too.

The workflow context can be set even later in the `adjust_numbers` method of your business object using the `setPayload` method.

> ### Sample Code:  
> Example: EML Create
> 
> ```abap
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
> ```abap
> 
> MODIFY ENTITIES OF i_cpwf_inst
>       ENTITY CPWFInstance
>       EXECUTE registerWorkflowCancel
>       FROM VALUE #( ( %key = '<a UUID which is mandatory for mass enabled callers>' ) ).
> 
> ```

Note, that this action should be part of the interaction phase.

During the save sequence, the workflow instance is canceled in a background unit.

