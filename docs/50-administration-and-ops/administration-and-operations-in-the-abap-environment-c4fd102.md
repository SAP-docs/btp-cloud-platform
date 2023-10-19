<!-- loioc4fd10279d6e44be8e65b6841acb52f6 -->

# Administration and Operations in the ABAP Environment

As an administrator in the ABAP environment, you have different tools and features available that support you in your daily work.



<a name="loioc4fd10279d6e44be8e65b6841acb52f6__section_fyr_2wx_5vb"/>

## Task Examples

As an administrator in the ABAP environment, you focus on administration and operational tasks that aren't managed by SAP. Such tasks can include, for example:

-   Account and organization management, including identity and access management for your users
-   Monitoring of performance issues and exceptions in your own applications

    Such a monitoring includes response times of application-related communication endpoints, SQL statements issued by the application, application jobs, or ABAP runtime errors originating from custom code.

-   System sizing, including a regular review of the overall resource utilization

    Such a system sizing can include a daily check of resource utilization peaks and a monthly check of resource utilization trends.

-   Software lifecycle of custom applications \(add-on updates or custom transports\)
-   Tenant management if you manage multi-tenant custom applications
-   Monitoring of integrations with other cloud or on-premise based services



<a name="loioc4fd10279d6e44be8e65b6841acb52f6__section_jh3_3zx_5vb"/>

## Tools, Apps, and Functions: Overview

Here's an overview of tools, apps, and functions that are available to you to perform administration and operations tasks, such as the following:


<table>
<tr>
<th valign="top">

Task



</th>
<th valign="top">

Tools, Apps, or Functions



</th>
</tr>
<tr>
<td valign="top">

Managing accounts and organizations



</td>
<td valign="top">

As an administrator in the ABAP environment, you can create additional accounts for users. In addition, you can manage orgs, spaces, and space quota plans to organize your subaccount into smaller units. You use the tools for account and org administration from the Cloud Foundry environment for this purpose.

For more information, see the following:

-   [Account Administration in the Cockpit](https://help.sap.com/docs/btp/sap-business-technology-platform/account-administration-in-cockpit?locale=en-US&version=Cloud)

-   [Org Administration Using the Cockpit](https://help.sap.com/docs/btp/sap-business-technology-platform/org-administration-using-cockpit?locale=en-US&version=Cloud)

-   [Org Administration Using the Cloud Foundry CLI](https://help.sap.com/docs/btp/sap-business-technology-platform/org-administration-using-cloud-foundry-cli?locale=en-US&version=Cloud) 


For more information about business roles in the ABAP environment, see [Business Catalogs and Business Roles](business-catalogs-and-business-roles-da32065.md).



</td>
</tr>
<tr>
<td valign="top">

Performing administration tasks, such as identity and access management, business configuration, communication management, and more



</td>
<td valign="top">

In the Fiori launchpad, you can find apps that support you as an administrator or developer with various operational tasks. For more information, see [SAP Fiori Apps in the ABAP Environment](sap-fiori-apps-in-the-abap-environment-dbfaac8.md).



</td>
</tr>
<tr>
<td valign="top">

Performing technical operations, such as monitoring the performance of your systems as well as the exhaustion of your purchased service volume



</td>
<td valign="top">

You can use tools such as the technical monitoring cockpit, health monitoring, and more. There’s also guidance available for the most common tasks in technical operations and for system sizing. For more information, see [Technical Operations](technical-operations-181ce28.md).



</td>
</tr>
<tr>
<td valign="top">

Operating communications when you integrate your system or solution with other systems to enable data exchange in your ABAP environment



</td>
<td valign="top">

For more information, see [Communication Operations](communication-operations-ac9137d.md).



</td>
</tr>
<tr>
<td valign="top">

Performing lifecycle management operations and system administration tasks such as

-   stopping currently unused systems and scheduling \(regularly recurring\) stop/starts for a system to save resource usage.

-   restoring recently deleted tenants that are still in retention time.

-   monitoring operations.




</td>
<td valign="top">

The [Landscape Portal](../30-development/landscape-portal-5eb70fb.md) functions as a central tool for providers to perform lifecycle management operations and system admininistation tasks, see [Manage System Hibernation](../30-development/manage-system-hibernation-26e2ee1.md), [Restore Consumer Tenants](../30-development/restore-consumer-tenants-619c40e.md), [Operations Dashboard](../30-development/operations-dashboard-0a3a735.md).



</td>
</tr>
<tr>
<td valign="top">

Getting notifications about planned maintenance events and about unplanned service outages



</td>
<td valign="top">

Register for the Cloud Availability Center. For more information, see the information about the [Cloud Availability Center](https://support.sap.com/en/my-support/systems-installations/cac.html)on SAP Support Portal.



</td>
</tr>
<tr>
<td valign="top">

Operating cloud-centric SAP solution landscapes



</td>
<td valign="top">

SAP Cloud ALM is the central entry point to operate cloud-centric SAP solution landscapes. You can use it for the following:

-   Central monitoring of service level indicators \(real user monitoring, job monitoring, exception monitoring\)
-   Central monitoring of key performance indicators for system and applications \(health monitoring\)
-   Alert notifications \(currently limited to SAP-defined metrics of the health monitoring framework\)

For more information about the available metrics for health monitoring, see [Central Health Monitoring Using SAP Focused Run and SAP Cloud ALM](central-health-monitoring-using-sap-focused-run-and-sap-cloud-alm-8d6e2e7.md).



</td>
</tr>
</table>

