<!-- loio117063a0acdb4f6aa34b38f35a8fbc73 -->

# Retrieve Application Job Parameters

Retrieve the application job parameters as a JSON string. This string can directly be used for scheduling an application job.



<a name="loio117063a0acdb4f6aa34b38f35a8fbc73__section_rvp_d5b_fdc"/>

## Request \(As a String\)

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

This is the name of the application job

</td>
</tr>
<tr>
<td valign="top">

JobCount

</td>
<td valign="top">

Mandatory

</td>
<td valign="top">

This is an alphanumerical job count value

</td>
</tr>
</table>



<a name="loio117063a0acdb4f6aa34b38f35a8fbc73__section_eny_n5b_fdc"/>

## Response

The operation returns:

-   Parameter String: A JSON string containing the application job parameters.




<a name="loio117063a0acdb4f6aa34b38f35a8fbc73__section_n1n_dvb_fdc"/>

## Examples



### Request

```
POST <host>/sap/opu/odata/SAP/BC_EXT_APPJOB_MANAGEMENT;v=0002/JobParamValuesGet?JobName='JobName'&JobCount='JobCount'
```



### Response

```
<d:ParameterValues>{JSONSTRING}</d:ParameterValues>
```



<a name="loio117063a0acdb4f6aa34b38f35a8fbc73__section_bfz_yvb_fdc"/>

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

JobName

</td>
<td valign="top">

Mandatory

</td>
<td valign="top">

This is the name of the application job

</td>
</tr>
<tr>
<td valign="top">

JobCount

</td>
<td valign="top">

Mandatory

</td>
<td valign="top">

This is an alphanumerical job count value

</td>
</tr>
</table>



<a name="loio117063a0acdb4f6aa34b38f35a8fbc73__section_gkt_gwb_fdc"/>

## Response

The operation returns:

-   Step Number: The number of the step where the parameter exists

-   Parameter Name: The name of the parameter

-   Sign/Option/Low/High: Values according to ABAP ranges




<a name="loio117063a0acdb4f6aa34b38f35a8fbc73__section_ibs_mwb_fdc"/>

## Examples



### Request

```
POST <host>/sap/opu/odata/SAP/BC_EXT_APPJOB_MANAGEMENT;v=0002/JobParamValuesStructGet?JobName='JobName'&JobCount='JobCount'
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

