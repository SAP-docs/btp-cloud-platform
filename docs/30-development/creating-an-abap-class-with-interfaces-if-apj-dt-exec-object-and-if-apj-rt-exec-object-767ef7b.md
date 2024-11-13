<!-- loio767ef7b6d55c47d5b5bcbae4b67aad33 -->

# Creating an ABAP Class with Interfaces IF\_APJ\_DT\_EXEC\_OBJECT and IF\_APJ\_RT\_EXEC\_OBJECT

Find out how to run business logic in an application job using an ABAP class that implements interfaces `IF_APJ_DT_EXEC_OBJECT` and `IF_APJ_RT_EXEC_OBJECT`.

> ### Note:  
> Note that this is a legacy interface. Don't use it for new developments. If you use this interface, you only have limited options during the editing of the job catalog entry.

If you want to run the business coding of your application in an application job, you can create an ABAP class which implements the interfaces`IF_APJ_DT_EXEC_OBJECT` and `IF_APJ_RT_EXEC_OBJECT` and put the coding into this class. It's not recommended to use this possibility for new developments, because it offers limited functionality only.

The interface `IF_APJ_DT_EXEC_OBJECT` contains the following method:

-   `GET_PARAMETERS`: This method is called by the application job framework to get all selection parameters. The method returns two internal tables:

    -   `ET_PARAMETER_DEF`: Determines the parameter list which is used by the job catalog entry that refers to this main class. It also defines how the parameters are displayed and how they behave on the selection screen

    -   `ET_PARAMETER_VAL`: Determines the default values for these parameters in a newly created job template that refers to the job catalog entry mentioned above



The structure of table `ET_PARAMETER_DEF` has the following fields:


<table>
<tr>
<th valign="top">

Field Name

</th>
<th valign="top">

Definition

</th>
</tr>
<tr>
<td valign="top">

`SELNAME`

</td>
<td valign="top">

Name of the parameter. The length of the name is restricted to 8 characters. It defines the parameter name which is used in the job catalog entry and in the job template

</td>
</tr>
<tr>
<td valign="top">

`KIND`

</td>
<td valign="top">

Defines whether a single value or a value range can be entered on the selection screen for this parameter. Possible values are:

-   `IF_APJ_DT_EXEC_OBJECT=>PARAMETER` for a single value parameter

-   `IF_APJ_DT_EXEC_OBJECT=>SELECT_OPTION` for a value range parameter




</td>
</tr>
<tr>
<td valign="top">

`DATATYPE`

</td>
<td valign="top">

The data type of the parameter. It must be an elementary data type, like `C` or `CHAR`

</td>
</tr>
<tr>
<td valign="top">

`LENGTH`

</td>
<td valign="top">

The output length of the parameter if the data type has no fixed length

</td>
</tr>
<tr>
<td valign="top">

`DECIMALS`

</td>
<td valign="top">

Number of decimals if the data type belongs to a number with decimals

</td>
</tr>
<tr>
<td valign="top">

`COMPONENT_TYPE`

</td>
<td valign="top">

Not supported

</td>
</tr>
<tr>
<td valign="top">

`SECTION_TEXT`

</td>
<td valign="top">

Not used

</td>
</tr>
<tr>
<td valign="top">

`GROUP_TEXT`

</td>
<td valign="top">

Not used

</td>
</tr>
<tr>
<td valign="top">

`PARAM_TEXT`

</td>
<td valign="top">

The title of the parameter which is displayed on the selection screen

</td>
</tr>
<tr>
<td valign="top">

`LOWERCASE_IND`

</td>
<td valign="top">

Defines whether lower case characters are allowed for the parameter

</td>
</tr>
<tr>
<td valign="top">

`HIDDEN_IND`

</td>
<td valign="top">

Defines whether the parameter is hidden on the selection screen

</td>
</tr>
<tr>
<td valign="top">

`CHANGEABLE_IND`

</td>
<td valign="top">

If set to `ABAP_FALSE`, the read-only flag is set for this parameter if the parameter is added to a catalog entry

</td>
</tr>
<tr>
<td valign="top">

`MANDATORY_IND`

</td>
<td valign="top">

Defines whether the parameter is mandatory on the selection screen

</td>
</tr>
<tr>
<td valign="top">

`CHECKBOX_IND`

</td>
<td valign="top">

If set, the parameter is displayed as checkbox on the selection screen

</td>
</tr>
<tr>
<td valign="top">

`LIST_IND`

</td>
<td valign="top">

If set, the parameter is displayed as list box on the selection screen

</td>
</tr>
<tr>
<td valign="top">

`RADIO_GROUP_IND`

</td>
<td valign="top">

If set, the parameter is displayed as radio button on the selection screen

</td>
</tr>
<tr>
<td valign="top">

`RADIO_GROUP_ID`

</td>
<td valign="top">

Name of the radio button group if the parameter is a radio button

</td>
</tr>
</table>

The structure of the table `ET_PARAMETER_VAL` has the following fields:


<table>
<tr>
<th valign="top">

Field Name

</th>
<th valign="top">

Definition

</th>
</tr>
<tr>
<td valign="top">

`SELNAME`

</td>
<td valign="top">

Name of the parameter. It's the same name that was used in table `ET_PARAMETER_DEF`

</td>
</tr>
<tr>
<td valign="top">

`KIND`

</td>
<td valign="top">

Defines whether a single value or a value range can be entered on the selection screen for this parameter. It should be the same value that was used in table `ET_PARAMETER_DEF`

</td>
</tr>
<tr>
<td valign="top">

`SIGN`, `OPTION`, `LOW`, `HIGH`

</td>
<td valign="top">

Entry of a ranges table which contains the parameter value, or a parameter value range

</td>
</tr>
</table>

The interface `IF_APJ_RT_EXEC_OBJECT` contains the following method:

-   `EXECUTE`: This method is called by the application job framework when the scheduled job is run. It receives the internal table `IT_PARAMETERS` as parameter. This internal table contains all parameter values that you entered on the selection screen when you scheduled the job.


The structure of table `IT_PARAMETERS` has the following fields:


<table>
<tr>
<th valign="top">

Field Name

</th>
<th valign="top">

Definition

</th>
</tr>
<tr>
<td valign="top">

`SELNAME`

</td>
<td valign="top">

Name of the parameter. It's the same name that was used in method `GET_PARAMETERS`

</td>
</tr>
<tr>
<td valign="top">

`KIND`

</td>
<td valign="top">

If you've defined the parameter as a single value parameter in method `GET_PARAMETERS`, it's set to `IF_APJ_DT_EXEC_OBJECT=>PARAMETER`. Otherwise, it's set to `IF_APJ_DT_EXEC_OBJECT=>SELECT_OPTION` 

</td>
</tr>
<tr>
<td valign="top">

`SIGN`, `OPTION`, `LOW`, `HIGH`

</td>
<td valign="top">

Entry of a ranges table which contains the parameter value, or a parameter value range

</td>
</tr>
</table>

> ### Note:  
> If you've selected several value ranges for a parameter on the selection screen, the table `IT_PARAMETERS` contains one entry for each value range.

