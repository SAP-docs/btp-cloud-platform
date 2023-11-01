<!-- loioc0182485178a4b9095e3bf73a4618b20 -->

# Abort a Running Application Job

Abort a running application job using the HTTP metthod POST.



<a name="loioc0182485178a4b9095e3bf73a4618b20__section_jzq_tvt_zhb"/>

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



<a name="loioc0182485178a4b9095e3bf73a4618b20__section_mwv_vwt_zhb"/>

## Examples



### Request

```
POST <host>/sap/opu/odata/SAP/BC_EXT_APPJOB_MANAGEMENT;v=0002/JobAbort?JobName='JobName'&JobRunCount='JobCount'
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

