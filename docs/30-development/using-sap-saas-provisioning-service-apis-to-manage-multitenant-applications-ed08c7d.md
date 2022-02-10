<!-- loioed08c7dcb35d4082936c045e7d7b3ecd -->

# Using SAP SaaS Provisioning Service APIs to Manage Multitenant Applications

You can use the SAP Software-as-a-Service Provisioning service \(technical name: `saas-registry`\) APIs to manage your multitenant application.



<a name="loioed08c7dcb35d4082936c045e7d7b3ecd__section_kbj_f1t_kjb"/>

## Prerequisites

You've obtained your application's JSON Web Token \(JWT\) from theSAP SaaS Provisioning service instance by calling the [Getting an Application Access Token](getting-an-application-access-token-6391b5d.md) API.



<a name="loioed08c7dcb35d4082936c045e7d7b3ecd__section_gq1_f2s_h4b"/>

## Available APIs

Go to [SAP API Business Hub](https://api.sap.com/api/APISaasManagerService/resource) get information about all the available APIs and their details.



<a name="loioed08c7dcb35d4082936c045e7d7b3ecd__section_wb5_5jz_fnb"/>

## Trying Out the APIs in Swagger

To try out the APIs, go to <code>https://saas-manager.<i class="varname">&lt;app domain&gt;</i>.<i class="varname">&lt;landscape domain&gt;</i>/swagger-ui.html</code>.

> ### Example:  
> If your account is running on the Europe \(Frankfurt\) region, use this URL:
> 
> `https://saas-manager.cfapps.eu10.hana.ondemand.com/swagger-ui.html`



<a name="loioed08c7dcb35d4082936c045e7d7b3ecd__section_dqy_mfk_lqb"/>

## Trying Out the APIs in SAP API Business Hub

To learn more about the SAP API Business Hub, see [Trying Out APIs](https://help.sap.com/viewer/e56a6c50d31541ea826021dc8e721a53/Cloud/en-US/de255b9e0c374ce68151f6b9ad517aba.html).

To learn how to authorize to work with the APIs, see [Trying Out APIs in a Configured Environment](https://help.sap.com/viewer/e56a6c50d31541ea826021dc8e721a53/Cloud/en-US/f7796baaef6a48e9867298827f5028ff.html).

> ### Note:  
> If you want to work with the Application Operations for App Providers APIs under the SAP SaaS Provisioning group, you must use a different authentication method than the one described in the link above.
> 
> Do not configure an environment. Open an API that you want to try out instead, and provide the authorization token in the `Authorization` header.
> 
> To find out how to obtain the authorization token, see [Getting an Application Access Token](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/6391b5dfe4704c6c8b71a32126828e9c.html).



<a name="loioed08c7dcb35d4082936c045e7d7b3ecd__section_g44_yxc_j4b"/>

## Overview

**Base URI:** *<URL\>* you obtained from the binding object you created during the registration of your multitenant application to the SAP SaaS Provisioning service.

For more information, see the example of the binding object in the [Getting an Application Access Token](getting-an-application-access-token-6391b5d.md) topic.

<a name="loioed08c7dcb35d4082936c045e7d7b3ecd__table_xlz_cyc_j4b"/>


<table>
<tr>
<th valign="top">

Method



</th>
<th valign="top">

URL



</th>
<th valign="top">

Name



</th>
</tr>
<tr>
<td valign="top">

*GET*



</td>
<td valign="top">

<code><i class="varname">&lt;URL&gt;</i>/saas-manager/v1/application</code>



</td>
<td valign="top">

`Get application details`



</td>
</tr>
<tr>
<td valign="top">

*POST*



</td>
<td valign="top">

<code><i class="varname">&lt;URL&gt;</i>/saas-manager/v1/application/tenants/<i class="varname">&lt;tenantId&gt;</i>/subscriptions</code>



</td>
<td valign="top">

`Subscribe the tenant to an application`



</td>
</tr>
<tr>
<td valign="top">

*DELETE*



</td>
<td valign="top">

<code><i class="varname">&lt;URL&gt;</i>/saas-manager/v1/application/tenants/<i class="varname">&lt;tenantId&gt;</i>/subscriptions</code>



</td>
<td valign="top">

`Unsubscribe the tenant from an application`



</td>
</tr>
<tr>
<td valign="top">

*GET*



</td>
<td valign="top">

<code><i class="varname">&lt;URL&gt;</i>/saas-manager/v1/application/subscriptions</code>



</td>
<td valign="top">

`Get application subscriptions`



</td>
</tr>
<tr>
<td valign="top">

*PATCH*



</td>
<td valign="top">

<code><i class="varname">&lt;URL&gt;</i>/saas-manager/v1/application/tenants/<i class="varname">&lt;tenantId&gt;</i>/subscriptions</code>



</td>
<td valign="top">

`Update subscription dependencies`



</td>
</tr>
<tr>
<td valign="top">

*GET*



</td>
<td valign="top">

<code><i class="varname">&lt;URL&gt;</i>/api/v2.0/jobs/<i class="varname">&lt;jobId&gt;</i></code>



</td>
<td valign="top">

`Get subscription job information`

> ### Note:  
> This API checks the status of the job created after one of the following APIs has been called:
> 
> -   `Subscribe the tenant to an application`
> 
> -   `Unsubscribe the tenant from an application`
> 
> -   `Update subscription dependencies`



</td>
</tr>
<tr>
<td valign="top">

*PATCH*



</td>
<td valign="top">

<code><i class="varname">&lt;URL&gt;</i>/saas-manager/v1/applications/<i class="varname">&lt;appName&gt;</i>/subscription</code>



</td>
<td valign="top">

`Update subscription plan`

> ### Note:  
> You can update a subscription plan only if additional plans for the application are entitled to the subaccount you're using and if your subscription is eligible for a plan update.



</td>
</tr>
</table>

> ### Tip:  
> You can use a dedicated interface to manage your multitenant application's subscriptions.
> 
> For more information, see [Using the Subscription Management Dashboard](using-the-subscription-management-dashboard-434be69.md).

