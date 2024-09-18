<!-- loio232c4a8ff2d8422b93bc89151068b893 -->

# Examples of Periodic Application Jobs

You can schedule application jobs to run periodically.

Here, you'll find a few codesamples that specify various periodicities. These code samples use the new human-readable constants of the class `CL_APJ_RT_API`. Let's start with a codesample showing an application job that runs monthly, always on the second day of the month:

> ### Sample Code:  
> ```abap
> CLASS zcl_apj_monthly DEFINITION
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
> CLASS zcl_apj_monthly IMPLEMENTATION.
> 
> " <SIGNATURE>---------------------------------------------------------------------------------------+
> " | Instance Public Method ZCL_APJ_MONTHLY->IF_OO_ADT_CLASSRUN~MAIN
> " +-------------------------------------------------------------------------------------------------+
> " | [--->] OUT                            TYPE REF TO IF_OO_ADT_CLASSRUN_OUT
> " +--------------------------------------------------------------------------------------</SIGNATURE>
>   METHOD if_oo_adt_classrun~main.
> 
> " the following coding creates an application job with the following start condition:
> "
> " periodicity:  every month on the second day - starting September 2nd, 2024
> " first start:  specified by variable  ls_start_info-timestamp
> "
> " Exception rule: If the execution day is a non-working day according to a
> "                  specified calendar, the job should be skipped.
> "
> " End of series:   after 10 executions - specified by ls_end_info
> 
>     DATA job_text		  TYPE cl_apj_rt_api=>ty_job_text VALUE 'Monthly_Job'.
> 
>     DATA template_name       TYPE cl_apj_rt_api=>ty_template_name.
> 
>     DATA ls_start_info       TYPE cl_apj_rt_api=>ty_start_info.
>     DATA ls_scheduling_info  TYPE cl_apj_rt_api=>ty_scheduling_info.
>     DATA ls_job_exception    TYPE cl_apj_rt_api=>ty_job_exception.
> 
>     DATA ls_end_info         TYPE cl_apj_rt_api=>ty_end_info.
> 
>     DATA jobname             TYPE cl_apj_rt_api=>ty_jobname.
>     DATA jobcount            TYPE cl_apj_rt_api=>ty_jobcount.
> 
>     DATA status              TYPE cl_apj_rt_api=>ty_job_status.
>     DATA statustext          TYPE cl_apj_rt_api=>ty_job_status_text.
> 
>     DATA: txt TYPE string.
>     DATA: tz  TYPE timezone.
> 
>     DATA dat TYPE d.
>     DATA tim TYPE t.
> 
>     template_name = 'ZTEST_MY_SIMPLE_JOB_TEMP'.
> 
> " the immediate start would look like this:
> " ls_start_info-start_immediately = cl_apj_rt_api=>start_immediately.
> 
>     dat = '20240902'.
>     tim = '040000'.
> 
>     tz = cl_abap_tstmp=>get_system_timezone(  ).
> 
>     CONVERT DATE dat TIME tim
>             INTO TIME STAMP DATA(ts) TIME ZONE tz.
> 
>     ls_start_info-timestamp = ts.
> 
> " periodicity 
> 
>     ls_scheduling_info-periodic_granularity   = cl_apj_rt_api=>period_months. " monthly
>     ls_scheduling_info-periodic_value         = 1.
>     ls_scheduling_info-test_mode              = abap_false.
>     ls_scheduling_info-timezone               = tz.
> 
> " exception rule
>     ls_job_exception-calender_id = '01'.
>     ls_job_exception-start_restriction_code = cl_apj_rt_api=>dont_process_on_holiday.  "skip, if the execution day is a holiday
> 
>     ls_scheduling_info-exception = ls_job_exception.
> 
> " the periodic job should not run anymore after the 10th execution
>     ls_end_info-type = cl_apj_rt_api=>period_end_by_nr_of_executions.
>     ls_end_info-max_iterations = 10.
> 
>     TRY.
> 
>         cl_apj_rt_api=>schedule_job(
>           EXPORTING
>             iv_job_template_name = template_name
>             iv_job_text          = job_text
>             is_start_info        = ls_start_info
>             is_scheduling_info   = ls_scheduling_info
>             is_end_info          = ls_end_info
>             iv_jobname           = jobname
>             iv_jobcount          = jobcount
>           IMPORTING
>             ev_jobname           = jobname
>             ev_jobcount          = jobcount
>         ).
> 
>         CONCATENATE jobname jobcount INTO txt SEPARATED BY space.
>         out->write( txt ).
> 
>         cl_apj_rt_api=>get_job_status(
>           EXPORTING
>             iv_jobname         = jobname
>             iv_jobcount        = jobcount
>           IMPORTING
>             ev_job_status      = status
>             ev_job_status_text = statustext
>         ).
> 
>         CONCATENATE 'status =' statustext INTO txt SEPARATED BY space.
>         out->write( txt ).
> 
>       CATCH cx_apj_rt INTO DATA(exc).
>         txt = exc->get_longtext( ).
>         out->write( txt ).
>     ENDTRY.
> 
>   ENDMETHOD.
> ENDCLASS.
> 
> ```

