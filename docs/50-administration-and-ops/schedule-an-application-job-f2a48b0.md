<!-- loiof2a48b0f4e774562a2ec6a3964a9c7e5 -->

# Schedule an Application Job

With `JobSchedule`, you can schedule an application job based on a job template using the HTTP method `POST`. No start condition can be specified, it's always an immediate start.



<a name="loiof2a48b0f4e774562a2ec6a3964a9c7e5__section_jzq_tvt_zhb"/>

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

TestModeInd

</td>
<td valign="top">

Optional

</td>
<td valign="top">

Reserved should be set to false.

</td>
</tr>
<tr>
<td valign="top">

JobParameterValues

</td>
<td valign="top">

Optional

</td>
<td valign="top">

These are the parameter values of the application job.

</td>
</tr>
<tr>
<td valign="top">

JobParameterValuesSimple

</td>
<td valign="top">

Optional

</td>
<td valign="top">

This is the parameter string containing the step number. You can schedule application jobs with a simplified format, containing the step number, the application job name, and the `T_VALUE`.

</td>
</tr>
<tr>
<td valign="top">

JobTemplateName

</td>
<td valign="top">

Mandatory

</td>
<td valign="top">

This is the technical ID of the application job template from which the new application job will be generated.

</td>
</tr>
<tr>
<td valign="top">

JobText

</td>
<td valign="top">

Mandatory

</td>
<td valign="top">

This is the human-readable name for the application job.

</td>
</tr>
<tr>
<td valign="top">

JobUser

</td>
<td valign="top">

Mandatory

</td>
<td valign="top">

This is the user ID of the user performing the job.

</td>
</tr>
<tr>
<td valign="top">

JobUserName

</td>
<td valign="top">

Obsolete

</td>
<td valign="top">

This is the user name of the user performing the job.

</td>
</tr>
<tr>
<td valign="top">

JobUserID

</td>
<td valign="top">

Obsolete

</td>
<td valign="top">

This is the ID of the application job user.

</td>
</tr>
<tr>
<td valign="top">

sap-language

</td>
<td valign="top">

Optional

</td>
<td valign="top">

This is the SAP language code. You can set the language that you want the job to run with by stating, for example, `sap-language=JA` \(with `JA` meaning "Japanese"\). If you don’t set a language explicitely, the job will run with the language of the communication user.

</td>
</tr>
</table>



<a name="loiof2a48b0f4e774562a2ec6a3964a9c7e5__section_ztj_5wt_zhb"/>

## Response

The operation schedules an application job.



<a name="loiof2a48b0f4e774562a2ec6a3964a9c7e5__section_mwv_vwt_zhb"/>

## Examples



### Request

```
POST <host>/sap/opu/odata/SAP/BC_EXT_APPJOB_MANAGEMENT;v=0002/JobSchedule?JobTemplateName='TemplateName'&JobText='Test'&JobUser='BusinessUser'&TestModeInd=false&JobParameterValues=''
```



### Response

```
{
  "d": {
    "results": [
      {

        "JobName": "string"
        "JobRunCount": "string"
        "JobStatus": "char"
        "ReturnCode": "integer" (0 = ok, <> 0 = error)
      }
    ]
  }
}

```



### Example of `JobParameterValuesSimple`

> ### Sample Code:  
> ```
> '{"VALUES":[{"STEP_NR":StepNum","NAME":"ParameterName","T_VALUE":[{"SIGN":"I","OPTION":"EQ","LOW":"Value or X depending on parameter Type","HIGH":""}]}]}'
> ```

