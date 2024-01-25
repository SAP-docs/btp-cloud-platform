<!-- loio8c37725a2b964d87987c385d125c5bdd -->

# Identity Authentication Without Corporate Identity Provider

You've only changed the protocol of the trust configuration between your SAP Business Technology Platform subaccount and Identity Authentication.

Copy the following configurations from the old SAML-based Identity Authentication application to your new OIDC-based Identity Authentication application:

-   Subject name identifier

    See [Configure the Subject Name Identifier Sent to the Application](http://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/1d020e3a3ba34c43a71fde70bfa6419a.html) in the documentation of Identity Authentication.

-   Attributes

    Change the names of the following attributes as listed in the following table.


    <table>
    <tr>
    <th valign="top">

    From User Attribute
    
    </th>
    <th valign="top">

    To User Attribute
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    first\_name
    
    </td>
    <td valign="top">
    
    given\_name
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    last\_name
    
    </td>
    <td valign="top">
    
    family\_name
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    mail
    
    </td>
    <td valign="top">
    
    email
    
    </td>
    </tr>
    </table>
    
    See [Configuring User Attributes from the Identity Directory](https://help.sap.com/docs/identity-authentication/identity-authentication/configure-user-attributes-sent-to-application?version=Cloud).


**Related Information**  


[Configuration of Identity Authentication After Migration from SAML to OIDC](configuration-of-identity-authentication-after-migration-from-saml-to-oidc-1fa7273.md "You replaced an SAML trust configuration to your custom identity provider with an OIDC trust configuration to Identity Authentication. Now, you need to make sure that the subaccount gets the same user attributes (names and values) as before.")

[Test the Trust Configuration After the Migration](test-the-trust-configuration-after-the-migration-edc7c42.md "Check that your users can still access their applications and have all the attributes they require. Use these steps to validate your new configuration.")