You can specify more periodicities with the method `CL_APJ_RT_API=>SCHEDULE_JOB`. The code snippets below show and explain in comments how to fill the method's parameters `IS_START_INFO`, `IS_SCHEDULING_INFO` \(including the substructures `EXCEPTION`, `WEEKDAY_INFO`, and `MONTH_INFO`\), and `IS_END_INFO`.

> ### Note:  
> Note that there are hard-coded dates and times in the examples.

Each of the examples needs the following data definitions \(or at least a subset\):

> ### Sample Code:  
> ```abap
> DATA ls_start_info       TYPE cl_apj_rt_api=>ty_start_info.  "for method parameter IS_START_INFO
> DATA ls_scheduling_info  TYPE cl_apj_rt_api=>ty_scheduling_info. "for method parameter IS_SCHEDULING_INFO
> DATA ls_job_exception    TYPE cl_apj_rt_api=>ty_job_exception. "substructure of ls_scheduling_info
> DATA ls_weekday_info     TYPE cl_apj_rt_api=>ty_weekday_info. "substructure of ls_scheduling_info
> DATA ls_month_info       TYPE cl_apj_rt_api=>ty_month_info.  "substructure of ls_scheduling_info
> DATA ls_end_info         TYPE cl_apj_rt_api=>ty_end_info. "for method parameter IS_END_INFO
> 
> DATA tz  TYPE timezone.
> DATA dat TYPE d.
> DATA tim TYPE t.
> DATA ts TYPE timestamp.
> ```

**Example 1**

This code snippet shows how to specify the start condition of the periodicity of the fourth from the last day every month, starting from 28 January, 2024. Its first start is specified by the variable `LS_START_INFO-TIMESTAMP`. The application job stops running after ten executions, specified by `LS_END_INFO`.

> ### Sample Code:  
> ```abap
> " the immediate start would look like this:
> " ls_start_info-start_immediately = cl_apj_rt_api=>start_immediately.
> 
> dat = '20241028'.  "should be the exact date of the first execution
> tim = '040000'.
> 
> tz = cl_abap_tstmp=>get_system_timezone(  ).
> 
> CONVERT DATE dat TIME tim
>         INTO TIME STAMP ts TIME ZONE tz.
> 
> ls_start_info-timestamp = ts.
> 
> " periodicity
> 
> ls_scheduling_info-periodic_granularity   = cl_apj_rt_api=>period_months.
> ls_scheduling_info-periodic_value         = 1.
> ls_scheduling_info-test_mode              = abap_false.
> ls_scheduling_info-timezone               = tz.
> 
> ls_month_info-day = 4.
> ls_month_info-shift_direction = cl_apj_rt_api=>from_end_of_month.
> 
> " there is also the constant
> " cl_apj_rt_api=>FROM_BEGINNING_OF_MONTH
> 
> ls_scheduling_info-month_info   = ls_month_info.
> 
> " the periodic job should not run anymore after the 10th execution
> ls_end_info-type = cl_apj_rt_api=>period_end_by_nr_of_executions.
> ls_end_info-max_iterations = 10.
> ```

**Example 2**

This code snippet shows how to specify the start condition of the periodicity of the second day of every month, starting from 2 September, 2024. Its first start is specified by the variable `LS_START_INFO-TIMESTAMP`. The exception rule is that if the execution day is a non-working day according to a specified calendar, the job should be skipped. The application job stops running after ten executions, specified by `LS_END_INFO`.

