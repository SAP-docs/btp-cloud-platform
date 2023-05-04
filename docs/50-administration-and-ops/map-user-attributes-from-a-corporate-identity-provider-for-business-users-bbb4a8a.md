<!-- loiobbb4a8a1eae04843967a8a629dcb30f9 -->

# Map User Attributes from a Corporate Identity Provider for Business Users

When you enable trust with a tenant of SAP Cloud Identity Services - Identity Authentication, you get an OpenID Connect \(OIDC\) application in Identity Authentication to represent your subaccount, in the context of business users. When Identity Authentication authenticates users using a corporate identity provider, map the user attributes provided by the corporate identity provider to the attributes required by your applications.



<a name="loiobbb4a8a1eae04843967a8a629dcb30f9__section_yv2_3cr_qsb"/>

## Finding the Application for Your Subaccount

The name of the application in the administration console of Identity Authentication that represents you subaccount has the prefix ***XSUAA\_*** and the display name of your subaccount.

If your subaccount is named ***My Subaccount***, the resulting application in Identity Authentication is ***XSUAA\_My Subaccount***.



<a name="loiobbb4a8a1eae04843967a8a629dcb30f9__section_wdh_bwq_qsb"/>

## Customizing Attribute Mappings

There are several options to customize attribute mappings in Identity Authentication, depending on whether identity federation is enabled or disabled.

For more information about identity federation, see [Configure Identity Federation](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/c029bbbaefbf4350af15115396ba14e2.html?version=Cloud).

-   When identity federation is disabled, Identity Authentication always propagates all the attributes received from the corporate identity provider to all the applications, on a 1:1 basis. You have the following options:
    -   Configure the corporate identity provider to directly send the attributes.

    -   If needed, use **enriched token claims** or **enriched assertion attributes** \(depending on whether the corporate identity provider is connected with SAML or OIDC\) to map the attributes sent by the corporate identity provider, to the attribute names needed by SAP BTP.

        **[Enriched token claims](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/f19e580088e74aaa96087f1def8972cd.html?version=Cloud)** or **[enriched assertion attributes](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/7124201682434efb946e1046fde06afe.html?version=Cloud&q=Enriched%20assertion%20attributes)** add additional attributes, either based on the corporate identity provider attributes \(for example, by renaming them\) or on static values.


