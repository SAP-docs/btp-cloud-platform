<!-- loio1491e6c075c04e7c9a485a2e24b82653 -->

# Maintaining Application Jobs Using an API



You can use the `CL_APJ_RT_API` class to maintain application jobs. You can do the following:

-   schedule an application job

-   retrieve the status of an application job

-   cancel an application job

-   delete an application job


> ### Example:  
> > ### Sample Code:  
> > ```abap
> > class z_cl_rt_api_demo definition
> >   public
> >   final
> >   create public .
> > 
> >   public section.
> >     interfaces if_oo_adt_classrun.
> >   protected section.
> >   private section.
> > endclass.
> > 
> > 
> > 
> > class z_cl_rt_api_demo implementation.
> > 
> > " <SIGNATURE>---------------------------------------------------------------------------------------+
> > " | Instance Public Method Z_CL_RT_API_DEMO->IF_OO_ADT_CLASSRUN~MAIN
> > " +-------------------------------------------------------------------------------------------------+
> > " | [--->] OUT                            TYPE REF TO IF_OO_ADT_CLASSRUN_OUT
> > " +--------------------------------------------------------------------------------------</SIGNATURE>
> >   method if_oo_adt_classrun~main.
> > 
> >     data lv_job_text type cl_apj_rt_api=>ty_job_text value 'Demo_Job'.
> > 
> >     data lv_template_name type cl_apj_rt_api=>ty_template_name.
> > 
> >     data ls_start_info type cl_apj_rt_api=>ty_start_info.
> >     data ls_scheduling_info type cl_apj_rt_api=>ty_scheduling_info.
> >     data ls_end_info type cl_apj_rt_api=>ty_end_info.
> > 
> >     data lt_job_parameters type cl_apj_rt_api=>tt_job_parameter_value.
> >     data ls_job_parameters type cl_apj_rt_api=>ty_job_parameter_value.
> >     data ls_value type cl_apj_rt_api=>ty_value_range.
> > 
> >     data lv_jobname type cl_apj_rt_api=>ty_jobname.
> >     data lv_jobcount type cl_apj_rt_api=>ty_jobcount.
> > 
> >     data lv_status type cl_apj_rt_api=>ty_job_status.
> >     data lv_statustext type cl_apj_rt_api=>ty_job_status_text.
> > 
> >     data lv_txt type string.
> >     data ls_ret type bapiret2.
> > 
> > " Choose the name of the existing job template.
> >     lv_template_name = 'ZTEST_MY_SIMPLE_JOB_TEMP'.
> > 
> > " The immediate start can't be used when being called from within a RAP business object
> > " because the underlying API performs an implicit COMMIT WORK.
> > "   ls_start_info-start_immediately = 'X'.
> > 
> > " Start the job using a timestamp instead. This will start the job immediately but can have a delay depending on the current workload.
> >     get time stamp field data(ls_ts1).
> > " Add 1 hour
> >     data(ls_ts2) = cl_abap_tstmp=>add( tstmp = ls_ts1
> >                                        secs  = 3600 ).
> > 
> >     ls_start_info-timestamp = ls_ts2.
> > 
> > " Periodicity
> > 
> >     ls_scheduling_info-periodic_granularity = 'D'.
> >     ls_scheduling_info-periodic_value = 1.
> >     ls_scheduling_info-test_mode = abap_false.
> >     ls_scheduling_info-timezone = 'CET'.
> > 
> >     ls_end_info-type = 'NUM'.
> >     ls_end_info-max_iterations = 3.
> > 
> > " Fill parameter table:
> > " Fill the table only if you want to overrule the parameter values
> > " which are stored in the template.
> > " The field names in this program must match the field names of the template.
> > 
> >     ls_job_parameters-name = 'P_TEST1'.
> > 
> >     ls_value-sign = 'I'.
> >     ls_value-option = 'EQ'.
> >     ls_value-low = 'Test 1'.
> >     append ls_value to ls_job_parameters-t_value.
> > 
> >     append ls_job_parameters to lt_job_parameters.
> >     clear ls_job_parameters.
> > 
> >     ls_job_parameters-name = 'P_TEST2'.
> > 
> >     ls_value-sign = 'I'.
> >     ls_value-option = 'BT'.
> >     ls_value-low = 'ATEST'.
> >     ls_value-high = 'ZTEST'.
> >     append ls_value to ls_job_parameters-t_value.
> > 
> >     ls_job_parameters-name = 'P_TEST2'.
> > 
> >     ls_value-sign = 'I'.
> >     ls_value-option = 'BT'.
> >     ls_value-low = '11111'.
> >     ls_value-high = '99999'.
> >     append ls_value to ls_job_parameters-t_value.
> > 
> >     append ls_job_parameters to lt_job_parameters.
> >     clear ls_job_parameters.
> > 
> >     ls_job_parameters-name = 'P_TEST3'.
> > 
> >     ls_value-sign = 'I'.
> >     ls_value-option = 'EQ'.
> >     ls_value-low = '220'.
> >     append ls_value to ls_job_parameters-t_value.
> > 
> >     append ls_job_parameters to lt_job_parameters.
> >     clear ls_job_parameters.
> > 
> >     try.
> > 
> > " Some scenarios require that the job key ( = jobname, jobcount) is already known
> > " before the job is created. The method generate_jobkey creates a valid job key.
> > " This key can then be passed later on to the method schedule_job, and a job with
> > " exactly this key is created.
> > 
> > " Optional. You need this call only if you have to know the job key in advance.
> > "        cl_apj_rt_api=>generate_jobkey(
> > "          importing
> > "            ev_jobname  = lv_jobname
> > "            ev_jobcount = lv_jobcount ).
> > 
> > " If you pass the table lt_job_parameters , then the parameters
> > " contained in this table are used.
> > " If you don't pass the table, the parameters contained in the
> > " job template are used.
> > 
> >         cl_apj_rt_api=>schedule_job(
> >           exporting
> >             iv_job_template_name   = lv_template_name
> >             iv_job_text            = lv_job_text
> >             is_start_info          = ls_start_info
> >             is_scheduling_info     = ls_scheduling_info
> >             is_end_info            = ls_end_info
> >             it_job_parameter_value = lt_job_parameters
> > " The following two parameters are optional. If you pass them, they must have been generated
> > " with the optional call generate_jobkey above.
> > "           iv_jobname             = lv_jobname
> > "           iv_jobcount            = lv_jobcount
> >           importing
> >             ev_jobname             = lv_jobname
> >             ev_jobcount            = lv_jobcount
> >         ).
> > 
> >         out->write( lv_jobname ).
> >         out->write( lv_jobcount ).
> > 
> >         cl_apj_rt_api=>get_job_status(
> >           exporting
> >             iv_jobname         = lv_jobname
> >             iv_jobcount        = lv_jobcount
> >           importing
> >             ev_job_status      = lv_status
> >             ev_job_status_text = lv_statustext
> >         ).
> > 
> >         out->write( lv_status ).
> >         out->write( lv_statustext ).
> > 
> > " Via the following method you can cancel the job
> > " in the application job context 'cancel' means (as in the Fiori app):
> > " 1. if the job is running, it will be canceled
> > " 2. if the job has not yet started, it will be deleted.
> > " In case the job is periodic, the whole periodicity chain is deleted.
> > 
> >         cl_apj_rt_api=>cancel_job(
> >           exporting
> >             iv_jobname  = lv_jobname
> >             iv_jobcount = lv_jobcount
> >         ).
> >       catch cx_apj_rt into data(exc).
> >         lv_txt = exc->get_longtext( ).
> >         ls_ret = exc->get_bapiret2( ).
> >         out->write( 'ERROR:' ).
> >         out->write( lv_txt ).
> >         out->write( 'msg type =' ).
> >         out->write( ls_ret-type ).
> >         out->write( 'msg id =' ).
> >         out->write( ls_ret-id ).
> >         out->write( 'msg number =' ).
> >         out->write( ls_ret-number ).
> >         out->write( 'msg message =' ).
> >         out->write( ls_ret-message ).
> >     endtry.
> > 
> >   endmethod.
> > 
> > endclass.
> > ```

