<!-- loio182356103df94ce89796163bad321436 -->

# Read Application Job Status

Read the status of an application job using the HTTP method `GET`.



<a name="loio182356103df94ce89796163bad321436__section_jzq_tvt_zhb"/>

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



<a name="loio182356103df94ce89796163bad321436__section_ztj_5wt_zhb"/>

## Response

The operation returns the status of an application job.



<a name="loio182356103df94ce89796163bad321436__section_zm4_s5q_gyb"/>

## Additional Information

Please note that to obtain the status of jobs that weren't scheduled using the external scheduler API, you should assign your communication user not only to SAP\_COM\_0064 but also to SAP\_COM\_0326. For more information on this issue, see [3358110](https://me.sap.com/notes/3358110).



<a name="loio182356103df94ce89796163bad321436__section_mwv_vwt_zhb"/>

## Examples



### Request

```
GET <host>/sap/opu/odata/SAP/BC_EXT_APPJOB_MANAGEMENT;v=0002/JobStatusGet?JobName='JobName'&JobRunCount='JobCount'
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

