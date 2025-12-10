<!-- loio40c2e54a5eb140baa46ed5bb15de4d3b -->

# Map User Attributes from a Corporate Identity Provider for Platform Users

When you enable trust with a tenant of SAP Cloud Identity Services, you get an OpenID Connect \(OIDC\) application in SAP Cloud Identity Services to represent SAP BTP, in the context of platform users. When you authenticate users using a corporate identity provider, map the user attributes provided by the corporate identity provider to the attributes required by SAP BTP. The following information explains which attributes SAP BTP needs for which purpose, and how you can map those attributes.



<a name="loio40c2e54a5eb140baa46ed5bb15de4d3b__section_mvm_1pq_ddc"/>

## Prerequisites

-   Ensure that your corporate identity provider allows local users from SAP Cloud Identity Services. If local users are not allowed, you must enrich the attributes coming from the corporate identity provider. For more information, see [Enrich Assertion Attributes Coming from Corporate IdP](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/enrich-assertion-attributes-coming-from-corporate-idp?version=Cloud).




<a name="loio40c2e54a5eb140baa46ed5bb15de4d3b__section_yv2_3cr_qsb"/>

## Finding the Application for Your Platform Users

The name of the application in the administration console of SAP Cloud Identity Services that represents SAP BTP in the context of platform users has the name, *SAP Business Technology Platform*.

For more information, see [OpenID Connect](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/a789c9c8c0f5439da8c30b5d9e43bece.html) in the documentation of SAP Cloud Identity Services.



<a name="loio40c2e54a5eb140baa46ed5bb15de4d3b__section_wdh_bwq_qsb"/>

## Customizing Attribute Mappings

There are several options to customize attribute mappings in SAP Cloud Identity Services, depending on whether identity federation is enabled or disabled. For more information about identity federation, see [Configure Identity Federation](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/c029bbbaefbf4350af15115396ba14e2.html?version=Cloud).

-   When identity federation is disabled, SAP Cloud Identity Services always propagates all the attributes received from the corporate identity provider to all the applications, on a 1:1 basis. You have the following options:
    -   Configure the corporate identity provider to directly send the attributes \(see the table below\).

    -   If needed, use **enriched token claims** or **enriched assertion attributes** \(depending on whether the corporate identity provider is connected with SAML or OIDC\) to map the attributes sent by the corporate identity provider, to the attribute names needed by SAP BTP.

        **[Enriched token claims](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/f19e580088e74aaa96087f1def8972cd.html?version=Cloud)** or **[enriched assertion attributes](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/7124201682434efb946e1046fde06afe.html?version=Cloud&q=Enriched%20assertion%20attributes)** add additional attributes, either based on the corporate identity provider attributes \(for example, by renaming them\) or on static values.


