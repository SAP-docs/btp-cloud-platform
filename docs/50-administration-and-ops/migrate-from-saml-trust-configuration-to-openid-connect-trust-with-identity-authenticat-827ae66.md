<!-- loio827ae664cf5448b1a2fa993a8372aafc -->

# Migrate from SAML Trust Configuration to OpenID Connect Trust with Identity Authentication

If your subaccount uses the SAML protocol to connect to your custom identity provider, you can't consume applications or application features that require direct authentication with Identity Authentication, such as SAP Build Work Zone and SAP Build Apps. To consume such applications or features, switch to using OpenID Connect \(OIDC\) with Identity Authentication.



<a name="loio827ae664cf5448b1a2fa993a8372aafc__prereq_znq_pz3_dxb"/>

## Prerequisites

-   You've enabled API access to the SAP Authorization and Trust Management service.

    For more information, see [Access SAP Authorization and Trust Management Service APIs](access-sap-authorization-and-trust-management-service-apis-ebc9113.md).

-   In the SAP BTP cockpit under *Custom Identity Provider for Applications*, there are no trust configurations with protocol OpenID Connect and no more than one with SAML; namely the configuration you want to migrate.

    For more information, see [Migration from SAML Trust to OpenID Connect Trust with Identity Authentication](migration-from-saml-trust-to-openid-connect-trust-with-identity-authentication-d097ce2.md).




## Procedure

1.  Find the origin key of the identity provider you want to switch.

    You can look up the origin key in the trust configuration in the SAP BTP cockpit, with the BTP command-line interface, or the Identity Provider Management API.

       
      
    **Finding the Origin Key in the Cockpit**

     ![](images/Show_Origin_Key_in_cockpit_7e03dc2.png "Finding the Origin Key in the Cockpit") 

2.  Migrate the protocol of the trust configuration from SAML to OIDC.

    Call the *PUT* method of the Identity Provider Management API at the following endpoint, including the origin key of the SAML trust configuration:

    <code>https://api.authentication.<i class="varname">&lt;region&gt;</i>.hana.ondemand.com/sap/rest/identity-providers/migrate/<i class="varname">&lt;origin-key&gt;</i></code>

    For example:

    `https://api.authentication.eu20.hana.ondemand.com/sap/rest/identity-providers/migrate/my-origin`

    Include in JSON format in the body of the request, the protocol type `oidc1.0` as well as the hostname of your Identity Authentication tenant in the configuration properties. Optionally, you can set the domain of the Identity Authentication tenant to use for user logon with the `additionalConfiguration` key.

    ```
    {
        "type": "oidc1.0",
        "config": {
            "iasTenant": {
                "host": "ar9ibaxhm.accounts.ondemand.com"
            },
            "additionalConfiguration": {
                "domain": "login.company.com"
            }
        }
    }
    ```

    The API returns a status 200 OK and a JSON. The JSON is the OIDC trust configuration to the Identity Authentication tenant for the subaccount with the same name, origin key, and ID.




<a name="loio827ae664cf5448b1a2fa993a8372aafc__result_ktm_pfj_dxb"/>

## Results

In the cockpit, there's a new OIDC trust configuration for your Identity Authentication tenant. The original SAML trust configuration has been set to inactive and received a new origin key ***oidc-migration-backup*** and a new ID. If you must roll back the change, the service uses this configuration to restore your original configuration.

In your Identity Authentication tenant, there's a new application that represents the trust configuration. The name is ***XSUAA\_*<subaccount\_display\_name\>****.



<a name="loio827ae664cf5448b1a2fa993a8372aafc__postreq_dpv_pfj_dxb"/>

## Next Steps

Configure your new Identity Authentication application to match your old configuration. Check that your users can log on with all the required attributes. If necessary, configure your new application to consume your corporate identity provider.

**Related Information**  


[Configuration of Identity Authentication After Migration from SAML to OIDC](configuration-of-identity-authentication-after-migration-from-saml-to-oidc-1fa7273.md "You replaced an SAML trust configuration to your custom identity provider with an OIDC trust configuration to Identity Authentication. Now, you need to make sure that the subaccount gets the same user attributes (names and values) as before.")

[Restore SAML Trust Configuration](restore-saml-trust-configuration-21d86cf.md "You replaced an SAML trust configuration to your custom identity provider to OpenID Connect (OIDC) and the authentication of application users in the subaccount isn't working as you expected. Restore your SAML configuration to get your application working again.")

