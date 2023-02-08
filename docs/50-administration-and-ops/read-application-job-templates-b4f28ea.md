<!-- loiob4f28eada84b44eaa85346365aee41aa -->

# Read Application Job Templates

Get a list of all application job templates using the HTTP methode `GET`.



<a name="loiob4f28eada84b44eaa85346365aee41aa__section_jzq_tvt_zhb"/>

## Request

Use the URL <host\>/sap/opu/odata/SAP/BC\_EXT\_APPJOB\_MANAGEMENT;v=0002/JobTemplateSet without parameters.



<a name="loiob4f28eada84b44eaa85346365aee41aa__section_ztj_5wt_zhb"/>

## Response

The operation returns a list of all application job templates.



<a name="loiob4f28eada84b44eaa85346365aee41aa__section_mwv_vwt_zhb"/>

## Examples



### Request

```
GET <host>/sap/opu/odata/SAP/BC_EXT_APPJOB_MANAGEMENT;v=0002/JobTemplateSet

```



### Response

```
{
  "d": {
    "results": [
      {
        "JobTemplateName": "string",
        "JobTemplateVersion": "string",
        "JobTemplateStepCount": "Unknown Type: integer,null",
        "JobPeriodicGranularity": "Unknown Type: string,null",
        "JobReportName": "Unknown Type: string,null",
        "JobUserName": "Unknown Type: string,null",
        "JobPeriodicValue": "Unknown Type: string,null",
        "JobTemplateText": "Unknown Type: string,null",
        "CreationDateTime": "/Date(1492098664000)/",
        "CreationUserName": "Unknown Type: string,null",
        "LastChangeDateTime": "/Date(1492098664000)/",
        "LastChangeUserName": "Unknown Type: string,null",
        "SupportsTestModeInd": "Unknown Type: boolean,null"
      }
    ]
  }
}
```

