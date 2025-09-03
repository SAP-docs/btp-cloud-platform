<!-- loio78173db86e244eada7783abb2371706a -->

# Example with Check Interface IF\_APJ\_JT\_CHECK\_20

Learn what you can do with the methods of the interface `IF_APJ_JT_CHECK_20`.



## Context

When you create a job catalog entry, you can add a check class. With the check class, you can implement useful functionalities to dynamically control the scheduling dialog. You can, for example, dynamically preset a field with a certain value, dynamically hide or show a field, or set a field to read-only.



## Procedure

A check class of a job catalog entry can implement some or all methods of the check interface `IF_APJ_JT_CHECK_20`. Here, you can learn what you can do with the methods of this interface. For this purpose, the example shows:

-   The class `zapj_sample_class`. This class fulfills the conditions for the new class-based application jobs concept. For more information, see [Example Implementation Using Interface IF\_APJ\_RT\_RUN](example-implementation-using-interface-if-apj-rt-run-3198dd0.md).

-   A screenshot of the job catalog entry `ZAPJ_JOB_CATALOG`. This job catalog entry refers to the class `zapj_sample_class` and defines further properties of the fields that are defined in the class

-   The class `zapj_sample_check_class`, which has been added as check class to the job catalog entry `ZAPJ_JOB_CATALOG`. This class contains the interface `IF_APJ_JT_CHECK_20` and has sample implementations of the interface methods, explained with comments


With the above objects, you can create a complete example, including a job template and a business role, as described in the different sections here: [Application Jobs](application-jobs-0837d1e.md).

> ### Note:  
> If you want to use the two classes mentioned above without changes, you must create:
> 
> -   The application log object `ZAPJ_LOGOBJ` with subobject `ZAPJ_SUBOBJ`
> 
> -   The message class `ZAPJ` with a message
> 
> -   Number: 001. Text: &1 &2

> ### Sample Code:  
> `zapj_sample_class`
> 
> ```abap
> " This class fulfills the conditions for the new class-based application jobs concept.
> 
> CLASS zapj_sample_class DEFINITION
>   PUBLIC
>   FINAL
>   CREATE PUBLIC .
> 
>   PUBLIC SECTION.
> 
>     INTERFACES if_apj_rt_run.
> 
>     TYPES char_20 TYPE c LENGTH 20.
>     TYPES char_10 TYPE c LENGTH 10.
> 
>     DATA chk  TYPE abap_bool.
>     DATA text TYPE char_20.
> 
>     DATA r1   TYPE abap_bool.
>     DATA r2   TYPE abap_bool.
> 
>     DATA multi_text TYPE RANGE OF char_20.
> 
>     DATA: read_o TYPE char_10. " will be used as read-only parameter
>     DATA: hidden TYPE char_10. " will be used as hidden parameter
> 
>   PROTECTED SECTION.
>   PRIVATE SECTION.
> ENDCLASS.
> 
> 
> 
> CLASS zapj_sample_class IMPLEMENTATION.
> 
>   METHOD if_apj_rt_run~execute.
> 
>     DATA logtext     TYPE string.
>     DATA exctext     TYPE string.
> 
>     TRY.
> 
> " log object and subobject must exist
>         DATA(l_log) = cl_bali_log=>create_with_header( cl_bali_header_setter=>create( object = 'ZAPJ_LOGOBJ'
>                                                                                       subobject = 'ZAPJ_SUBOBJ'
>                                                                                       external_id = 'My ID' ) ).
> " message class Z_APJ must exist.
>         MESSAGE ID 'ZAPJ' TYPE 'I' NUMBER '001' WITH 'text = ' text INTO logtext.
>         l_log->add_item( cl_bali_message_setter=>create_from_sy( ) ).
> 
>         MESSAGE ID 'ZAPJ' TYPE 'I' NUMBER '001' WITH 'read_o = ' read_o INTO logtext.
>         l_log->add_item( cl_bali_message_setter=>create_from_sy( ) ).
> 
>         MESSAGE ID 'ZAPJ' TYPE 'I' NUMBER '001' WITH 'hidden = ' hidden INTO logtext.
>         l_log->add_item( cl_bali_message_setter=>create_from_sy( ) ).
> 
>         cl_bali_log_db=>get_instance( )->save_log(
>                                                    log = l_log
>                                                    assign_to_current_appl_job = abap_true
>                                                  ).
> 
>       CATCH cx_bali_runtime INTO DATA(exc).
> "          appropriate error handling
>     ENDTRY.
> 
>   ENDMETHOD.
> 
> ENDCLASS.
> ```

