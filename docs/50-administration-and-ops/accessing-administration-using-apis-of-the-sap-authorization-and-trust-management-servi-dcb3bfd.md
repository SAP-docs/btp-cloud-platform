<!-- loiodcb3bfd09c4b465e9d6f599485c5b6de -->

# Accessing Administration Using APIs of the SAP Authorization and Trust Management Service

The REST services of the SAP Authorization and Trust Management service \(XSUAA\) provide APIs that enable you to manage entities, such as roles, shadow users, and access tokens in global accounts, directories, and multi-environment subaccounts.

> ### Note:  
> To manage Neo subaccounts, use the Neo APIs. For more information, see [Using Platform APIs](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/392af9d162694d6595499f1549978aa6.html "Platform APIs are protected with OAuth 2.0 client credentials. Create an OAuth client and obtain an access token to call the platform API methods.") :arrow_upper_right:.



<a name="loiodcb3bfd09c4b465e9d6f599485c5b6de__section_urt_lrq_zzb"/>

## API Overview

The following table provides an overview of the APIs. For more information about the APIs and their API endpoints, see *SAP Business Accelerator Hub* in the related links.

**APIs of SAP Authorization and Trust Management Service**


<table>
<tr>
<th valign="top">

API

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

User Management \(System for Cross-domain Identity Management \(SCIM\)\)

</td>
<td valign="top">

Provides functions to administrate the SAP Authorization and Trust Management service of the Cloud Foundry environment. Provision users from identity providers and manage roles and role collections. Use this API to manage shadow users; users the service provisions from your identity provider to the subaccount.

See [SAP BTP XS Advanced UAA \(Cloud Foundry\)](https://help.sap.com/docs/link-disclaimer?site=https%3A%2F%2Fhelp.sap.com%2Fdocs%2Fidentity-provisioning%2Fidentity-provisioning%2Ftarget-sap-btp-xs-advanced-uaa-cloud-foundry) for more information.

</td>
</tr>
<tr>
<td valign="top">

Authorization

</td>
<td valign="top">

Provides functions to administrate the SAP Authorization and Trust Management service of Cloud Foundry environment. Manage service instances of the SAP Authorization and Trust Management service. You can also manage roles, role templates, and role collections of your subaccount.

</td>
</tr>
<tr>
<td valign="top">

Identity Provider Management

</td>
<td valign="top">

Provides functions to manage identity providers in in the Cloud Foundry environment.

</td>
</tr>
<tr>
<td valign="top">

Security Settings

</td>
<td valign="top">

Provides functions to manage the security settings of an account in Cloud Foundry environment. Use this API to manage access token validity and signing keys.

</td>
</tr>
</table>



**Related Information**  


[APIs of SAP Authorization and Trust Management Service service on SAP Business Accelerator Hub](https://api.sap.com/package/authtrustmgmnt)

[Using Platform APIs](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/392af9d162694d6595499f1549978aa6.html "Platform APIs are protected with OAuth 2.0 client credentials. Create an OAuth client and obtain an access token to call the platform API methods.") :arrow_upper_right:

[Rate Limiting](../60-security/rate-limiting-d203e2d.md "This section provides information on the rate limiting in the SAP Authorization and Trust Management service.")

[Limits for Technical Artifacts of the SAP Authorization and Trust Management Service](../60-security/limits-for-technical-artifacts-of-the-sap-authorization-and-trust-management-service-6d3ef52.md "To improve the resiliency of the SAP Authorization and Trust Management service, we have introduced limitations on technical artifacts of the service.")

