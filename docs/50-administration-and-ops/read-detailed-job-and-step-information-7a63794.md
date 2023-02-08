<!-- loio7a6379466c294e7fb65b90ac68f1643a -->

# Read Detailed Job and Step Information

Read detailed job and step information using the HTTP method `GET`.

This operation returns one line for each job step, where each line contains some global information of the job \(like status, start time, end time\) and step specific information like step status and step start time.



<a name="loio7a6379466c294e7fb65b90ac68f1643a__section_jzq_tvt_zhb"/>

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

JobRunCount



</td>
<td valign="top">

Mandatory



</td>
<td valign="top">

This is the ID of an application job.



</td>
</tr>
<tr>
<td valign="top">

JobName



</td>
<td valign="top">

Mandatory



</td>
<td valign="top">

This is the name of an application job.



</td>
</tr>
</table>



<a name="loio7a6379466c294e7fb65b90ac68f1643a__section_mwv_vwt_zhb"/>

## Examples



### Request

```
GET <host><host>/sap/opu/odata/SAP/BC_EXT_APPJOB_MANAGEMENT;v=0002/JobinfoGet?JobName='JobName'&JobRunCount='JobCount'
```



### Response

```
{
  "d": {
    "results": [
      {
        "JobName": "string",
        "JobRunCount": "string",
        "JobStatus": "string",
        "JobSdlDateTime": "DateTime",
        "JobStartDateTime": "DateTime",
        "JobEndDateTime": "DateTime",
        "JobAppRC": "Integer",
        "StepCount": "DateTime",
        "StepStatus": "String",
        "StepStartDateTime": "DateTime",
        "StepAppRC": "Integer",
      }
    ]
  }
}
```