-   When identity federation is enabled, Identity Authentication doesn't automatically propagate any attributes from the corporate identity provider to the application. This option requires mappings in the Identity Authentication application, for each attribute that is needed by the application.

    Use the *Default Attributes* in the Identity Authentication application representing your subaccount.

    SAP BTP expects the following attributes:


    <table>
    <tr>
    <th valign="top">

    Attribute


    
    </th>
    <th valign="top">

    Corporate Identity Provier


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    `email`


    
    </td>
    <td valign="top">

    `${corporateIdP.email}`


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    `email_verified`


    
    </td>
    <td valign="top">

    `${corporateIdP.email_verified}`


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    `family_name`


    
    </td>
    <td valign="top">

    `${corporateIdP.family_name}`


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    `given_name`


    
    </td>
    <td valign="top">

    `${corporateIdP.given_name}`


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    `groups`


    
    </td>
    <td valign="top">

    `${corporateIdP.groups}`


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    `user_uuid`


    
    </td>
    <td valign="top">

    `${corporateIdP.user_uuid}`


    
    </td>
    </tr>
    </table>
    
    If the corporate identity provider sends user attributes with other names, map the attribute for the corporate identity provider to the right attribute name.

    > ### Example:  
    > If your corporate identity provider sends users' last names as attribute `sn`, map the `sn` attribute to the `family_name` attribute required by your application with the value ***$\{corporateIdP.sn\}***.

       
      
    **Default Attribute Configuration in Identity Authentication**

     ![](images/Default_attributes_for_corporate_IdP_b33e732.png "Default Attribute Configuration in Identity
                                    Authentication") 

    For more information, see [Configure the Default Attributes Sent to the Application](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/a2f1e4692e7d4379ab82144ab309e7b3.html?version=Cloud&q=corporateidp).


The following table provides the information needed for mapping the attributes, independently from where you do this in Identity Authentication.

The subject name identifier attribute is used by SAP BTP to uniquely identify the application user.

For more information, see [Configure the Subject Name Identifier Sent to the Application](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/1d020e3a3ba34c43a71fde70bfa6419a.html) in the documentation of Identity Authentication.

**Attribute Mapping in Identity Authentication Tokens**


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

This attribute is the user identifier for the application.

Default value: ***User ID***



</td>
</tr>
<tr>
<td valign="top">

 `mail` 



</td>
<td valign="top">

E-mail address of the user.



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
</table>



<a name="loiobbb4a8a1eae04843967a8a629dcb30f9__section_wdh_bwq_qsc"/>

## Default Configuration of ID Tokens

In the default configuration, the attributes provided in the ID token issued by Identity Authentication are described in the following table.

**Default Attributes of Identity Authentication Tokens**


<table>
<tr>
<th valign="top">

Identity Authentication User Attribute



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

See the table *Default Configurations of the Subaccount in Identity Authentication* following this table.



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

Indicates whether the subject has confirmed their e-mail address. Your identity provider mgiht requires users to verify their e-mail address.



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

An identifier for a user that is unique across technology layers such as user interface, APIs, and security tokens, as well as across products and lines of businesses contributing to a business process in the Intelligent Enterprise.

Business applications can use this identifier to correlate information about the user. While not necessary for platform users, the attribute doesn't hinder such users either.



</td>
</tr>
</table>



<a name="loiobbb4a8a1eae04843967a8a629dcb30f9__section_qt5_pwq_qsb"/>

## Default Configuration the Identity Authentication Application

In the application of Identity Authentication that represents the subaccount, the configuration sets defaults as shown in the following table.

**Default Configurations of the Subaccount in Identity Authentication**


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

This attribute is used to by SAP Authorization and Trust Management service to identify the user for authentication.

Default value: ***E-Mail***.

For more information, see [Configure the Subject Name Identifier Sent to the Application](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/1d020e3a3ba34c43a71fde70bfa6419a.html) in the documentation of Identity Authentication.



</td>
</tr>
<tr>
<td valign="top">

List of allowed redirect URIs



</td>
<td valign="top">

The list of URIs to which Identity Authentication is allowed to redirect from the application that represents your subaccount.

Default value: <code>https://<i class="varname">&lt;subdomain&gt;</i>.authentication.<i class="varname">&lt;landscape&gt;</i>/login/callback/<i class="varname">&lt;origin&gt;</i></code>.

For example: `https://mysubdomain.authentication.us10.hana.ondemand.com/login.callback/sap.custom`.

For more information, see [OpenID Connect Application Configurations](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/1ae324ee3b2d4a728650eb022d5fd910.html) in the documentation of Identity Authentication.



</td>
</tr>
<tr>
<td valign="top">

Post logout redirect URIs



</td>
<td valign="top">

The list of URIs to which Identity Authentication is allowed to direct users when logging out.

Default value: <code>https://<i class="varname">&lt;subdomain&gt;</i>.authentication.<i class="varname">&lt;landscape&gt;</i>/*</code>.

For example: `https://mysubdomain.authentication.us10.hana.ondemand.com/*`.

For more information, see [OpenID Connect Application Configurations](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/1ae324ee3b2d4a728650eb022d5fd910.html) in the documentation of Identity Authentication.



</td>
</tr>
</table>

**Related Information**  


[Establish Trust and Federation Between UAA and Identity Authentication](establish-trust-and-federation-between-uaa-and-identity-authentication-161f8f0.md "Use your SAP Cloud Identity Services - Identity Authentication tenant as an identity provider or a proxy to your own identity provider hosting your business users. This method avoids the upload and download of SAML meta data by using Open ID Connect (OIDC) to establish trust.")

[Establish Trust and Federation of Custom Identity Providers for Platform Users in Multi-Environment Subaccounts \[Feature Set A\]](establish-trust-and-federation-of-custom-identity-providers-for-platform-users-in-multi-8600afb.md "By default, platform users in multi-environment subaccounts are users in SAP ID service. The use of your own identity provider requires integration between the user bases of multi-environment and Neo subaccounts.")

