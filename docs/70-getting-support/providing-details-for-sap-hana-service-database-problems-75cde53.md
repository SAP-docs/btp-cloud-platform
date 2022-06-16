<!-- loio75cde5383e8d42dabd039b7dceef9511 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Providing Details for SAP HANA Service Database Problems

If your problem is related to a SAP HANA service database, the details you need to provide differ depending on the environment or infrastructure provider the database is provisioned in.




<table>
<tr>
<th valign="top">

Infrastructure Provider



</th>
<th valign="top">

Details You Need to Provide



</th>
<th valign="top">

How to Find the Details You Need



</th>
</tr>
<tr>
<td valign="top">

Azure regions



</td>
<td valign="top" rowspan="2">

The URL of the space the database is provisioned in



</td>
<td valign="top" rowspan="2">

1.  In the SAP BTP cockpit, navigate to the org and space the database is provisioned in.

2.  In the navigation area, go to *SAP HANA* \> *Database Systems*.

3.  Choose the affected *Database System*.

4.  Copy the URL from the overview of the affected database system.

    Example URL:

    `https://account.hana.ondemand.com/cockpit#/globalaccount/<id>/subaccount/<id>/org/<id>/dbsystems/<id>/overview`




</td>
</tr>
<tr>
<td valign="top">

AWS regions

\(databases provisioned before June 4, 2018\)



</td>
</tr>
<tr>
<td valign="top">

AWS regions

\(databases provisioned after June 4, 2018\)



</td>
<td valign="top" rowspan="2">

The service instance ID



</td>
<td valign="top" rowspan="2">

1.  In the SAP BTP cockpit, navigate to the space the SAP HANA service instance is provisioned in.
2.  In the navigation area, choose *Services* \> *Service Instances*.
3.  In the list of available services, find your SAP HANA service instance and choose <span class="SAP-icons"></span> Open Dashboard from the *Actions* column.
4.  Copy the service instance GUID under *Details* \> *ID*.

    Example GUID: ad539b83-39bd-4ff4-8b41-1a5dfdfca7ea




</td>
</tr>
<tr>
<td valign="top">

Google Cloud regions



</td>
</tr>
<tr>
<td valign="top">

 China \(Shanghai\) region



</td>
<td valign="top">

See [Getting Support](https://help.sap.com/viewer/cc53ad464a57404b8d453bbadbc81ceb/alibabacloud/en-US/7d64c7f819f246a59d8860146567c0e9.html) 



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

 Government Cloud \(US\) region



</td>
<td valign="top" colspan="2">

Please contact your operator.



</td>
</tr>
</table>

**Related Information**  


[Providing Details for Database Problems in the Neo Environment](https://help.sap.com/viewer/663f91a6573b49ae9fa5f0007abb4d18/Internal/en-US/74749227a1f1470e939ddd3ce9bea1c4.html "If your problem is related to a database, the details you need to provide differ depending on the environment or infrastructure provider the database is provisioned in.") :arrow_upper_right:

