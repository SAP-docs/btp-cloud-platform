<!-- loioa508b724bf6d457ca7ac024b8e4b8457 -->

# SAP Cloud Management Service - Service Plans

Describes the service plans for the SAP Cloud Management service for SAP BTP and the scopes that they provide. The techncial name for this service is `cis`.


<table>
<tr>
<th>

Service Display Name



</th>
<th>

Technical Name



</th>
<th>

Service Plan



</th>
<th>

Scopes



</th>
</tr>
<tr>
<td>

Cloud Management Service



</td>
<td rowspan="2">

cis



</td>
<td>

**central:** Service plan for using SAP Cloud Management service APIs to manage your global accounts, subaccounts, directories, and entitlements.



</td>
<td>

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
<td>

Cloud Management Service



</td>
<td>

**local:** Service plan for using SAP Cloud Management service APIs to manage your environments and subscriptions to multitenant applications.



</td>
<td>

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
<td>

SaaS Provisioning Service



</td>
<td>

`saas-registry`



</td>
<td>

**application:** Service plan for application owners to manage the lifecycle of multitenant applications with SAP Software-as-a-Service Provisioning service APIs.



</td>
<td>

-   job.read
-   subscription.read
-   subscription.write
-   entitlement.read



</td>
</tr>
</table>

