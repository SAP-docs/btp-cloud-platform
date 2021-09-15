<!-- loio75cde5383e8d42dabd039b7dceef9511 -->

# Providing Details for SAP HANA Service Database Problems

If your problem is related to a SAP HANA service database, the details you need to provide differ depending on the environment or infrastructure provider the database is provisioned in.




<table>
<tr>
<th>

Infrastructure Provider



</th>
<th>

Details You Need to Provide



</th>
<th>

How to Find the Details You Need



</th>
</tr>
<tr>
<td>

Azure regions



</td>
<td rowspan="2">

The URL of the space the database is provisioned in



</td>
<td rowspan="2">

1.  In the SAP BTP cockpit, navigate to the org and space the database is provisioned in.

2.  In the navigation area, go to *SAP HANA* \> *Database Systems*.

3.  Choose the affected *Database System*.

4.  Copy the URL from the overview of the affected database system.

    Example URL:

    `https://account.hana.ondemand.com/cockpit#/globalaccount/<id>/subaccount/<id>/org/<id>/dbsystems/<id>/overview`




</td>
</tr>
<tr>
<td>

AWS regions

\(databases provisioned before June 4, 2018\)



</td>
</tr>
<tr>
<td>

AWS regions

\(databases provisioned after June 4, 2018\)



</td>
<td rowspan="2">

The service instance ID



</td>
<td rowspan="2">

1.  In the SAP BTP cockpit, navigate to the space the SAP HANA service instance is provisioned in.
2.  In the navigation area, choose *Services* \> *Service Instances*.
3.  In the list of available services, find your SAP HANA service instance and choose   Open Dashboard  from the *Actions* column.
4.  Copy the service instance GUID under *Details* \> *ID*.

    Example GUID: ad539b83-39bd-4ff4-8b41-1a5dfdfca7ea




</td>
</tr>
<tr>
<td>

GCP regions



</td>
</tr>
<tr>
<td>

 China \(Shanghai\) region



</td>
<td>

See [Getting Support](https://help.sap.com/viewer/cc53ad464a57404b8d453bbadbc81ceb/alibabacloud/en-US/7d64c7f819f246a59d8860146567c0e9.html) 



</td>
<td>

 



</td>
</tr>
<tr>
<td>

 Government Cloud \(US\) region



</td>
<td colspan="2">

Please contact your operator.



</td>
</tr>
</table>

**Related Information**  


[Providing Details for Database Problems in the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/74749227a1f1470e939ddd3ce9bea1c4.html "If your problem is related to a database, the details you need to provide differ depending on the environment or infrastructure provider the database is provisioned in.") :arrow_upper_right:

