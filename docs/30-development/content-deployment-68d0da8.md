<!-- loio68d0da84bc1e4cfcadd8a24141dadac6 -->

# Content Deployment

SAP Business Technology Platform Cloud Foundry supports the lifecycle of all standard Cloud Foundry entities, such as applications and services. To satisfy all business requirements, SAP Business Technology Platform Cloud Foundry also supports the lifecycle of other entities that do not match 1-to-1 to CF native entities.

SAP traditionally provides its customers with complex business solutions, which work with their own entities and content. Every service might have its own content with a specific format that is developed, provided, or consumed by end customers.

SAP Workflow Management provides the possibility for SAP partners to develop their own BPM workflows \(for example, Leave Request flow\) and provide them to end customers. In turn, end customers can easily import and use the developed BPM workflows.

With multitarget applications, you can manage the lifecycle of content provided by different SAP applications. This way, by using one standard approach via an MTA, you can deploy various kinds of SAP application content in your accounts, normally done on the CF space level.

> ### Restriction:  
> Content deployment used with [blue-green deployment](https://help.sap.com/docs/btp/sap-business-technology-platform/blue-green-deployment-of-multitarget-applications) will be done during the first phase when idle suffixes and temporary routes are used. The same rule is applicable for all content deployment mechanisms – either with direct content deployment or with content deployers \(`hdi-deploy`, `html5-app-deployer`, `portal deployer`\). HTTP Destinations, created with direct content deployment, will not be updated after the validation phase, so avoid using default resolvable parameters `${default-host}`, `${default-uri}`, `${default-url}`. Configurations that include idle suffixes and temporary routes may persist after the MTA deployment finishes. Content that was already deployed during the first phase cannot be reverted or removed. It will be necessary to trigger a new MTA deployment.



<a name="loio68d0da84bc1e4cfcadd8a24141dadac6__section_c2r_1w3_wxb"/>

## Supported Content Deployment Mechanisms

-   Using content applications – there is a dedicated SAP provisioned content deployer for each content type that communicates with the dedicated content backend
    -   \[DEPRECATED\] Deploying Content with Simulated App Execution
    -   Deploying Content with CF task execution

-   Using direct content deployment – there is a direct communication between the SAP Cloud Deployment service and the content backends
    -   Deploying Content with Generic Application Content Deployment
    -   CPI content deployment




<a name="loio68d0da84bc1e4cfcadd8a24141dadac6__section_kxw_kw3_wxb"/>

## Supported MTA Module Types for Content Deployment

****


<table>
<tr>
<th valign="top">

Module Type

</th>
<th valign="top">

Content Deployment Mechanism

</th>
</tr>
<tr>
<td valign="top">

`com.sap.portal.site-content`

</td>
<td valign="top">

Simulated App Execution

</td>
</tr>
<tr>
<td valign="top">

`com.sap.html5.application-content`

</td>
<td valign="top">

Simulated App Execution

</td>
</tr>
<tr>
<td valign="top">

`com.sap.portal.content`

</td>
<td valign="top">

CF task execution

</td>
</tr>
<tr>
<td valign="top">

`com.sap.html5.application.content`

</td>
<td valign="top">

CF task execution

</td>
</tr>
<tr>
<td valign="top">

`com.sap.xs.hdi`

</td>
<td valign="top">

CF task execution

</td>
</tr>
<tr>
<td valign="top">

`com.sap.application.content`

</td>
<td valign="top">

Generic Application Content Deployment

</td>
</tr>
<tr>
<td valign="top">

`com.sap.integration`

</td>
<td valign="top">

CPI content deployment

</td>
</tr>
<tr>
<td valign="top">

`com.sap.api.management`

</td>
<td valign="top">

CPI content deployment

</td>
</tr>
</table>

For all predefined parameters and properties for each MTA module type, see [MTA Module Types](modules-177d34d.md#loio177d34d45e3d4fd99f4eeeffc5814cf1__section_mtaModuleTypes).