-   When identity federation is enabled, SAP Cloud Identity Services doesn't automatically propagate any attributes from the corporate identity provider to the application. This option requires mappings in the SAP Cloud Identity Services application, for each attribute that is needed by the application.

    Use the attributes in the SAP Cloud Identity Services application representing SAP BTP.

    > ### Note:  
    > You can add attribute sources or disable the default application attributes. You can also add self-defined attributes for mapping to role collections.
    > 
    > For example, you have so many groups being added to your token and you're running into size limits. You can disable the standard groups configuration and add a regular expression to include only those groups, which begin with BTP. So, to the *groups* attribute, you add a source of type `Expression` with the value `${companyGroups:regex[BTP.*]}`.
    > 
    > For more information, see [Configuring Attributes Based on Flexible Expressions](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/configure-default-attributes-sent-to-application?version=Cloud).
    > 
    > To check which groups SAP Cloud Identity Services actually sends, use the troubleshooting logs for OpenID Connect. For more information, see [Logging OpenID Connect Tokens](https://help.sap.com/docs/identity-authentication/identity-authentication/logging-openid-connect-tokens?version=Cloud) in the documentation for SAP Cloud Identity Services.

    > ### Note:  
    > Ensure that you enter the accurate value names for the attributes as they are provided by your corporate identity provider.

    **Default Configuration of Application Attributes in SAP Cloud Identity Services**


    <table>
    <tr>
    <th valign="top">

    Attribute Name
    
    </th>
    <th valign="top">

    Source
    
    </th>
    <th valign="top">

    Attribute Value
    
    </th>
    </tr>
    <tr>
    <td valign="top" rowspan="2">
    
    `email` 
    
    </td>
    <td valign="top">
    
    Identity Directory
    
    </td>
    <td valign="top">
    
    `Email` 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Corporate Identity Provider
    
    </td>
    <td valign="top">
    
    `email` 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `groups` 
    
    </td>
    <td valign="top">
    
    Identity Directory
    
    </td>
    <td valign="top">
    
    `All Groups` 
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="2">
    
    `mail` 
    
    </td>
    <td valign="top">
    
    Identity Directory
    
    </td>
    <td valign="top">
    
    `Email` 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Corporate Identity Provider
    
    </td>
    <td valign="top">
    
    `email` 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `uuid` 
    
    </td>
    <td valign="top">
    
    Identity Provider
    
    </td>
    <td valign="top">
    
    `User ID` 
    
    </td>
    </tr>
    </table>
    
    If the corporate identity provider sends user attributes for email address, first and last name with other names than *mail*, *first\_name*, or *last\_name*, set the right attribute name by replacing those values.

    > ### Example:  
    > If your corporate identity provider sends users' last names as the `sn` attribute, add the corporate identity provider as source to the `last_name` attribute with the value `sn`.

    For more information, see [User Attributes](https://help.sap.com/docs/identity-authentication/identity-authentication/user-attributes?version=Cloud) in the documentation of SAP Cloud Identity Services.


The following table provides the information needed for mapping the attributes.

The subject name identifier attribute is used by SAP BTP to uniquely identify the user in Neo subaccounts. The email address is used as the user identifier for the global account, directory, multi-environment subaccount, and the Cloud Foundry environment.

For more information, see [Configure the Subject Name Identifier Sent to the Application](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/1d020e3a3ba34c43a71fde70bfa6419a.html) in the documentation of SAP Cloud Identity Services.

**Attribute Mapping in SAP Cloud Identity Services Tokens**


<table>
<tr>
<th valign="top">

User Attribute Expected by SAP BTP

</th>
<th valign="top">

Purpose

</th>
</tr>
<tr>
<td valign="top">

`Subject name identifier` 

</td>
<td valign="top">

User identifier for Neo subaccounts.

Default value: ***User ID***

</td>
</tr>
<tr>
<td valign="top">

`email` 

</td>
<td valign="top">

Email address of the user.

> ### Note:  
> User identifier for all the account levels \(global account, directory, multi-environment subaccount\), and for the Cloud Foundry environment.

The email addresses of all the users in the SAP Cloud Identity Services tenant must be unique.

For more information, see the [prerequisites](establish-trust-and-federation-of-custom-identity-providers-for-platform-users-c368984.md#loioc36898473d704e07a33268c9f9d29515__prereq_avv_mp1_5tb) for establishing trust and federation of custom identity providers for platform users.

</td>
</tr>
<tr>
<td valign="top">

`first_name` 

</td>
<td valign="top">

First name of the user.

</td>
</tr>
<tr>
<td valign="top">

`last_name` 

</td>
<td valign="top">

Last name of the user.

</td>
</tr>
<tr>
<td valign="top">

`groups` 

</td>
<td valign="top">

Any groups the subject is assigned to in the identity provider.

</td>
</tr>
</table>

**Related Information**  


[Establish Trust and Federation Between SAP Authorization and Trust Management Service and SAP Cloud Identity Services](establish-trust-and-federation-between-sap-authorization-and-trust-management-service-a-161f8f0.md "Use your SAP Cloud Identity Services tenant as an identity provider or a proxy to your own identity provider hosting your business users. This method avoids the upload and download of SAML meta data by using OpenID Connect (OIDC) to establish trust.")

[Map User Attributes from a Corporate Identity Provider for Business Users](map-user-attributes-from-a-corporate-identity-provider-for-business-users-bbb4a8a.md "When you enable trust with a tenant of SAP Cloud Identity Services, you get an OpenID Connect (OIDC) application in SAP Cloud Identity Services to represent your subaccount, in the context of business users. When SAP Cloud Identity Services authenticates users using a corporate identity provider, map the user attributes provided by the corporate identity provider to the attributes required by your applications.")

