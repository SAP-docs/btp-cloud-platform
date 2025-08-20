<!-- loio269f60d804bd499d821312cd1ad3ff0b -->

# Prepare for Migration from SAML Trust to OpenID Connect

Before migrating your trust configuration, check which user data are sent today, so you can validate the new configuration after the migration. If you use a corporate identity provider, prepare the trust between your SAP Cloud Identity Services tenant and your corporate identity provider ahead of time.



<a name="loio269f60d804bd499d821312cd1ad3ff0b__steps_yvg_gsz_gxb"/>

## Procedure

1.  Check what attributes your users have.

    To see what attributes your user has, open the following page of your subaccount:

    <code>https://<i class="varname">&lt;subaccount_subdomain&gt;</i>.authentication.<i class="varname">&lt;region&gt;</i>.hana.ondemand.com/config?action=who&amp;details=true&amp;trustMigrationOnly=true</code>

    For example

    `https://my-subdomain.authentication.eu10.hana.ondemand.com/config?action=who&details=true&trustMigrationOnly=true`

    If at logon you see multiple identity providers, choose the one you want to migrate from for your applications.

    > ### Remember:  
    > Save the results. You'll need to compare the attributes with the attributes you get after migrating the trust configuration.
    > 
    > For an example, see [Test the Trust Configuration After the Migration](test-the-trust-configuration-after-the-migration-edc7c42.md).

2.  Determine if you need to establish trust between your corporate identity provider and your SAP Cloud Identity Services tenant.

    If you previously had configured your subaccount trust to your corporate identity provider directly, configure your SAP Cloud Identity Services tenant to trust your corporate identity provider.

      
      
    **Insertion of SAP Cloud Identity Services in Trust Chain of Identity Providers**

    ![](images/Injection_of_IAS_Between_Corp_IDP_db96a95.png "Insertion of SAP Cloud Identity Services in Trust Chain of Identity
    							Providers")

    In the preceding figure, we're configuring the SAML or OIDC trust between the SAP Cloud Identity Services tenant and the corporate identity provider. Configure the corporate identity provider to send the same value for subject name identifier and the attributes. Keep the attribute names the same, too, except for the attribute names listed in the following table.


    <table>
    <tr>
    <th valign="top">

    From User Attribute
    
    </th>
    <th valign="top">

    To Assertion Attribute
    
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
    
    For more information, see [Corporate Identity Providers](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/19f3eca47db643b6aad448b5dc1075ad.html) in the documentation of SAP Cloud Identity Services.


