<!-- loio7fb79d7a811146679646ebfb5844b858 -->

# Display Technical Users

This app shows all technical users that exist in your tenant. To call the app, log on to your SAP Fiori Launchpad and go to *Identity and Access Management* \> *Display Technical Users*.



<a name="loio7fb79d7a811146679646ebfb5844b858__purpose"/>

## Purpose

With this app, you can display technical users. These technical users can be services that are used to automate technical tasks in the system. All users are assigned to one of the following user groups:



<a name="loio7fb79d7a811146679646ebfb5844b858__d158e24"/>User Groups


<table>
<tr>
<th valign="top">

Group



</th>
<th valign="top">

Explanation



</th>
</tr>
<tr>
<td valign="top">

**SAP Technical Users**



</td>
<td valign="top">

These users are predefined by SAP to run tasks in the system for cloud operation activities and automated processes. SAP technical users are also required for customer-specific tasks, such as running and scheduling jobs. The required job template contains the SAP technical user needed to run the job by default.



</td>
</tr>
<tr>
<td valign="top">

**Communication Users**



</td>
<td valign="top">

In this group, all communication users used in communication arrangements that are managed by customers are displayed.

Communication users are technical users required for communication between your system and any integrated system. The following types of communication users are available:

-   SAP communication users: Predefined by SAP

-   Communication users: Created by customers

    Custom communication users are created in the *Maintain Communication Users* app and are assigned to systems for inbound and outbound communication. These technical users either use basic authentication or certificates to communicate between your system and the integrated system. The communication system, together with a communication scenario, is assigned to a communication arrangement. Thus, all communication scenario roles are assigned to the communication user which provides this user with all permission required for the connection between your system and the integrated system.




</td>
</tr>
<tr>
<td valign="top">

**Support Users**



</td>
<td valign="top">

SAP uses support users to provide customers with support if issues occur in the system. These users only exist temporarily and are deleted by SAP after the support process is completed.



</td>
</tr>
</table>



<a name="loio7fb79d7a811146679646ebfb5844b858__section_m3x_rzg_jfb"/>

## Key Features

You can use this app to:



-   Display all technical users in the system.

-   Export user data \(such as *User ID* or *User Group*\) to a spreadsheet if required


> ### Note:  
> To lock and unlock communication users, use the *Maintain Communication Users* app. See section Related Information.



<a name="loio7fb79d7a811146679646ebfb5844b858__supported_devices"/>

## Supported Device Types

-   Desktop

-   Tablet




<a name="loio7fb79d7a811146679646ebfb5844b858__section_bx3_335_ksb"/>

## SAP Technical Users


<table>
<tr>
<th valign="top">

 



</th>
<th valign="top">

 



</th>
</tr>
<tr>
<td valign="top">

`SAP*`



</td>
<td valign="top">

This user has always been used in on-premise systems to log on to newly created tenants. This user is locked in your tenant and it'sn't used for any system operation.



</td>
</tr>
<tr>
<td valign="top">

`SAP_CUST_BUS`



</td>
<td valign="top">

This user is a reference user assigned to all customer business users and SAP support users. General authorizations required for basic system access are assigned through this reference \(for example to access Fiori Launchpad\). The user can't be used by itself. It's locked and has no logon credentials.



</td>
</tr>
<tr>
<td valign="top">

`SAP_LMADM`



</td>
<td valign="top">

This user is used for system internal, automated software lifecycle management across all tenants. It's used in processes that need to update tenant-specific data after changes to tenant-independent data. This user is unlocked. External system logon isn't possible.



</td>
</tr>
<tr>
<td valign="top">

`SAP_SMTP_IN`



</td>
<td valign="top">

This user is used as the SMTP mail server user.



</td>
</tr>
<tr>
<td valign="top">

`SAP_SPC`



</td>
<td valign="top">

This user is used for SAP-internal automated system operation.



</td>
</tr>
<tr>
<td valign="top">

`SAP_SYSTEM`



</td>
<td valign="top">

This user is the default user to run system-internal technical jobs.



</td>
</tr>
<tr>
<td valign="top">

`SAP_WFRT`



</td>
<td valign="top">

This user is used by Business Workflow for the automated background processing of work items.



</td>
</tr>
<tr>
<td valign="top">

`SAP_WSRT`



</td>
<td valign="top">

This user is used for system internal processing in the Web service runtime.



</td>
</tr>
</table>



<a name="loio7fb79d7a811146679646ebfb5844b858__customer_component"/>

## Component for Customer Incidents

If you need support or experience issues, please report an incident under component `BC-SRV-APS-IAM`.