> ### Sample Code:  
> ```abap
> " the immediate start would look like this:
> " ls_start_info-start_immediately = cl_apj_rt_api=>start_immediately.
> 
> dat = '20240902'.
> tim = '040000'.
> 
> tz = cl_abap_tstmp=>get_system_timezone(  ).
> 
> CONVERT DATE dat TIME tim
>         INTO TIME STAMP ts TIME ZONE tz.
> 
> ls_start_info-timestamp = ts.
> 
> " periodicity
> 
> ls_scheduling_info-periodic_granularity   = cl_apj_rt_api=>period_months. " monthly
> ls_scheduling_info-periodic_value         = 1.
> ls_scheduling_info-test_mode              = abap_false.
> ls_scheduling_info-timezone               = tz.
> 
> " exception rule
> ls_job_exception-calender_id = '01'.
> ls_job_exception-start_restriction_code = cl_apj_rt_api=>dont_process_on_holiday.  "skip if the execution day is a holiday
> 
> " There are also the following constants for exception rules (names are self-explanatory):
> " cl_apj_rt_api=>PROCESS_BEFORE_HOLIDAY
> " cl_apj_rt_api=>PROCESS_AFTER_HOLIDAY
> " cl_apj_rt_api=>PROCESS_ALWAYS
> 
> ls_scheduling_info-exception = ls_job_exception.
> 
> " the periodic job should not run anymore after the 10th execution
> ls_end_info-type = cl_apj_rt_api=>period_end_by_nr_of_executions.
> ls_end_info-max_iterations = 10.
> ```

**Example 3**

This code snippet shows how to specify the start condition of the periodicity of every week on Monday and Thursday. Its first start is specified by the variable `LS_START_INFO-TIMESTAMP`. The application job stops running after a specific time, specified by `LS_END_INFO-TIMESTAMP`.

> ### Note:  
> The application job start in this code snippet has to match a valid start date \(a Monday or a Thursday\).

> ### Sample Code:  
> ```abap
> " the immediate start would look like this
> " ls_start_info-start_immediately = cl_apj_rt_api=>start_immediately.
> 
> " In the following the assignment
> "      dat
> " must be a Monday or a Thursday, because the job should run
> " every week on Monday and Thursday.
> " Otherwise, an error will be reported.
> " So the variable
> "   ls_start_info-timestamp
> " will be the start date and time of the series.
> 
> dat = '20240219'.
> tim = '180000'.
> 
> tz = cl_abap_tstmp=>get_system_timezone(  ).
> 
> CONVERT DATE dat TIME tim
>         INTO TIME STAMP ts TIME ZONE tz.
> 
> ls_start_info-timestamp = ts.
> 
> " periodicity
> 
> " the job should run every third Tuesday of the month
> ls_weekday_info-on_monday      = abap_true.
> ls_weekday_info-on_thursday    = abap_true.
> 
> ls_scheduling_info-periodic_granularity   = cl_apj_rt_api=>period_weeks. " weekly
> ls_scheduling_info-periodic_value         = 1.
> ls_scheduling_info-test_mode              = abap_false.
> ls_scheduling_info-timezone               = tz.
> 
> ls_scheduling_info-weekday_info = ls_weekday_info.
> 
> " the periodic job should not run anymore after Dec. 31st 2030, 11:00 time zone tz (system time zone)
> ls_end_info-type = cl_apj_rt_api=>period_end_by_date.
> 
> dat = '20300331'.
> tim = '110000'.
> 
> CONVERT DATE dat TIME tim
>         INTO TIME STAMP ls_end_info-timestamp TIME ZONE tz.
> ```

**Example 4**

This code snippet shows how to specify the start condition of the periodicity of every week on Friday. Its first start is specified by the variable `LS_START_INFO-TIMESTAMP`. The exception rule is that if a Friday is a non-working day according to a specified calendar, the job should run on the next working day. The application job stops running at a specific day, specified by `LS_END_INFO-TIMESTAMP`.

> ### Note:  
> The application job start in this code snippet has to match a valid start date \(a Friday\).

> ### Sample Code:  
> ```abap
> " the immediate start would look like this
> " ls_start_info-start_immediately = cl_apj_rt_api=>start_immediately.
> 
> " In the following the assignment
> "      dat
> " must be a Friday, because the job should run
> " every week on Friday.
> " Otherwise, an error will be reported.
> " So the variable
> "   ls_start_info-timestamp
> " will be the start date and time of the series.
> 
> dat = '20240823'.
> tim = '040000'.
> 
> " alternatively, we can work with the system timezone
> " tz = CL_ABAP_TSTMP=>get_system_timezone(  ).
> 
> CONVERT DATE dat TIME tim
>         INTO TIME STAMP ts TIME ZONE 'CET'. "means: the first job should start at 4:00 CET
> 
> ls_start_info-timestamp = ts.
> 
> " periodicity
> 
> ls_scheduling_info-periodic_granularity   = cl_apj_rt_api=>period_weeks. " weekly
> ls_scheduling_info-periodic_value         = 1.
> ls_scheduling_info-test_mode              = abap_false.
> 
> " Below, the timezone for the periodicity is set. In combination with the above first start time 4:00
> " the periodicity time zone CET means: The job should always start at 4:00 CET - no matter if daylight savings time
> " is active or not.
> " If we don't set the periodicity timezone, it will be set to the system timezone by default. Let's assume UTC.
> " Since the first start date and time of the job is 20240223 040000 CET, it is 20240223 030000 UTC.
> " The job will then run at 3:00 UTC every Friday, which is 4:00 CET in 'winter' and 5:00 CET in 'summer'.
> 
> ls_scheduling_info-timezone               = 'CET'.
> 
> " the job should run every Friday
> ls_weekday_info-on_friday      = abap_true.
> 
> ls_scheduling_info-weekday_info = ls_weekday_info.
> 
> " exception rule
> ls_job_exception-calender_id = '01'.
> ls_job_exception-start_restriction_code = cl_apj_rt_api=>process_after_holiday.  "run on the next working day
> 
> ls_scheduling_info-exception = ls_job_exception.
> 
> 
> " the periodic job should not run anymore after Dec. 31st 2030, 11:00 time zone tz (system time zone)
> ls_end_info-type = cl_apj_rt_api=>period_end_by_date.
> 
> dat = '20300331'.
> tim = '110000'.
> 
> CONVERT DATE dat TIME tim
>         INTO TIME STAMP ls_end_info-timestamp TIME ZONE tz.
> ```

