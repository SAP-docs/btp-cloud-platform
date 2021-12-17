<!-- loioa508b724bf6d457ca7ac024b8e4b8457 -->

# SAP Cloud Management Service - Service Plans

Describes the service plans for the SAP Cloud Management service for SAP BTP and the scopes that they provide. The techncial name for this service is `cis`.


<table>
<tr>
<th valign="top">

Service Display Name



</th>
<th valign="top">

Technical Name



</th>
<th valign="top">

Service Plan



</th>
<th valign="top">

Scopes



</th>
</tr>
<tr>
<td valign="top">

Cloud Management Service



</td>
<td valign="top" rowspan="2">

cis



</td>
<td valign="top">

**central:** Service plan for using SAP Cloud Management service APIs to manage your global accounts, subaccounts, directories, and entitlements.



</td>
<td valign="top">

-   global-account.read
-   global-account.update
-   global-account.subaccount.read
-   global-account.subaccount.create
-   global-account.subaccount.update
-   global-account.subaccount.delete
-   global-account.account-directory.read
-   global-account.account-directory.create
-   global-account.account-directory.update
-   global-account.account-directory.delete
-   global-account.entitlement
-   global-account.entitlement.subaccount.update
-   global-account.region.read
-   catalog.product.update
-   catalog.product.delete
-   directory.entitlement.update
-   directory.entitlement.read
-   job.read
-   cis-central.event.read




</td>
</tr>
<tr>
<td valign="top">

Cloud Management Service



</td>
<td valign="top">

**local:** Service plan for using SAP Cloud Management service APIs to manage your environments and subscriptions to multitenant applications.



</td>
<td valign="top">

-   subaccount.entitlement.read
-   subaccount.environment.read
-   subaccount.environment.create
-   subaccount.environment.delete
-   subaccount.application.subscription.read
-   subaccount.application.subscription.update
-   job.read
-   cis-local.event.read




</td>
</tr>
<tr>
<td valign="top">

SaaS Provisioning Service



</td>
<td valign="top">

`saas-registry`



</td>
<td valign="top">

**application:** Service plan for application owners to manage the lifecycle of multitenant applications with SAP Software-as-a-Service Provisioning service APIs.



</td>
<td valign="top">

-   job.read
-   subscription.read
-   subscription.write
-   entitlement.read



</td>
</tr>
</table>

