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
<th valign="top">

Additional Configuration Parameters

</th>
</tr>
<tr>
<td valign="top">

Cloud Management Service

</td>
<td valign="top" rowspan="2">

`cis`

</td>
<td valign="top">

**`central`:** Service plan for using SAP Cloud Management service APIs to manage your global accounts, subaccounts, directories, and entitlements.

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
<td valign="top">

-   `grantType`: Choose whether to get a Client Credentials or Password grant type token when using the SAP Service Manager API, CLI, or the SAP BTP cockpit to create the service instance of the SAP Cloud Management service \(`cis`\). If you don't specify this parameter, the Password grant type is chosen by default.
-   `directoryId`: ID of a directory to allow directory administrators to use the APIs of the [Accounts and Entitlements services](https://api.sap.com/package/SAPCloudPlatformCoreServices) to perform account management actions, such as creating subaccounts and setting entitlements, in the directory.

For more information, see [Getting an Access Token for SAP Cloud Management Service APIs](getting-an-access-token-for-sap-cloud-management-service-apis-3670474.md).

</td>
</tr>
<tr>
<td valign="top">

Cloud Management Service

</td>
<td valign="top">

**`local`:** Service plan for using SAP Cloud Management service APIs to manage your environments and subscriptions to multitenant applications.

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
<td valign="top">

`grantType`: Choose whether to get a Client Credentials or Password grant type token when using the SAP Service Manager API, CLI, or the SAP BTP cockpit to create the service instance of the SAP Cloud Management service \(`cis`\). If you don't specify this parameter, the Password grant type is chosen by default. For more information, see [Getting an Access Token for SAP Cloud Management Service APIs](getting-an-access-token-for-sap-cloud-management-service-apis-3670474.md).

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

**`application`:** Service plan for application owners to manage the lifecycle of multitenant applications with SAP Software-as-a-Service Provisioning service APIs.

</td>
<td valign="top">

-   job.read
-   subscription.read
-   subscription.write
-   entitlement.read



</td>
<td valign="top">

See configuration JSON file properties in [Register the Multitenant Application to the SAP SaaS Provisioning Service](../30-development/register-the-multitenant-application-to-the-sap-saas-provisioning-service-3971151.md).

</td>
</tr>
</table>

For information about assigning these plans to a subaccount, see [Managing Entitlements and Quotas Using the Cockpit](managing-entitlements-and-quotas-using-the-cockpit-c824874.md).

**Related Information**  


[Getting an Access Token for SAP Cloud Management Service APIs](getting-an-access-token-for-sap-cloud-management-service-apis-3670474.md "The APIs of the SAP Cloud Management service for SAP BTP are protected with the OAuth 2.0 Password grant type and, in some cases, also the Client Credentials grant type. This procedure guides you through the steps to create an OAuth client and obtain an access token from SAP Authorization and Trust Management service (xsuaa) to call the APIs of the SAP Cloud Management service.")