**Example 5**

This code snippet shows how to specify the start condition of the periodicity of the second Thursday of every month. Its first start is specified by the variable `LS_START_INFO-TIMESTAMP`. The application job stops running after 10 executions, specified by `LS_END_INFO`.

> ### Sample Code:  
> ```abap
> " the immediate start would look like this:
> " ls_start_info-start_immediately = cl_apj_rt_api=>start_immediately.
> 
> " start date and time of series
> 
> dat = '20240208'. " this date must match the date of the first job execution
> tim = '180000'.
> 
> tz = cl_abap_tstmp=>get_system_timezone(  ).
> 
> CONVERT DATE dat TIME tim
>         INTO TIME STAMP ts TIME ZONE tz.
> 
> ls_start_info-timestamp = ts.
> 
> " periodicity
> 
> ls_scheduling_info-periodic_granularity   = cl_apj_rt_api=>period_weekday_in_month.
> ls_scheduling_info-periodic_value         = 1.
> ls_scheduling_info-test_mode              = abap_false.
> ls_scheduling_info-timezone               = tz.
> 
> ls_weekday_info-on_thursday               = abap_true.
> 
> ls_scheduling_info-weekday_info  = ls_weekday_info.
> 
> 
> ls_month_info-week_number = 2.
> 
> ls_scheduling_info-month_info   = ls_month_info.
> 
> 
> " the periodic job should not run anymore after the 10th execution
> ls_end_info-type = cl_apj_rt_api=>period_end_by_nr_of_executions.
> ls_end_info-max_iterations = 10.
> ```

**New Constants of the Class `CL_APJ_RT_API`:**

For periodicity:

-   `CL_APJ_RT_API=>PERIOD_MINUTES`

-   `CL_APJ_RT_API=>PERIOD_HOURS`

-   `CL_APJ_RT_API=>PERIOD_DAYS`

-   `CL_APJ_RT_API=>PERIOD_WEEKS`

-   `CL_APJ_RT_API=>PERIOD_MONTHS`

-   `CL_APJ_RT_API=>PERIOD_WEEKDAY_IN_MONTH` \(see example 5\)


For immediate start:

-   `CL_APJ_RT_API=>START_IMMEDIATELY` \(used in all above examples, but commented out\)


For end of condition series:

-   `CL_APJ_RT_API=>PERIOD_END_BY_DATE` \(see example 5, for example\)

-   `CL_APJ_RT_API=>PERIOD_END_BY_NR_OF_EXECUTIONS` \(see example 2, for example\)


For count direction \(from the start or end of the month\):

-   `CL_APJ_RT_API=>FROM_BEGINNING_OF_MONTH` \(see example 1\)

-   `CL_APJ_RT_API=>FROM_END_OF_MONTH` \(see example 1\)


Exception rules \(how to treat an application job if the regular job execution is \(or would be\) on a holiday according to the specified calendar:

-   `CL_APJ_RT_API=>DONT_PROCESS_ON_HOLIDAY`

-   `CL_APJ_RT_API=>DONT_PROCESS_BEFORE_HOLIDAY` \(for example, on the last working day before the holiday\)

-   `CL_APJ_RT_API=>PROCESS_AFTER_HOLIDAY` \(for example, on the first working day after the holiday\)

-   `CL_APJ_RT_API=>PROCESS_ALWAYS`


Only relevant for the method `CL_APJ_RT_API=>RESTART_JOB`:

-   `CL_APJ_RT_API=>RESTART_FROM_ERROR_STEP`

-   `CL_APJ_RT_API=>RESTART_AFTER_ERROR_STEP`


