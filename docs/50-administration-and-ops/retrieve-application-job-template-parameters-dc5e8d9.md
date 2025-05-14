<!-- loiodc5e8d92882848829393dd1c1425d676 -->

# Retrieve Application Job Template Parameters

Retrieve application job template parameters as a JSON string. This string can directly be used for scheduling an application job.



<a name="loiodc5e8d92882848829393dd1c1425d676__section_zxs_cv5_2fc"/>

## Request \(As a String\)

You can include the following properties in the URL of the request:

****


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

This is the name of the application job template.

</td>
</tr>
</table>



<a name="loiodc5e8d92882848829393dd1c1425d676__section_wm4_3v5_2fc"/>

## Response

The operation returns:

-   Parameter String: A JSON string containing the application job template parameters. The parameters not pre-defined in the application job template are also delivered in the response.



<a name="loiodc5e8d92882848829393dd1c1425d676__section_bsp_nv5_2fc"/>

## Examples



### Request

```
GET <host>/sap/opu/odata/SAP/BC_EXT_APPJOB_MANAGEMENT;v=0002/TemplateValuesGet?JobTemplateName='TemplateName'
```



### Response

```
<d:ParameterValues>{JSONSTRING}</d:ParameterValues>
```



<a name="loiodc5e8d92882848829393dd1c1425d676__section_sbh_qzq_ffc"/>

## Request \(Standard\)

Retrieve the application job parameters. You can include the following properties in the URL of the request:


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

This is the name of the application job template.

</td>
</tr>
</table>



<a name="loiodc5e8d92882848829393dd1c1425d676__section_ifm_ffr_ffc"/>

## Response

The operation returns:

-   Application job template parameter values



<a name="loiodc5e8d92882848829393dd1c1425d676__section_mq5_hfr_ffc"/>

## Examples



### Request

```
GET <host>/sap/opu/odata/SAP/BC_EXT_APPJOB_MANAGEMENT;v=0002/TemplateValuesStructGet?JobTemplateName='TemplateName'
```



### Response

```
{
  "d": {
    "results": [
      {
       "StepNr": StepNumber,
	"JobParameterName": "ParameterName",
	"Sign": "I",
	"Option": "EQ",
	"Low": "LowValue",
	"High": "HighValue"	}
    ]
  }
}

```

