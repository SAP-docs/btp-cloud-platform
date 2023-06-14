<!-- loioedc7c42084d64861beeeba9c30a7525d -->

# Test the Trust Configuration After the Migration

Check that your users can still access their applications and have all the attributes they require. Use these steps to validate your new configuration.



<a name="loioedc7c42084d64861beeeba9c30a7525d__prereq_ujt_dhn_hxb"/>

## Prerequisites

You saved the list of attributes you get before the migration.

For more information, see [Prepare for Migration from SAML Trust to OpenID Connect](prepare-for-migration-from-saml-trust-to-openid-connect-269f60d.md).



<a name="loioedc7c42084d64861beeeba9c30a7525d__steps_qdc_fhn_hxb"/>

## Procedure

1.  Check what attributes your user has now.

    <code>https://<i class="varname">&lt;subaccount_subdomain&gt;</i>.authentication.<i class="varname">&lt;region&gt;</i>.hana.ondemand.com/config?action=who&amp;details=true&amp;trustMigrationOnly=true</code>

    For example

    `https://my-subdomain.authentication.eu10.hana.ondemand.com/config?action=who&details=true&trustMigrationOnly=true`

2.  Compare with the results you had before the migration.

    In the following example, the user has a few special attributes in addition to the standard ones:

    -   Custom attribute `cost_center`

    -   Group assignment `my-group`

    -   Authorization assignment over the group to the role collection for reading audit logs



    <table>
    <tr>
    <th valign="top">

    Before \(SAML\)


    
    </th>
    <th valign="top">

    After \(OIDC\)


    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
        ```
    userName P000011
    origin my-origin-key
    zoneId 9fcd13d0-77d7-4cfa-86b0-a41b02e662a6
    User Attributes {
      user_uuid=[7ebf5c32-cacd-4ad2-a208-6bcb3e764f6f], 
      email=[maria.fontes@example.com], 
      cost_center=[my-cost-center], 
      Groups=[my-group],
      family_name=[Fontes], 
      given_name=[Maria]
      }
    email maria.fontes@example.com
    userId 128af760-ad57-4213-b063-2dd381a4d92e
    externalId P000011
    given_name Maria
    family_name Fontes
    verified true 
    authorities [
      openid, 
      user_attributes, 
      auditlog-management!b8.ReadAuditLogs, 
      uaa.user
    ]
    ```


    
    </td>
    <td valign="top">
    
        ```
    userName P000011
    origin my-origin-key
    zoneId 9fcd13d0-77d7-4cfa-86b0-a41b02e662a6
    User Attributes {
      given_name=[Maria], 
      user_uuid=[7ebf5c32-cacd-4ad2-a208-6bcb3e764f6f], 
      cost_center=[my-cost-center], 
      groups=[my-group], 
      family_name=[Fontes], 
      email=[maria.fontes@example.com]
      }
    email maria.fontes@example.com
    userId 128af760-ad57-4213-b063-2dd381a4d92e
    externalId P000011
    given_name Maria
    family_name Fontes
    verified true
    authorities [
      openid, 
      user_attributes, 
      auditlog-management!b8.ReadAuditLogs, 
      uaa.user
    ]
    ```


    
    </td>
    </tr>
    </table>
    
    > ### Note:  
    > In the new OIDC application, uppercase or lower case G in the `groups` attribute name doesn't matter.

3.  If there are any remaining differences, adjust the configuration of the Identity Authentication tenant or applications or of the corporate identity provider until you get the same attributes.

    For more information, see [Configuration of Identity Authentication After Migration from SAML to OIDC](configuration-of-identity-authentication-after-migration-from-saml-to-oidc-1fa7273.md).

    Use the OIDC token logging in Identity Authentication to help troubleshoot any problems.

    For more information, see [Logging OpenID Connect Tokens](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/b6c42b53518b46de8b4dffd8c4c52ed7.html) in the documentation of Identity Authentication.

    If you can't get the configuration to work, restore the SAML trust configuration.

    For more information, see [Restore SAML Trust Configuration](restore-saml-trust-configuration-21d86cf.md).




<a name="loioedc7c42084d64861beeeba9c30a7525d__postreq_dqr_5zj_3xb"/>

## Next Steps

Once everything is working as you expected and are certain you don't need it anymore, delete your old SAML trust configuration with the origin ***oidc-migration-backup***.

> ### Caution:  
> If you delete the old SAML trust configuration too early, you can't use the restore feature anymore.

**Related Information**  


[Restore SAML Trust Configuration](restore-saml-trust-configuration-21d86cf.md "You replaced a SAML trust configuration to your custom identity provider with an OpenID Connect (OIDC) trust configuration to Identity Authentication, and the authentication of application users in the subaccount isn't working as you expected. Restore your SAML configuration to get your applications working again.")

