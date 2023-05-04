<!-- loio21d86cf36ce94da7b2f2db8271e0b539 -->

# Restore SAML Trust Configuration

You replaced an SAML trust configuration to your custom identity provider to OpenID Connect \(OIDC\) and the authentication of application users in the subaccount isn't working as you expected. Restore your SAML configuration to get your application working again.



<a name="loio21d86cf36ce94da7b2f2db8271e0b539__prereq_znq_pz3_dxb"/>

## Prerequisites

You previously migrated your trust configuration from SAML to OIDC.

For more information, see [Migrate from SAML Trust Configuration to OpenID Connect Trust with Identity Authentication](migrate-from-saml-trust-configuration-to-openid-connect-trust-with-identity-authenticat-827ae66.md).



## Procedure

1.  Find the origin key of the OIDC trust configuration you want to restore to SAML.

    You can look up the origin key in the trust configuration in the SAP BTP cockpit, with the BTP command-line interface, or the Identity Provider Management API.

       
      
    **Finding the Origin Key in the Cockpit**

     ![](images/OIDC_Migration_Backup_68d59f6.png "Finding the Origin Key in the Cockpit") 

2.  Restore the protocol of the trust configuration from SAML to OIDC.

    Call the *PUT* method of the Identity Provider Management API at the following endpoint, including the origin key of the OIDC trust configuration:

    <code>https://api.authentication.<i class="varname">&lt;region&gt;</i>.hana.ondemand.com/sap/rest/identity-providers/migrate/<i class="varname">&lt;origin-key&gt;</i>/rollback</code>

    For example:

    `https://api.authentication.eu20.hana.ondemand.com/sap/rest/identity-providers/migrate/my-origin/rollback`

    The API returns a status 200 OK and a JSON with the original SAML identity provider configuration. The OIDC configuration has been deleted.




<a name="loio21d86cf36ce94da7b2f2db8271e0b539__result_ktm_pfj_dxb"/>

## Results

The original SAML trust configuration has been restored, with its original ID and origin key. The respective OIDC trust configuration no longer exists. In your Identity Authentication tenant, the application for the OIDC trust configuration, ***XSUAA\_*<subaccount\_display\_name\>**** has been deleted.

