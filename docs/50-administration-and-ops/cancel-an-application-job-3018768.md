<!-- loio3018768a6e9c43afad4e5f3ad1720e5d -->

# Cancel an Application Job

Cancel an application job in general using the HTTP method `POST`.

This operation is more general than JobAbort. JobCancel treats a job depending on its status:

• If a job is already running, JobCancel will cancel the job like JobAbort.

• If a job has not yet started, JobCancel will delete it.



<a name="loio3018768a6e9c43afad4e5f3ad1720e5d__section_jzq_tvt_zhb"/>

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



<a name="loio3018768a6e9c43afad4e5f3ad1720e5d__section_mwv_vwt_zhb"/>

## Examples



### Request

```
POST <host>/sap/opu/odata/SAP/BC_EXT_APPJOB_MANAGEMENT;v=0002/JobCancel?JobName='JobName'&JobRunCount='JobCount'
```



### Response

```
{
  "d": {
    "results": [
      {
        "ReturnCode": "integer" (0 = ok, <> 0 = error)
      }
    ]
  }
}

```

