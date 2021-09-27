<!-- loio1491e6c075c04e7c9a485a2e24b82653 -->

# Maintaining Application Jobs using an API



You can use the `CL_APJ_RT_API` class to maintain application jobs. You can do the following:

-   schedule an application job

-   retrieve the status of an application job

-   cancel an application job

-   delete an application job


> ### Example:  
> > ### Sample Code:  
> > ```
> > 
> >  CLASS z_cl_rt_api_demo DEFINITION
> >   PUBLIC
> >   FINAL
> >   CREATE PUBLIC .
> > 
> >   PUBLIC SECTION.
> >     INTERFACES if_oo_adt_classrun.
> >   PROTECTED SECTION.
> >   PRIVATE SECTION.
> > ENDCLASS.
> > 
> > 
> > 
> > CLASS z_cl_rt_api_demo IMPLEMENTATION.
> > 
> >   METHOD if_oo_adt_classrun~main.
> > 
> >     DATA lv_job_text TYPE cl_apj_rt_api=>ty_job_text VALUE 'Demo_Job'.
> > 
> >     DATA lv_template_name TYPE cl_apj_rt_api=>ty_template_name.
> > 
> >     DATA ls_start_info TYPE cl_apj_rt_api=>ty_start_info.
> >     DATA ls_scheduling_info TYPE cl_apj_rt_api=>ty_scheduling_info.
> >     DATA ls_end_info TYPE cl_apj_rt_api=>ty_end_info.
> > 
> >     DATA lt_job_parameters TYPE cl_apj_rt_api=>tt_job_parameter_value.
> >     DATA ls_job_parameters TYPE cl_apj_rt_api=>ty_job_parameter_value.
> >     DATA ls_value TYPE cl_apj_rt_api=>ty_value_range.
> > 
> >     DATA lv_jobname TYPE cl_apj_rt_api=>ty_jobname.
> >     DATA lv_jobcount TYPE cl_apj_rt_api=>ty_jobcount.
> > 
> >     DATA lv_status TYPE cl_apj_rt_api=>ty_job_status.
> >     DATA lv_statustext TYPE cl_apj_rt_api=>ty_job_status_text.
> > 
> >     DATA lv_txt TYPE string.
> >     DATA ls_ret TYPE bapiret2.
> > 
> > * choose name of existing job template !!!!
> >     lv_template_name = 'ZTEST_MY_SIMPLE_JOB_TEMP'.
> > 
> > * immediate start
> > *ls_start_info-start_immediately = 'X'.
> > 
> > * alternatively with timestamp:
> >     GET TIME STAMP FIELD DATA(ls_ts1).
> > * add 1 hour
> >     DATA(ls_ts2) = cl_abap_tstmp=>add( tstmp = ls_ts1
> >                                      secs = 3600 ).
> > 
> >     ls_start_info-timestamp = ls_ts2.
> > 
> > ********** periodicity ******************************
> > 
> >     ls_scheduling_info-periodic_granularity = 'D'.
> >     ls_scheduling_info-periodic_value = 1.
> >     ls_scheduling_info-test_mode = abap_false.
> >     ls_scheduling_info-timezone = 'CET'.
> > 
> >     ls_end_info-type = 'NUM'.
> >     ls_end_info-max_iterations = 3.
> > 
> > * fill parameter table ******************************
> > * fill the table only, if you want to overrule the parameter values,
> > * which are stored in the template
> > * the field names in this program must match the field names of the template
> > 
> >     ls_job_parameters-name = 'P_TEST1'.
> > 
> >     ls_value-sign = 'I'.
> >     ls_value-option = 'EQ'.
> >     ls_value-low = 'Blabla 1'.
> >     APPEND ls_value TO ls_job_parameters-t_value.
> > 
> >     APPEND ls_job_parameters TO lt_job_parameters.
> >     CLEAR ls_job_parameters.
> > *+++++++++++++++++++++++++
> > 
> >     ls_job_parameters-name = 'P_TEST2'.
> > 
> >     ls_value-sign = 'I'.
> >     ls_value-option = 'BT'.
> >     ls_value-low = 'ATEST'.
> >     ls_value-high = 'ZTEST'.
> >     APPEND ls_value TO ls_job_parameters-t_value.
> > 
> >     ls_job_parameters-name = 'P_TEST2'.
> > 
> >     ls_value-sign = 'I'.
> >     ls_value-option = 'BT'.
> >     ls_value-low = '11111'.
> >     ls_value-high = '99999'.
> >     APPEND ls_value TO ls_job_parameters-t_value.
> > 
> >     APPEND ls_job_parameters TO lt_job_parameters.
> >     CLEAR ls_job_parameters.
> > *+++++++++++++++++++++++++
> > 
> >     ls_job_parameters-name = 'P_TEST3'.
> > 
> >     ls_value-sign = 'I'.
> >     ls_value-option = 'EQ'.
> >     ls_value-low = '220'.
> >     APPEND ls_value TO ls_job_parameters-t_value.
> > 
> >     APPEND ls_job_parameters TO lt_job_parameters.
> >     CLEAR ls_job_parameters.
> > 
> > *****************************************************
> > 
> >     TRY.
> > 
> > * If you pass the table lt_job_parameters , then the parameters
> > * contained in this table are used.
> > * If you don't pass the table, the parameters contained in the
> > * job template are used.
> > 
> >         cl_apj_rt_api=>schedule_job(
> >         EXPORTING
> >         iv_job_template_name = lv_template_name
> >         iv_job_text = lv_job_text
> >         is_start_info = ls_start_info
> >         is_scheduling_info = ls_scheduling_info
> >         is_end_info = ls_end_info
> >         it_job_parameter_value = lt_job_parameters
> >         IMPORTING
> >         ev_jobname  = lv_jobname
> >         ev_jobcount = lv_jobcount
> >         ).
> > 
> >         out->write( lv_jobname ).
> >         out->write( lv_jobcount ).
> > 
> >         cl_apj_rt_api=>get_job_status(
> >         EXPORTING
> >         iv_jobname  = lv_jobname
> >         iv_jobcount = lv_jobcount
> >         IMPORTING
> >         ev_job_status = lv_status
> >         ev_job_status_text = lv_statustext
> >         ).
> > 
> >         out->write( lv_status ).
> >         out->write( lv_statustext ).
> > 
> > * via the following method you can cancel the job
> > * in the application job context 'cancel' means (as in the Fiori app):
> > * 1. if the job is running, it will be cancelled
> > * 2. if the job has not yet started, it will be deleted.
> > * In case the job is periodic, the whole periodicity chain is deleted.
> > 
> >         cl_apj_rt_api=>cancel_job(
> >         EXPORTING
> >         iv_jobname = lv_jobname
> >         iv_jobcount = lv_jobcount
> >         ).
> >       CATCH cx_apj_rt INTO DATA(exc).
> >         lv_txt = exc->get_longtext( ).
> >         ls_ret = exc->get_bapiret2( ).
> >         out->write( 'ERROR:' ). out->write( lv_txt ).
> >         out->write( 'msg type =' ). out->write( ls_ret-type ).
> >         out->write( 'msg id =' ). out->write( ls_ret-id ).
> >         out->write( 'msg number =' ). out->write( ls_ret-number ).
> >         out->write( 'msg message =' ). out->write( ls_ret-message ).
> >     ENDTRY.
> > 
> >   ENDMETHOD.
> > ENDCLASS.
> > ```

