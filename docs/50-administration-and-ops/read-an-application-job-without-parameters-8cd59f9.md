<!-- loio8cd59f9597284db78714f900cc233796 -->

# Read an Application Job Without Parameters

Read an application job including step and log data, without parameters, using the HTTP method `GET`. An application job consists of a job header, a job step, a log header, and a log message. Via `$expand` all these job data can be read with one request.



<a name="loio8cd59f9597284db78714f900cc233796__section_eg4_sgb_d1c"/>

## Request

You can retrieve all entities of an application job with one call: GET `<host>/sap/opu/odata/SAP/BC_EXT_APPJOB_MANAGEMENT;v=0002/JobHeaderSet(JobName='JobName',JobRunCount='JobCount')?$expand=JobStepSet/JobStepLogInfoSet/JobLogMessageSet`

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

JobName

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

JobRunCount

</td>
<td valign="top">

Mandatory

</td>
<td valign="top">

This is the ID of the application job.

</td>
</tr>
</table>



<a name="loio8cd59f9597284db78714f900cc233796__section_fhz_bhb_d1c"/>

## Example

GET `<host>/sap/opu/odata/SAP/BC_EXT_APPJOB_MANAGEMENT;v=0002/JobHeaderSet(JobName='JobName',JobRunCount='JobCount')?$expand=JobStepSet/JobStepLogInfoSet/JobLogMessageSet`

For more information, see [3383044](https://me.sap.com/notes/3383044).

