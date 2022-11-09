<!-- loiodcb3bfd09c4b465e9d6f599485c5b6de -->

# Access Administration Using APIs of the SAP Authorization and Trust Management Service

The REST services of the SAP Authorization and Trust Management service \(XSUAA\) provide APIs that enable you to manage entities, such as roles, shadow users, and access tokens in SAP BTP, subaccounts.

To access the API, you need an OAuth 2.0 client. For more information about how to enable the ***apiaccess*** plan, see the related links.

> ### Restriction:  
> When using the APIs, also consider the following restrictions:
> 
> **Sizing Restrictions**
> 
> 
> <table>
> <tr>
> <th valign="top">
> 
> Element
> 
> 
> 
> </th>
> <th valign="top">
> 
> Maximum Size
> 
> 
> 
> </th>
> </tr>
> <tr>
> <td valign="top">
> 
> HTTP header
> 
> 
> 
> </td>
> <td valign="top">
> 
> 16 KB
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> POST body
> 
> 
> 
> </td>
> <td valign="top">
> 
> 1 MB
> 
> 
> 
> </td>
> </tr>
> </table>

The following table provides an overview of the APIs. For more information about the APIs and their API endpoints, see *SAP API Business Hub* in the related links.

> ### Note:  
> For subaccounts based on the Neo environment, use the Neo APIs. For more information, see *Using Platform APIs* in the documentation for SAP BTP, Neo environment in the related links.

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
<tr>
<td valign="top">

User Management \(System for Cross-domain Identity Management \(SCIM\)\)



</td>
<td valign="top">

Provides functions to administrate the SAP Authorization and Trust Management service of the Cloud Foundry environment. Provision users from identity providers and manage roles and role collections. Use this API to manage shadow users; users the service provisions from your identity provider to the subaccount.



</td>
</tr>
</table>



**Related Information**  


[Access SAP Authorization and Trust Management Service APIs](access-sap-authorization-and-trust-management-service-apis-ebc9113.md "To enable programmatic access to the SAP Authorization and Trust Management service (XSUAA) in your multi-environment subaccount, create a service instance with the apiaccess plan.")

[APIs of SAP Authorization and Trust Management Service service on SAP API Business Hub](https://api.sap.com/package/authtrustmgmnt)

[Using Platform APIs](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/392af9d162694d6595499f1549978aa6.html "Platform APIs are protected with OAuth 2.0 client credentials. Create an OAuth client and obtain an access token to call the platform API methods.") :arrow_upper_right:

[Rate Limiting](../60-security/rate-limiting-d203e2d.md "This section provides information on the rate limiting in the SAP Authorization and Trust Management service.")

[Limitations on Bindings and Service Keys](../60-security/limitations-on-bindings-and-service-keys-6d3ef52.md "To preserve the stability of the SAP Authorization and Trust Management service, we allow a maximum of 1000 bindings and service keys in total per service instance. The service rejects attempts to add more bindings or service keys.")

