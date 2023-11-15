<!-- loio4b83be95f7db4fddba5c46d388ebf39a -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Kyma Functionalities

SAP BTP, Kyma runtime and open source project "Kyma" offer slightly different functionalities and install a different set of components.



For all functionalities that the Kyma environment offers, see the official [project "Kyma" documentation](https://kyma-project.io/#/).

**Functionality Comparison**


<table>
<tr>
<th valign="top">

Functionality

</th>
<th valign="top">

open source project "Kyma"

</th>
<th valign="top">

SAP BTP, Kyma runtime

</th>
</tr>
<tr>
<td valign="top">

Service Level Agreements

</td>
<td valign="top">

:x:

</td>
<td valign="top">

:heavy_check_mark:

</td>
</tr>
<tr>
<td valign="top">

Managed Kubernetes

</td>
<td valign="top">

:x:

</td>
<td valign="top">

:heavy_check_mark:

</td>
</tr>
<tr>
<td valign="top">

Managed Kyma

</td>
<td valign="top">

:x:

</td>
<td valign="top">

:heavy_check_mark:

</td>
</tr>
<tr>
<td valign="top">

Monitoring<sup>[1](kyma-functionalities-4b83be9.md#loio4b83be95f7db4fddba5c46d388ebf39a__ol_tcn_pdp_pvb)</sup>

</td>
<td valign="top">

:heavy_check_mark:

</td>
<td valign="top">

limited \(no customization in SAP BTP, Kyma runtime\)

</td>
</tr>
<tr>
<td valign="top">

Kyma CLI

</td>
<td valign="top">

:heavy_check_mark:

</td>
<td valign="top">

limited \(SAP BTP, Kyma runtime supports commands for serverless Functions, not the commands related to installation.\)

</td>
</tr>
<tr>
<td valign="top">

Centrally hosted Kyma dashboard

</td>
<td valign="top">

:x:

</td>
<td valign="top">

:heavy_check_mark:

</td>
</tr>
<tr>
<td valign="top">

System landscape management in SAP BTP cockpit

</td>
<td valign="top">

:x:

</td>
<td valign="top">

:heavy_check_mark:

</td>
</tr>
<tr>
<td valign="top">

In-cluster system landscape management \(Application Connector\)

</td>
<td valign="top">

:heavy_check_mark:

</td>
<td valign="top">

:x:

</td>
</tr>
</table>

> ### Caution:  
> 1.  The Monitoring capability based on Prometheus, which enables you to query metrics using Grafana, has been deprecated. For details, see [What's New for Kyma on Jan 20, 2023](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?Component=Kyma%20Runtime&locale=en-US&version=Cloud&Valid_as_Of=2023-01-20%3A2023-01-20). In the future, it will be removed from both, SAP BTP, Kyma runtime and open source project "Kyma".

