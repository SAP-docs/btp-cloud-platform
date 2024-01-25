<!-- loiob331bde8d502472390647a271e162ee4 -->

# Check Parameters for Scheduling a Job

Check the parameter string that you intend to schedule a job with. This call makes the same checks as the *Check* button contained within the *Application Jobs* app.



<a name="loiob331bde8d502472390647a271e162ee4__section_rnc_1gb_d1c"/>

## Request

You can include the following properties in the URL of the request:


<table>
<tr>
<th valign="top">

Property

</th>
<th valign="top">

Necessity

</th>
<th valign="top">

Comment

</th>
</tr>
<tr>
<td valign="top">

JobTemplateName

</td>
<td valign="top">

Mandatory

</td>
<td valign="top">

This is the name of the application job.

</td>
</tr>
<tr>
<td valign="top">

JobParameterValues

</td>
<td valign="top">

Mandatory

</td>
<td valign="top">

These are the parameter values of the application job. For more information, see [3383044](https://me.sap.com/notes/3383044).

</td>
</tr>
</table>



<a name="loiob331bde8d502472390647a271e162ee4__section_tcm_fgb_d1c"/>

## Response

The operation returns:

-   Parameter String: An overview of the supplied parameter string. \(In some applications, the supplied parameters can be changed by the framework. In such cases, a string with the changed parameters is returned in the response\).

-   Successful Indicator: Returns `true` when the supplied parameters are allowed. Otherwise it will return `false`.

-   Changed Indicator: Returns `true` if the parameters have been adjusted. Otherwise it will return `false`.

-   Dynamic Properties: `<Reserved>`

-   Error Messages: Shows errors or warnings regarding the supplied parameter string.




<a name="loiob331bde8d502472390647a271e162ee4__section_nbb_3gb_d1c"/>

## Examples



### Request

```
GET <host>/sap/opu/odata/SAP/BC_EXT_APPJOB_MANAGEMENT;v=0002/JobScheduleCheck?JobTemplateName='TemplateName'&JobParameterValues='ParameterValueString'
```



### Response

```
{
					"d": {
					"results": [
					{
					"JobParameterValues": "ParameterValueString",
					"SuccessfulInd": "boolean",
					"ChangedInd": "boolean",
					"DynamicProperties": "",
					"ErrMessages": "ErrorMessagesString",
					}
					]
					}
					}
				
```

