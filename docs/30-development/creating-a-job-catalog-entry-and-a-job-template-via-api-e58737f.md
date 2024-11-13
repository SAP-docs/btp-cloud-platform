<!-- loioe58737f463534a23bff0e9f21f7ee6d0 -->

# Creating a Job Catalog Entry and a Job Template via API

Find out how to create job catalog entries and job templates using a released API.

If you can't use the ABAP development tools for Eclipse to create job catalog entries and job templates, or of you have the requirement to create these objects via an ABAP class, you can use a released API. To use this API, you can use the ABAP class `CL_APJ_DT_CREATE_CONTENT`. The class offers the following methods:

-   `GET_INSTANCE` \(static\): Get an instance of class `CL_APJ_DT_CREATE_CONTENT`

-   `CREATE_JOB_CAT_ENTRY`: Create an application job catalog entry

-   `CREATE_JOB_TEMPLATE_ENTRY`: Create an application job template

-   `DELETE_JOB_CAT_ENTRY`: Delete an application job catalog entry

-   `DELETE_JOB_TEMPLATE_ENTRY`: Delete an application job template

-   `EXISTS_JOB_CAT_ENTRY`: Check the existence of an application job catalog entry

-   `EXISTS_JOB_TEMPLATE_ENTRY`: Check the existence of an application job template


The following code sample generates one job catalog entry and one related job template:

> ### Sample Code:  
> ```abap
> CLASS zcl_test_apj_simple_obj_gen DEFINITION
>   PUBLIC
>   FINAL
>   CREATE PUBLIC .
> 
>   PUBLIC SECTION.
>     INTERFACES if_oo_adt_classrun.
>   PROTECTED SECTION.
>   PRIVATE SECTION.
> ENDCLASS.
> 
> 
> CLASS zcl_test_apj_simple_obj_gen IMPLEMENTATION.
> 
>   METHOD if_oo_adt_classrun~main.
> 
>     CONSTANTS lc_catalog_name      TYPE cl_apj_dt_create_content=>ty_catalog_name  VALUE 'ZTEST_MY_SIMPLE_JOB'.
>     CONSTANTS lc_catalog_text      TYPE cl_apj_dt_create_content=>ty_text          VALUE 'My first simple application job'.
>     CONSTANTS lc_class_name        TYPE cl_apj_dt_create_content=>ty_class_name    VALUE 'ZCL_TEST_APJ_SIMPLE'.
> 
>     CONSTANTS lc_template_name     TYPE cl_apj_dt_create_content=>ty_template_name VALUE 'ZTEST_MY_SIMPLE_JOB_TEMPL'.
>     CONSTANTS lc_template_text     TYPE cl_apj_dt_create_content=>ty_text          VALUE 'My first simple job template'.
> 
>     CONSTANTS lc_transport_request TYPE cl_apj_dt_create_content=>ty_transport_request VALUE 'Y11K900361'.
>     CONSTANTS lc_package           TYPE cl_apj_dt_create_content=>ty_package           VALUE 'Z_D028092_APJ_MAIN'.
> 
>     DATA(lo_dt) = cl_apj_dt_create_content=>get_instance( ).
> 
>     " Create job catalog entry (corresponds to the former report incl. selection parameters)
>     " Provided implementation class iv_class_name shall implement two interfaces:
>     " - if_apj_dt_exec_object to provide the definition of all supported selection parameters of the job
>     "   (corresponds to the former report selection parameters) and to provide the actual default values
>     " - if_apj_rt_exec_object to implement the job execution
>     TRY.
>         lo_dt->create_job_cat_entry(
>             iv_catalog_name       = lc_catalog_name
>             iv_class_name         = lc_class_name
>             iv_text               = lc_catalog_text
>             iv_catalog_entry_type = cl_apj_dt_create_content=>class_based
>             iv_transport_request  = lc_transport_request
>             iv_package            = lc_package
>         ).
>         out->write( |Job catalog entry created successfully| ).
> 
>       CATCH cx_apj_dt_content INTO DATA(lx_apj_dt_content).
>         out->write( |Creation of job catalog entry failed: { lx_apj_dt_content->get_text( ) }| ).
>     ENDTRY.
> 
>     " Create job template (corresponds to the former system selection variant) which is mandatory
>     " to select the job later on in the Fiori app to schedule the job
>     DATA lt_parameters TYPE if_apj_dt_exec_object=>tt_templ_val.
> 
>     NEW zcl_test_apj_simple( )->if_apj_dt_exec_object~get_parameters(
>       IMPORTING
>         et_parameter_val = lt_parameters
>     ).
> 
>     TRY.
>         lo_dt->create_job_template_entry(
>             iv_template_name     = lc_template_name
>             iv_catalog_name      = lc_catalog_name
>             iv_text              = lc_template_text
>             it_parameters        = lt_parameters
>             iv_transport_request = lc_transport_request
>             iv_package           = lc_package
>         ).
>         out->write( |Job template created successfully| ).
> 
>       CATCH cx_apj_dt_content INTO lx_apj_dt_content.
>         out->write( |Creation of job template failed: { lx_apj_dt_content->get_text( ) }| ).
>         RETURN.
>     ENDTRY.
> 
>   ENDMETHOD.
> 
> ENDCLASS.
> ```

