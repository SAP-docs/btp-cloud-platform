<!-- loio91d64bf0813c41bc8a55cd90bd34a61f -->

# Tips for Configurations with Log Contexts



<a name="loio91d64bf0813c41bc8a55cd90bd34a61f__section_N1007E_N1007B_N10003"/>

## Definition

In a Read Access Logging configuration for Dynpro and Web Dynpro channels, you might need to use a log context to make sure that your log can be interpreted correctly. The log context is the UI element that other UI elements within the logging session depend on. When read access is being logged and the field that is defined as the log context changes on the user interface, all other fields are deleted from memory before the next log entry is created. Whether or not you need a log context depends on the user interface of your application. The graphic below shows a screen sequence taken from a simple HR application and the accompanying table gives recommendations on how to configure Read Access Logging for this screen sequence with the help of the log context.

> ### Note:  
> Log contexts are based on single applications or programs, like configurations. Log contexts cannot be applied across several configurations or applications/programs.
> 
> For Dynpro, single transactions can contain more than one program, which may not be apparent to you when you create a recording. In this case too, log contexts cannot be spread over multiple programs used in the transaction.



<a name="loio91d64bf0813c41bc8a55cd90bd34a61f__section_N1008B_N1007B_N10003"/>

## Example

The graphic below shows a sequence of three screens. On Screen 1, the user enters an employee number. Screen 2 displays the social security number and religion of the employee. Screen 3 displays the salary of the employee.

   
  
<a name="loio91d64bf0813c41bc8a55cd90bd34a61f__fig_N10097_N1008B_N1007B_N10003"/>Example screen sequence

 ![](images/RAL-Screen-Sequence_fddde8a.png "Example screen sequence") 

The table below shows how to configure the screen sequence depicted in the graphic above. Note that the field *Employee Number* is a different field on the three screens; on the first screen, it is an input field and on the second and third field, it is an output field like the other fields that cannot be edited.


<table>
<tr>
<th valign="top">

Screen Number



</th>
<th valign="top">

UI Element



</th>
<th valign="top">

Recommended Logging Type



</th>
<th valign="top">

Comment



</th>
</tr>
<tr>
<td valign="top">

Screen 1



</td>
<td valign="top">

Employee No



</td>
<td valign="top">

Log with value and define as log context



</td>
<td valign="top">

The employee number is an input field, we recommend that you log it. As the other fields on Screen 2 depend on the employee number, we recommend defining it as the log context.

In the log, the field that is the log context is marked for easy identification.



</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Screen 2



</td>
<td valign="top">

Employee No



</td>
<td valign="top">

No logging necessary



</td>
<td valign="top">

The employee number has been entered on Screen 1 and is repeated here as an output field. As you have already specified it as the log context, you do not need to log this field.

> ### Note:  
> Even if the employee number is not repeated on each screen, the log context is still logged as part of the log entry of these screens.



</td>
</tr>
<tr>
<td valign="top">

Social Security No



</td>
<td valign="top">

Log without value \(for example, legal regulations may prohibit logging social security numbers\)



</td>
<td valign="top">

The social security number of this employee is displayed within the same log entry as the log context. If you configure to log it without the value, only the fact that the field was accessed is logged, but not the value.



</td>
</tr>
<tr>
<td valign="top">

Religion



</td>
<td valign="top">

Log with value



</td>
<td valign="top">

The religion of this employee is displayed within the same log entry. If you configure to log it with value, the religion is displayed in the log.



</td>
</tr>
<tr>
<td valign="top" rowspan="2">

Screen 3



</td>
<td valign="top">

Employee No



</td>
<td valign="top">

No logging necessary



</td>
<td valign="top">

As you have specified the employee number from Screen 1 as the log context, you do not need to log this field.

> ### Note:  
> Even if the employee number is not repeated on each screen, the log context is still logged as part of the log entry of these screens.



</td>
</tr>
<tr>
<td valign="top">

Salary



</td>
<td valign="top">

Log with value



</td>
<td valign="top">

As it is the only field that is configured on this screen, the salary of this employee will be displayed with the log context from Screen 1 in one log entry.



</td>
</tr>
</table>

 **Result** 

When a user clicks through this screen sequence when it is configured as described above, two log entries are created, one for Screen 2 and one for Screen 3. On Screen 1, no output field exists that can be logged. On Screen 3, the employee number does not have to be logged as the employee number field from screen 2 is the log context and is thus automatically logged during a screen sequence even if it is not displayed on subsequent screens.

**Related Information**  


[Channel-Specific Information](channel-specific-information-24c7399.md "The Read Access Logging framework handles the channels generically, but each channel configuration is specific.")

[How to Define What to Log](how-to-define-what-to-log-0eb5542.md "To define what to log, use a read access logging configuration.")

