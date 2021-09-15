<!-- loioe9ea22491efb46b5ac36fbd75b02478f -->

# Dynpro Screen Elements that Can Be Logged

A list of screen elements in Dynpro applications that can have read access logged.

The main scope of Read Access Logging is to log output fields on result screens. Optionally, also the input fields of the corresponding selection or query screens can be logged. Logging and defining a log context are supported for such selection or query screens and their result screens if both are implemented and processed in the same program. Please note that one business transaction may be processed using more than one program. In such cases, logging of the input is not possible.

The table below shows the basic screen elements that can be logged in Dynpro applications.


<table>
<tr>
<th>

Basic Screen Element



</th>
<th>

Comment



</th>
</tr>
<tr>
<td>

Input fields



</td>
<td>

Value of input field



</td>
</tr>
<tr>
<td>

Output fields



</td>
<td>

Value of output field



</td>
</tr>
<tr>
<td>

Radio buttons



</td>
<td>

For each radio button, a value is logged \(true/false\). Note that each radio button is logged separately. There is no logging of entire groups of radio buttons.



</td>
</tr>
<tr>
<td>

Checkboxes



</td>
<td>

Value of checkbox



</td>
</tr>
<tr>
<td>

Dropdown lists



</td>
<td>

Technical key value with marker for selected key. Note that the texts from the user interface are not logged.



</td>
</tr>
<tr>
<td>

Table controls



</td>
<td>

Columns of table control



</td>
</tr>
<tr>
<td>

Parameters



</td>
<td>

Value of the parameters of a selection screen



</td>
</tr>
<tr>
<td>

Subscreens



</td>
<td>

As subscreens consist of the same elements as screens, logging takes place for the elements of subscreens in the same way as for screens



</td>
</tr>
<tr>
<td>

Select-Options



</td>
<td>

Value of each select-option of a selection screen \(list of sign, option, low/high values\).

A select-option `SELOPT` is displayed as:

-   a `LOW` or `HIGH` field for a single selection
-   a push-button \(arrow icon\) for a multiple selection that is represented as a table of fields \(`SIGN`, `OPTION`, `LOW`, `HIGH`\)

To be able to log `SELOPT-LOW` or `SELOPT-HIGH` fields, they have to be configured.

You can enter the data to `SELOPT-LOW` or `SELOPT-HIGH` manually:

-   If a program was executed without a screen round trip, the fields `SELOPT-LOW` and `SELOPT-HIGH` can be logged as input fields.
-   The multiple selection is attached to the `SELOPT-LOW` field: if the field `SELOPT-LOW` is configured for logging, the multiple selection is configured for logging as well. If a screen round trip was done \(e.g. pressing [Enter\]\), or if the multiple selection was used, the `SELOPT` data is added to the multiple selection table, therefore the `SELOPT-LOW` field can be logged as an input or output field.

If a variant that is used to provide the input data for a selection-option shall be logged, it has to be configured for output logging. Input data provided for the multiple selection can be logged, even if it was not displayed.

Input data provided via variant for other parameter fields on a selection screen can be logged using the input logging.

> ### Note:  
> To be sure that all the data related to the select-option field is logged, it should be configured for both input and output logging.



</td>
</tr>
<tr>
<td>

Value help \(F4\)



</td>
<td>

Entries from the value help \(F4 help\) can be recorded by choosing the read access logging function from the context menu.



</td>
</tr>
</table>

The table below shows the screen attributes that can be logged:


<table>
<tr>
<th>

Screen Attribute



</th>
<th>

Comment



</th>
</tr>
<tr>
<td>

Screen title



</td>
<td>

The title of a screen



</td>
</tr>
<tr>
<td>

Transaction code



</td>
<td>

The value of a transaction code at runtime



</td>
</tr>
<tr>
<td>

OK code



</td>
<td>

Code that is set when triggering an action \(for example, clicking a button\)



</td>
</tr>
<tr>
<td>

Message



</td>
<td>

The status message displayed on a screen



</td>
</tr>
</table>

The table below shows the controls that can be logged:


<table>
<tr>
<th>

Control



</th>
<th>

Comment



</th>
</tr>
<tr>
<td>

ALV grid



</td>
<td>

Columns of a display-only ALV grid control



</td>
</tr>
<tr>
<td>

Tab strip



</td>
<td>

Same logging behavior as for subscreens. If switching tabs happens on front-end, logging is done together for all tabs. If, on the other hand, switching tabs happens on application level, the tabs are logged separately. In addition, an OK code can only be logged when switching tabs happens on application level.



</td>
</tr>
</table>

The table below shows the additional screen elements that can be logged:


<table>
<tr>
<th>

Screen Element



</th>
<th>

Comment



</th>
</tr>
<tr>
<td>

ABAP Lists



</td>
<td>

ABAP lists can be recorded by choosing the read access logging function from the context menu. The pseudo field `$_LIST_CODE` will be added to the created recording. Using this pseudo field, all lists of a program can be configured for logging. It is not possible to log input fields and OK codes of a list.



</td>
</tr>
</table>

It is not possible to log other screen objects, such as the following:

-   Input-enabled ALV grid
-   ALV tree
-   File download

For more information about the availability of features of Read Access Logging, see SAP Note [1969086](https://launchpad.support.sap.com/#/notes/1969086).

**Related Information**  


[Channel-Specific Information](Channel-Specific_Information_24c7399.md "The Read Access Logging framework handles the channels generically, but each channel configuration is specific.")

[How to Manage Recordings of Application User Interfaces](How_to_Manage_Recordings_of_Application_User_Interfaces_ae187d4.md "To use Read Access Logging with user interface technologies like Web Dynpro and Dynpro, you first identify the log-relevant fields. Read Access Logging provides a user interface recorder to identify those fields.")

