<!-- loio036126cc79f54ec0ab7bfbf3b24b5fbc -->

# Identity Authentication with Corporate Identity Provider

You want to insert your Identity Authentication tenant in the user authentication flow between your SAP BTP subaccount and your corporate identity provider. So far, you've migrated the trust configuration from your subaccount to use Identity Authentication. Now, you configure Identity Authentication to delegate user authentication to the corporate identity provider.

We already asked you to configure trust between your Identity Authentication tenant and your corporate identity provider is this step: [Prepare for Migration from SAML Trust to OpenID Connect](prepare-for-migration-from-saml-trust-to-openid-connect-269f60d.md).

How you configure the connection depends on whether you're using identity federation or not. Identity federation is a configuration of Identity Authentication. If you haven't connected Identity Authentication to the corporate identity provider yet, use the disabled approach. If your Identity Authentication tenant already trusts your corporate provider, then choose the approach that fits to the existing trust configuration.

For more information about identity federation, see [Configure Identity Federation](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/c029bbbaefbf4350af15115396ba14e2.html) in the documentation of Identity Authentication.

-   Identity federation is disabled \(default option\)

    See [Choose Default Identity Provider for an Application](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/e9d82742d42b4f769c2d0f16d8e9ee41.html) in the documentation of Identity Authentication.

-   Identity federation is enabled \(advanced\)

    See [Configure Conditional Authentication for an Application](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/0143dce88a604533ab5ab17e639fec09.html)in the documentation of Identity Authentication.




## Identity Federation Is Disabled

As you were preparing for this migration, you saw what subject and attributes you need for your users.

For more information, see [Prepare for Migration from SAML Trust to OpenID Connect](prepare-for-migration-from-saml-trust-to-openid-connect-269f60d.md).

Attributes are passed to SAP BTP just as they're received from the corporate identity provider. Subject and attribute configurations on the Identity Authentication application are ignored. The subject **must** be provided by the corporate identity provider as required. Attributes **ideally** come from the corporate identity provider with the attribute names used by the subaccount so far.

Compare the attributes you got before the migration to the attributes you get now.

For more information, see [Test the Trust Configuration After the Migration](test-the-trust-configuration-after-the-migration-edc7c42.md).

If the assertion attributes don't come from the corporate identity provider as you expected, change the names of the following assertion attributes as listed in the following table.


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

Map the attribute names between what the corporate identity provider provides and what the subaccount expects, according to the protocol of the trust configuration:

-   For OIDC: See [Enrich Token Claims Coming from Corporate IdP](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/f19e580088e74aaa96087f1def8972cd.html) in the documentation of Identity Authentication.

-   For SAML: [Enrich Assertion Attributes Coming from Corporate IdP](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/7124201682434efb946e1046fde06afe.html) in the documentation of Identity Authentication.




<a name="loio036126cc79f54ec0ab7bfbf3b24b5fbc__section_kjm_hh4_hxb"/>

## Identity Federation Is Enabled

As you were preparing for this migration, you saw what subject and attributes you need for your users.

For more information, see [Prepare for Migration from SAML Trust to OpenID Connect](prepare-for-migration-from-saml-trust-to-openid-connect-269f60d.md).

Configure your new OIDC-based Identity Authentication application to send the same information to your SAP BTP subaccount as before.

-   Subject name identifier

    See [Configure the Subject Name Identifier Sent to the Application](http://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/1d020e3a3ba34c43a71fde70bfa6419a.html) in the documentation of Identity Authentication.

-   Assertion attributes

    > ### Recommendation:  
    > Change the names of the following assertion attributes as listed in the following table.
    > 
    > 
    > <table>
    > <tr>
    > <th valign="top">
    > 
    > From User Attribute
    > 
    > </th>
    > <th valign="top">
    > 
    > To User Attribute
    > 
    > </th>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > first\_name
    > 
    > </td>
    > <td valign="top">
    > 
    > given\_name
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > last\_name
    > 
    > </td>
    > <td valign="top">
    > 
    > family\_name
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > mail
    > 
    > </td>
    > <td valign="top">
    > 
    > email
    > 
    > </td>
    > </tr>
    > </table>

    See [Configuring User Attributes from a Corporate Identity Provider](https://help.sap.com/docs/identity-authentication/identity-authentication/configure-default-attributes-for-subscribed-applications?version=Cloud) in the documentation of Identity Authentication.


Compare the attributes you got before the migration to the attributes you get now.

For more information, see [Test the Trust Configuration After the Migration](test-the-trust-configuration-after-the-migration-edc7c42.md).

