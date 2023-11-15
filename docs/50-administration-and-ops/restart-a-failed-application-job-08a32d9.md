<!-- loio08a32d93c29f43b09a365a530c47b5bd -->

# Restart a Failed Application Job

Create a copy of the failed application job and start it from or after the failed step using HTTP method `POST`.



<a name="loio08a32d93c29f43b09a365a530c47b5bd__section_irg_w3c_3zb"/>

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

This is the ID of an application job

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

This is the name of an application job

</td>
</tr>
<tr>
<td valign="top">

JobRestartMode

</td>
<td valign="top">

Mandatory

</td>
<td valign="top">

This is the type of restart you can trigger

</td>
</tr>
</table>

There are two restart modes:

-   JobRestartMode='E': Restart the job from the failed step. The job steps before the failed step will be skipped.

-   JobRestartMode='A': Restart the job after the failed step. The failed step and the steps before will be skipped.




<a name="loio08a32d93c29f43b09a365a530c47b5bd__section_ids_jjc_3zb"/>

## Response

The operation restarts a failed application job.



<a name="loio08a32d93c29f43b09a365a530c47b5bd__section_bgl_kjc_3zb"/>

## Examples



### Request

```
POST <host>/sap/opu/odata/sap/BC_EXT_APPJOB_MANAGEMENT;v=0002/JobRestart?JobName='JobName'&JobRunCount='JobCount'&JobRestartMode='E'
```



### Response

```
<d:JobName>JobName</d:JobName>
<d:JobRunCount>JobCount</d:JobRunCount>
<d:JobStatus>R</d:JobStatus>
<d:ReturnCode>0</d:ReturnCode>
```

