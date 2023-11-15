<!-- loio2473b538ce3149db89adbe86ebea12f3 -->

# Read Application Job Status Texts

Get a list of all possible application job statuses and their corresponding status texts using the HTTP method `GET`.



<a name="loio2473b538ce3149db89adbe86ebea12f3__section_hp1_43c_3zb"/>

## Request

Use the URL `<host>/sap/opu/odata/SAP/BC_EXT_APPJOB_MANAGEMENT;v=0002/JobStatusInfoSet` without parameters.



<a name="loio2473b538ce3149db89adbe86ebea12f3__section_cvd_p3c_3zb"/>

## Response

The operation returns a list of all application job statuses and their texts.



<a name="loio2473b538ce3149db89adbe86ebea12f3__section_gxk_q3c_3zb"/>

## Examples



### Request

```
GET <host>/sap/opu/odata/SAP/BC_EXT_APPJOB_MANAGEMENT;v=0002/JobStatusInfoSet
```

optional with language settings:

```
GET <host>/sap/opu/odata/SAP/BC_EXT_APPJOB_MANAGEMENT;v=0002/JobStatusInfoSet?sap-language=EN
```



### Response

```
<d:JobStatus>C</d:JobStatus>
<d:JobStatusText>Canceled</d:JobStatusText>
```

or

```
<d:JobStatus>S</d:JobStatus>
<d:JobStatusText>Scheduled</d:JobStatusText>
```

and so on.

