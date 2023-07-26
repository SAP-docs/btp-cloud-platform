<!-- loio1491e6c075c04e7c9a485a2e24b82653 -->

# Maintaining Application Jobs using an API



You can use the `CL_APJ_RT_API` class to maintain application jobs. You can do the following:

-   schedule an application job

-   retrieve the status of an application job

-   cancel an application job

-   delete an application job


> ### Example:  
> > ### Sample Code:  
> > ```abap
> > CLASS z_cl_rt_api_demo DEFINITION
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
> >     DATA lv_job_text TYPE cl_apj_rt_api=>ty_job_text VALUE 'Demo_Job 2'.
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
> > * choose the name of the existing job template !
> >     lv_template_name = 'ZTEST_MY_SIMPLE_JOB_TEMPL'.
> > 
> > * in the commented lines below you see, how we define
> > * start time = current time + 1 hour
> > 
> > 
> > * Start the job using a timestamp instead.
> > *    GET TIME STAMP FIELD DATA(ls_ts1).
> > * add 1 hour
> > *    DATA(ls_ts2) = cl_abap_tstmp=>add( tstmp = ls_ts1
> > *                                     secs = 3600 ).
> > 
> > *    ls_start_info-timestamp = ls_ts2.
> > 
> > * in our example we choose immediate start
> >     ls_start_info-start_immediately = 'X'.
> > 
> > ********** periodicity ******************************
> > 
> >     ls_scheduling_info-periodic_granularity = 'D'. "daily
> >     ls_scheduling_info-periodic_value = 1.
> >     ls_scheduling_info-test_mode = abap_false.
> >     ls_scheduling_info-timezone = 'CET'.
> > 
> >     ls_end_info-type = 'NUM'.
> >     ls_end_info-max_iterations = 3.  " three reoccurrences
> > 
> > * fill parameter table ******************************
> > * fill the table only if you want to overrule the parameter values
> > * which are stored in the template
> > * the field names in this program must match the field names of the template
> > 
> > 
> >     ls_job_parameters-name = 'S_ID'.
> > 
> >     ls_value-sign = 'I'.
> >     ls_value-option = 'EQ'.
> >     ls_value-low = '4712'.
> >     APPEND ls_value TO ls_job_parameters-t_value.
> > 
> >     ls_job_parameters-name = 'S_ID'.
> > 
> >     ls_value-sign = 'I'.
> >     ls_value-option = 'EQ'.
> >     ls_value-low = '4713'.
> >     APPEND ls_value TO ls_job_parameters-t_value.
> > 
> >     APPEND ls_job_parameters TO lt_job_parameters.
> >     CLEAR ls_job_parameters.
> > 
> > *+++++++++++++++++++++++++
> > 
> >     ls_job_parameters-name = 'P_DESCR'.
> > 
> >     ls_value-sign = 'I'.
> >     ls_value-option = 'EQ'.
> >     ls_value-low = 'New Description'.
> >     ls_value-high = ''.
> > 
> >     APPEND ls_value TO ls_job_parameters-t_value.
> > 
> >     APPEND ls_job_parameters TO lt_job_parameters.
> >     CLEAR ls_job_parameters.
> > *+++++++++++++++++++++++++
> > 
> >     ls_job_parameters-name = 'P_COUNT'.
> > 
> >     ls_value-sign = 'I'.
> >     ls_value-option = 'EQ'.
> >     ls_value-low = '300'.
> >     APPEND ls_value TO ls_job_parameters-t_value.
> > 
> >     APPEND ls_job_parameters TO lt_job_parameters.
> >     CLEAR ls_job_parameters.
> > 
> > *****************************************************
> > 
> >     TRY.
> > 
> > * at the beginning we can check, if the user has the authorization at all to schedule the job
> > 
> >         data(can_schedule) = cl_apj_rt_api=>can_schedule_job(
> >                                  exporting
> >                                      iv_job_template_name = lv_template_name ).
> > 
> >         out->write( 'can_schedule:' ).    out->write( can_schedule ).
> > 
> > * some scenarios require that the job key ( = jobname, jobcount) is already known
> > * before the job is created. The method generate_jobkey creates a valid job key.
> > * This key can then be passed later on to the method schedule_job, and a job with
> > * exactly this key is created.
> > 
> > * optional. You need this call only if you have to know the job key in advance
> > *       cl_apj_rt_api=>generate_jobkey(
> > *                       importing
> > *                            ev_jobname  = lv_jobname
> > *                            ev_jobcount = lv_jobcount ).
> > 
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
> > * the following two parameters are optional. If you pass them, they must have been generated
> > * with the call of generate_jobkey above
> > *        iv_jobname  = lv_jobname
> > *        iv_jobcount = lv_jobcount
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
> > * 1. if the job is running, it will be canceled
> > * 2. if the job has not yet started, it will be deleted.
> > * In case the job is periodic, the whole periodicity chain is deleted.
> > 
> > *        cl_apj_rt_api=>cancel_job(
> > *        EXPORTING
> > *        iv_jobname = lv_jobname
> > *        iv_jobcount = lv_jobcount
> > *        ).
> > 
> > * read the details of the job
> > 
> >         data: ls_job_info  type cl_apj_rt_api=>ty_job_info.
> > 
> >         ls_job_info = cl_apj_rt_api=>get_job_details( iv_jobname  = lv_jobname
> >                                                    iv_jobcount = lv_jobcount ).
> > 
> > * write some details
> >         out->write( 'job text:' ).       out->write( ls_job_info-job_text ).
> >         out->write( 'job catalog:' ).    out->write( ls_job_info-catalog ).
> >         out->write( 'job template:' ).   out->write( ls_job_info-template ).
> > 
> > 
> > * read the step list of the job (in this case only 1 step)
> > 
> >         data: lt_steplist type cl_apj_rt_api=>tt_step_list.
> > 
> >         lt_steplist = cl_apj_rt_api=>get_steplist_of_job( iv_jobname  = lv_jobname
> >                                                        iv_jobcount = lv_jobcount ).
> > 
> > * write some step info
> >         loop at lt_steplist into data(wa_steplist).
> >            out->write( 'Highest log severity:' ).       out->write( wa_steplist-step_log_severity ).
> >            out->write( 'has result list:' ).            out->write( wa_steplist-step_has_results ).
> >         endloop.
> > 
> > 
> > * copy the above job
> >         data: lv_copy_job_text      type CL_APJ_RT_API=>TY_JOB_TEXT.
> >         data: lv_copy_jobname       type CL_APJ_RT_API=>TY_jobname.
> >         data: lv_copy_jobcount      type CL_APJ_RT_API=>TY_jobcount.
> > 
> >         lv_copy_job_text = 'copied job'.
> > 
> >         CALL METHOD cl_apj_rt_api=>copy_job(
> >            EXPORTING
> >               IV_SOURCE_JOBNAME  = lv_jobname
> >               IV_SOURCE_JOBCOUNT = lv_jobcount
> >               IV_JOB_TEXT        = lv_copy_job_text
> >               IS_START_INFO      = ls_start_info
> >            IMPORTING
> >               EV_NEW_JOBNAME     = lv_copy_jobname
> >               EV_NEW_JOBCOUNT    = lv_copy_jobcount ).
> > 
> > 
> > 
> >       CATCH cx_apj_rt INTO DATA(exc).
> >         lv_txt = exc->get_longtext( ).
> >         ls_ret = exc->get_bapiret2( ).
> >         out->write( 'ERROR:' ). out->write( lv_txt ).
> >         out->write( 'msg type =' ). out->write( ls_ret-type ).
> >         out->write( 'msg id =' ). out->write( ls_ret-id ).
> >         out->write( 'msg number =' ). out->write( ls_ret-number ).
> >         out->write( 'msg message =' ). out->write( ls_ret-message ).
> > 
> > 
> > 
> >     ENDTRY.
> > 
> >   ENDMETHOD.
> > ENDCLASS.
> > 
> > ```