![Screenshot of job catalog entry ZAPJ_JOB_CATALOG](images/4b15286a775c44798ebbb753294fc242.image)

**`zapj_sample_check_class` implements all methods of the interface `IF_APJ_JT_CHECK_20`. It's an example check class for the class `ZAPJ_SAMPLE_CLASS`. A check class that implements the interface `IF_APJ_JT_CHECK_20` should always inherit from the class `CL_APJ_JT_CHECK_BASE_20`. This base class contains dummy implementations of all check methods. They make sure that no error is caused if you don't implement all check methods in your own check class. All methods have - among others - the import parameter `IV_USERNAME`. This parameter contains the name of the job user. By default, this is the user that creates the job \(the job owner\). If the job is created via an API, a different job user can be specified. See also [3295193](https://me.sap.com/notes/3295193).**

> ### Sample Code:  
> `zapj_sample_check_class`
> 
> ```abap
> CLASS zapj_sample_check_class DEFINITION
>   PUBLIC
>   INHERITING FROM cl_apj_jt_check_base_20
>   FINAL
>   CREATE PUBLIC .
> 
>   PUBLIC SECTION.
>     METHODS if_apj_jt_check_20~initialize REDEFINITION.
>     METHODS if_apj_jt_check_20~check_start_condition REDEFINITION.
>     METHODS if_apj_jt_check_20~check_and_adjust_parameter REDEFINITION.
>     METHODS if_apj_jt_check_20~check_and_adjust REDEFINITION.
>     METHODS if_apj_jt_check_20~check_authorizations REDEFINITION.
>     METHODS if_apj_jt_check_20~get_dynamic_properties REDEFINITION.
>     METHODS if_apj_jt_check_20~adjust_read_only REDEFINITION.
>     METHODS if_apj_jt_check_20~adjust_hidden REDEFINITION.
> 
>   PROTECTED SECTION.
>   PRIVATE SECTION.
> ENDCLASS.
> 
> 
> CLASS zapj_sample_check_class
>   IMPLEMENTATION.
> 
>   METHOD if_apj_jt_check_20~initialize.
> 
> " This method is called in the job scheduling dialog, right before the parameter section is displayed.
> " The table CT_VALUE contains all parameter values of the template that are about to be displayed.
> " In this method, changes can be made to the table CT_VALUE, which means that values can dynamically be changed, added, or deleted.
> " 'Read-only' parameters and their values can be added to CT_VALUE here.
> " This method is not called if the job is scheduled via an API.
> 
>     READ TABLE ct_value WITH KEY param COMPONENTS parameter_name = 'TEXT' ASSIGNING  FIELD-SYMBOL(<fs_value>).
>     IF sy-subrc = 0.
>       <fs_value>-low = 'New Text'.
>     ELSE.
>       APPEND VALUE #( parameter_name = 'TEXT' sign = 'I' option = 'EQ' low = 'Very new text' )  TO ct_value.
>     ENDIF.
> 
>     READ TABLE ct_value WITH KEY param COMPONENTS parameter_name = 'READ_O' ASSIGNING  <fs_value>.
>     IF sy-subrc = 0.
>       <fs_value>-low = 'Initialize'.
>     ELSE.
>       APPEND VALUE #( parameter_name = 'READ_O' sign = 'I' option = 'EQ' low = 'Initialize' )  TO ct_value.
>     ENDIF.
> 
>   ENDMETHOD.
> 
> ******
> 
>   METHOD if_apj_jt_check_20~check_start_condition.
> 
> " This method is called after you select 'Schedule' and after the method
> " CHECK_AUTHORIZATIONS. Parameter values can't be manipulated here anymore.
> " The purpose of this method is to check the start condition of the job that is about to be
> " scheduled. The start condition is received in the parameter IS_SCHEDULE_INFO.
> " Depending on certain values, it may be forbidden to schedule a job as periodic job or with a
> " very short period.
> 
>     CLEAR et_msg.
> 
>     "is_schedule_info-type
>     "O - once
>     "P - periodic
> 
>     IF is_schedule_info-type EQ 'P'.
> 
>       IF is_schedule_info-periodic_granularity = cl_apj_rt_api=>period_minutes OR
>          is_schedule_info-periodic_granularity = cl_apj_rt_api=>period_hours.
>         ev_incorrect = abap_true.
>         APPEND VALUE #( type = 'E' id = 'ZAPJ' number = '001' message_v1 = 'period is too short' ) TO et_msg ##NO_TEXT.
>       ENDIF.
> 
>     ENDIF.
> 
>   ENDMETHOD.
> 
> ******
> 
>   METHOD if_apj_jt_check_20~check_and_adjust_parameter.
> 
> " This method is called in the job scheduling dialog, after you've changed the value of a parameter
> " which is marked with the flag 'Backend Call'.
> " The parameter table CT_VALUE contains all parameter values. IV_PARAMETER_NAME contains the name of the
> " parameter for which this method has been called.
> " In this example, the value ABCDE is rejected in the field TEXT.
> " If the value is set to XYZ, the value is changed to X.
> " Moreover, messages of T100 format can be added to the message table et_msg. They will then
> " be displayed on the UI.
> " This method is not called if the job is scheduled via an API.
> 
>     CLEAR et_msg.
>     ev_successful = abap_true.
> 
>     CHECK iv_parameter_name = 'TEXT'.
>     READ TABLE ct_value ASSIGNING FIELD-SYMBOL(<fs_value>)
>          WITH KEY param COMPONENTS parameter_name = 'TEXT'.
>     IF <fs_value> IS ASSIGNED.
>       IF <fs_value>-low = 'ABCDE'.
>         APPEND VALUE #( type = 'E' id = 'ZAPJ' number = '001' message_v1 = 'Value not allowed' ) TO et_msg ##NO_TEXT.
>         RETURN.
>       ENDIF.
> 
>       IF <fs_value>-low = 'XYZ'.
>         <fs_value>-low = 'X'.
>       ENDIF.
> 
>     ENDIF.
> 
>   ENDMETHOD.
> 
> ******
> 
>   METHOD if_apj_jt_check_20~check_and_adjust.
> 
> " This method is called when the application jobs framework receives the job scheduling request.
> " In this method, parameters can be checked and changed.
> " The parameter table CT_VALUE contains all parameter values.
> " Attention: Changing parameters with the attribute 'read-only' or 'hidden' in this method has no effect.
> " They must be changed using the methods ADJUST_READ_ONLY or ADJUST_HIDDEN respectively.
> " This method is not called if the job is scheduled via the external API 'Service BC_EXT_APPJOB_MANAGEMENT'.
> 
>     CLEAR et_msg.
>     ev_successful = abap_true.
> 
>     READ TABLE ct_value ASSIGNING FIELD-SYMBOL(<fs_value>)
>          WITH KEY param COMPONENTS parameter_name = 'TEXT'.
>     IF <fs_value> IS ASSIGNED.
>       IF <fs_value>-low = 'X'.
>         <fs_value>-low = 'Bingo'.
>       ENDIF.
>     ENDIF.
> 
>   ENDMETHOD.
> 
> ******
> 
>   METHOD if_apj_jt_check_20~check_authorizations.
> 
> " This method is called when the application jobs framework receives the job scheduling request and after the method
> " CHECK_AND_ADJUST. Parameter values can't be manipulated here anymore; they can only be
> " evaluated. This method receives the parameter values in the import table parameter IT_VALUE.
> " Moreover, the job user (according to note 3295193 linked above) and the job catalog entry name are passed to this method.
> 
>     CLEAR et_msg.
>     ev_successful = abap_true.
> 
> " If necessary, implement appropriate checks based on the available information and set
> "   ev_successful = abap_false
> " and write error messages to et_msg, if necessary.
> " In this case, the job will not be scheduled.
> 
>   ENDMETHOD.
> 
> ******
> 
>   METHOD if_apj_jt_check_20~get_dynamic_properties.
> 
> " This method is called in the job scheduling dialog, right before the parameter section is displayed AND
> " after the INITIALIZE method.
> " Moreover, this method is called after the value of a field with the attribute 'Backend Call Required' has been changed.
> " The parameter table IT_VALUE contains all parameter values, including the initial ones.
> " The parameter IV_JOB_CATALOG_ENTRY_NAME contains the name of the job catalog entry.
> " This method is not called if the job is scheduled via an API.
> " In this example, the method has the following effect:
> " If you enter HIDE into the field TEXT, then the field READ_O disappears from the selection screen.
> " Entering the value SHOW has the opposite effect.
> " This method is not called if the job is scheduled via an API.
> 
>     READ TABLE it_value WITH KEY param COMPONENTS parameter_name = 'TEXT' ASSIGNING  FIELD-SYMBOL(<fs_value>).
>     IF sy-subrc = 0.
>       IF <fs_value>-low = 'HIDE'.
> 
>         APPEND VALUE #( job_parameter_name = 'READ_O' hidden_ind = abap_true ) TO rts_dynamic_property.
> 
>       ENDIF.
> 
>       IF <fs_value>-low = 'SHOW'.
> 
>         APPEND VALUE #( job_parameter_name = 'READ_O' hidden_ind = abap_false ) TO rts_dynamic_property.
> 
>       ENDIF.
> 
> 
>     ENDIF.
> 
> 
>   ENDMETHOD.
> 
> ******
> 
>   METHOD if_apj_jt_check_20~adjust_read_only.
> 
> " This method is called when the application jobs framework receives the job scheduling request,
> " regardless of whether the job is scheduled from the app or via an API.
> " Only with this method the values of read-only parameters can be manipulated in this phase.
> 
>     READ TABLE ct_value WITH KEY param COMPONENTS parameter_name = 'READ_O' ASSIGNING  FIELD-SYMBOL(<fs_value>).
>     IF sy-subrc = 0.
>       <fs_value>-low = 'ReadAdjust'.
>     ELSE.
>       APPEND VALUE #( parameter_name = 'READ_O' sign = 'I' option = 'EQ' low = 'ReadAdjust' )  TO ct_value.
>     ENDIF.
> 
>   ENDMETHOD.
> 
> ******
> 
>   METHOD if_apj_jt_check_20~adjust_hidden.
> 
> " Attention: 'hidden' parameters are now obsolete.
> " This parameter value is not visible in the scheduling dialog.
> " It's not possible anymore to specify values for hidden parameters. For compatibility reasons, the method
> " adjust_hidden is still supported.
> "
> " This method is called when the application jobs framework receives the job scheduling request,
> " regardless of whether the job is scheduled from the app or via an API.
> " Only with this method the values of hidden parameters can be manipulated.
> 
>     READ TABLE ct_value WITH KEY param COMPONENTS parameter_name = 'HIDDEN' ASSIGNING  FIELD-SYMBOL(<fs_value>).
>     IF sy-subrc = 0.
>       <fs_value>-low = 'HiddenAdj'.
>     ELSE.
>       APPEND VALUE #( parameter_name = 'HIDDEN' sign = 'I' option = 'EQ' low = 'HiddenAdj' )  TO ct_value.
>     ENDIF.
> 
>   ENDMETHOD.
> 
> ENDCLASS.
> ```

