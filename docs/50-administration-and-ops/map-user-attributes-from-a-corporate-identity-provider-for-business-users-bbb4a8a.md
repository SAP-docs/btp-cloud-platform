<!-- loiobbb4a8a1eae04843967a8a629dcb30f9 -->

# Map User Attributes from a Corporate Identity Provider for Business Users

When you enable trust with a tenant of SAP Cloud Identity Services, you get an OpenID Connect \(OIDC\) application in SAP Cloud Identity Services to represent your subaccount, in the context of business users. When SAP Cloud Identity Services authenticates users using a corporate identity provider, map the user attributes provided by the corporate identity provider to the attributes required by your applications.



<a name="loiobbb4a8a1eae04843967a8a629dcb30f9__section_yv2_3cr_qsb"/>

## Finding the Application for Your Subaccount

The name of the application in the administration console of SAP Cloud Identity Services that represents your subaccount has the prefix ***SAP BTP subaccount*** or ***XSUAA\_*** and the display name of your subaccount.

If your subaccount is named ***My Subaccount***, the resulting application in SAP Cloud Identity Services is ***SAP BTP subaccount My Subaccount*** or ***XSUAA\_My Subaccount***.



<a name="loiobbb4a8a1eae04843967a8a629dcb30f9__section_wdh_bwq_qsb"/>

## Customizing Attribute Mappings

There are several options to customize attribute mappings in SAP Cloud Identity Services, depending on whether identity federation is enabled or disabled.

For more information about identity federation, see [Configure Identity Federation](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/c029bbbaefbf4350af15115396ba14e2.html?version=Cloud).

-   When identity federation is disabled, SAP Cloud Identity Services always propagates all the attributes received from the corporate identity provider to all the applications, on a 1:1 basis. You have the following options:
    -   Configure the corporate identity provider to directly send the attributes.

    -   If needed, use **enriched token claims** or **enriched assertion attributes** \(depending on whether the corporate identity provider is connected with SAML or OIDC\) to map the attributes sent by the corporate identity provider, to the attribute names needed by SAP BTP.

        **[Enriched token claims](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/f19e580088e74aaa96087f1def8972cd.html?version=Cloud)** or **[enriched assertion attributes](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/7124201682434efb946e1046fde06afe.html?version=Cloud&q=Enriched%20assertion%20attributes)** add additional attributes, either based on the corporate identity provider attributes \(for example, by renaming them\) or on static values.


