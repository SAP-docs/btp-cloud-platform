<!-- loioc94c85ee026846f1843e3bc9abd111f1 -->

# SAP Usage Data Management Service - Service Plans

Describes the plans available for the SAP Usage Data Management service for SAP BTP.

> ### Note:  
> The SAP Usage Data Management service APIs can be found in the *Resource Consumption* tile in Swagger.


<table>
<tr>
<th valign="top">

Display Name



</th>
<th valign="top">

Technical Service Name



</th>
<th valign="top">

Service Plans



</th>
<th valign="top">

Scopes



</th>
</tr>
<tr>
<td valign="top" rowspan="2">

Usage Data Management Service \(UDM\)



</td>
<td valign="top" rowspan="2">

`uas`



</td>
<td valign="top">

**`reporting-ga-admin`:** Service plan for using the SAP Usage Data Management service APIs.

This microservice is used to generate reports based on resource and cost consumption of a global account.



</td>
<td valign="top">

`Reporting.GA_Admin`



</td>
</tr>
<tr>
<td valign="top">

**`reporting-directory`:** Service plan for using the SAP Usage Data Management service APIs.

This microservice is used to generate reports based on resource and cost consumption of a directory.

When you create a service instance of this plan, you have to pass the directory ID in the following format:

-   `{"directoryGuid": "f4c920c1-efb7-4bda-8d0e-81616ab9a574"}` - if you create the service instance using the SAP BTP cockpit

-   `-c "{\"directoryGuid\": \"f4c920c1-efb7-4bda-8d0e-81616ab9a574\"}"` - if you create the service instance using the cf CLI


> ### Restriction:  
> The directory must be located under `globalAccount` and contain the subaccount from which you are creating the service instance.



</td>
<td valign="top">

`$XSAPPNAME.reporting.Directory_Admin`



</td>
</tr>
</table>