-   When identity federation is enabled, SAP Cloud Identity Services doesn't automatically propagate any attributes from the corporate identity provider to the application. This option requires mappings in the SAP Cloud Identity Services application, for each attribute that is needed by the application.

    Use the *Attributes* in the SAP Cloud Identity Services application representing your subaccount.

    SAP BTP expects the following attributes. The default configuration of the trust configuration sets up the values in the following table in the SAP Cloud Identity Services tenant.


    <table>
    <tr>
    <th valign="top">

    Self-Defined Attributes
    
    </th>
    <th valign="top">

    Identity Directory
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `email`
    
    </td>
    <td valign="top">
    
    `Email`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `email_verified`
    
    </td>
    <td valign="top">
    
    `Email Verified`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `family_name`
    
    </td>
    <td valign="top">
    
    `Last Name`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `given_name`
    
    </td>
    <td valign="top">
    
    `First Name`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `groups`
    
    </td>
    <td valign="top">
    
    `Groups`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `user_uuid`
    
    </td>
    <td valign="top">
    
    `Global user ID`
    
    </td>
    </tr>
    </table>
    
    If the corporate identity provider sends user attributes with other names, set the source to the corporate identity provider and the value to the correct attribute name.

    > ### Example:  
    > If your corporate identity provider sends users' last names as the `sn` attribute, add the corporate identity provider as source to the `last_name` attribute with the value `sn`.

    > ### Note:  
    > To check which groups SAP Cloud Identity Services actually sends, use the troubleshooting logs for OpenID Connect. For more information, see [Logging OpenID Connect Tokens](https://help.sap.com/docs/identity-authentication/identity-authentication/logging-openid-connect-tokens?version=Cloud) in the documentation for SAP Cloud Identity Services.

    **Customized Last Name Attribute Configuration in SAP Cloud Identity Services**


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
    <td valign="top">
    
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
    
    `email_verified` 
    
    </td>
    <td valign="top">
    
    Identity Directory
    
    </td>
    <td valign="top">
    
    `Email Verified` 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `family_name` 
    
    </td>
    <td valign="top">
    
    Identity Directory
    
    </td>
    <td valign="top">
    
    `Last Name` 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `given_name` 
    
    </td>
    <td valign="top">
    
    Identity Directory
    
    </td>
    <td valign="top">
    
    `First Name` 
    
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
    
    `Groups` 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `last_name` 
    
    </td>
    <td valign="top">
    
    Corporate Identity Provider
    
    </td>
    <td valign="top">
    
    > ### Example:  
    > `sn`


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
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
    
    `user_uuid` 
    
    </td>
    <td valign="top">
    
    Identity Directory
    
    </td>
    <td valign="top">
    
    `Global User ID` 
    
    </td>
    </tr>
    </table>
    
    For more information, see [User Attributes](https://help.sap.com/docs/identity-authentication/identity-authentication/user-attributes?version=Cloud) in the documentation of SAP Cloud Identity Services.


The subject name identifier attribute is used by SAP BTP to uniquely identify the application user.

For more information, see [Configure the Subject Name Identifier Sent to the Application](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/1d020e3a3ba34c43a71fde70bfa6419a.html) in the documentation of SAP Cloud Identity Services.



<a name="loiobbb4a8a1eae04843967a8a629dcb30f9__section_wdh_bwq_qsc"/>

## Default Configuration of ID Tokens

In the default configuration, the attributes provided in the ID token issued by SAP Cloud Identity Services are described in the following table.

**Default Attributes of SAP Cloud Identity Services Tokens**


<table>
<tr>
<th valign="top">

User Attribute of SAP Cloud Identity Services

</th>
<th valign="top">

Assertion Attribute

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`mail` 

</td>
<td valign="top">

`email` 

</td>
<td valign="top">

E-mail address of the subject. By default, this value is used for the subject name identifier.

See the table *Default Configurations of the Subaccount in SAP Cloud Identity Services* following this table.

</td>
</tr>
<tr>
<td valign="top">

`mailVerified` 

</td>
<td valign="top">

`email_verified` 

</td>
<td valign="top">

Indicates whether the subject has confirmed their e-mail address. Your identity provider might require users to verify their e-mail address.

</td>
</tr>
<tr>
<td valign="top">

`lastName` 

</td>
<td valign="top">

`family_name` 

</td>
<td valign="top">

Last name of the subject.

</td>
</tr>
<tr>
<td valign="top">

`firstName` 

</td>
<td valign="top">

`given_name` 

</td>
<td valign="top">

First name of the subject.

</td>
</tr>
<tr>
<td valign="top">

`companyGroups` 

</td>
<td valign="top">

`groups` 

</td>
<td valign="top">

Any groups the subject is assigned to in the identity provider.

</td>
</tr>
<tr>
<td valign="top">

`userUuid` 

</td>
<td valign="top">

`user_uuid` 

</td>
<td valign="top">

An identifier for a user that’s unique across technology layers such as user interface, APIs, and security tokens, as well as across products and lines of businesses contributing to a business process in the Intelligent Enterprise.

Business applications can use this identifier to correlate information about the user. While not necessary for platform users, the attribute doesn't hinder such users either.

> ### Note:  
> SAP Authorization and Trust Management service supports global user identifiers. When SAP Cloud Identity Services sends a global user identifier, it's included in the SAP Authorization and Trust Management service tokens, which means that you can use it in scenarios where you need to use global user identifiers.
> 
> For more information, see [Global User ID in Integration Scenarios](https://help.sap.com/docs/cloud-identity/system-integration-guide/global-user-id-in-integration-scenarios?version=Cloud).



</td>
</tr>
</table>



<a name="loiobbb4a8a1eae04843967a8a629dcb30f9__section_qt5_pwq_qsb"/>

## Default Configuration of the SAP Cloud Identity Services Application

In the application of SAP Cloud Identity Services that represents the subaccount, the configuration sets defaults as shown in the following table.

**Default Configurations of the Subaccount in SAP Cloud Identity Services**


<table>
<tr>
<th valign="top">

Configuration

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Subject name identifier

</td>
<td valign="top">

This attribute is used to by the SAP Authorization and Trust Management service to identify the user for authentication.

Default value: ***E-Mail***.

For more information, see [Configure the Subject Name Identifier Sent to the Application](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/1d020e3a3ba34c43a71fde70bfa6419a.html) in the documentation of SAP Cloud Identity Services.

</td>
</tr>
<tr>
<td valign="top">

List of allowed redirect URIs

</td>
<td valign="top">

The list of URIs to which SAP Cloud Identity Services is allowed to redirect from the application that represents your subaccount.

Default value: <code>https://<i class="varname">&lt;subdomain&gt;</i>.authentication.<i class="varname">&lt;landscape&gt;</i>/login/callback/<i class="varname">&lt;origin&gt;</i></code>.

For example: `https://mysubdomain.authentication.us10.hana.ondemand.com/login.callback/sap.custom`

For more information, see [OpenID Connect Application Configurations](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/1ae324ee3b2d4a728650eb022d5fd910.html) in the documentation of SAP Cloud Identity Services.

</td>
</tr>
<tr>
<td valign="top">

Post logout redirect URIs

</td>
<td valign="top">

The list of URIs to which SAP Cloud Identity Services is allowed to direct users when logging out.

Default value: <code>https://<i class="varname">&lt;subdomain&gt;</i>.authentication.<i class="varname">&lt;landscape&gt;</i>/*</code>.

For example: `https://mysubdomain.authentication.us10.hana.ondemand.com/*`

For more information, see [OpenID Connect Application Configurations](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/1ae324ee3b2d4a728650eb022d5fd910.html) in the documentation of SAP Cloud Identity Services.

</td>
</tr>
</table>

**Related Information**  


[Establish Trust and Federation Between SAP Authorization and Trust Management Service and SAP Cloud Identity Services](establish-trust-and-federation-between-sap-authorization-and-trust-management-service-a-161f8f0.md "Use your SAP Cloud Identity Services tenant as an identity provider or a proxy to your own identity provider hosting your business users. This method avoids the upload and download of SAML meta data by using OpenID Connect (OIDC) to establish trust.")

