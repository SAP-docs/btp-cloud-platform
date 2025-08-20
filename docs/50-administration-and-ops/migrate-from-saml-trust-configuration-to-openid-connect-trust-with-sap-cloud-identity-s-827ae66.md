<!-- loio827ae664cf5448b1a2fa993a8372aafc -->

# Migrate from SAML Trust Configuration to OpenID Connect Trust with SAP Cloud Identity Services

If your subaccount uses the SAML protocol to connect to your custom identity provider, you can't consume applications or application features that require direct authentication with SAP Cloud Identity Services, such as SAP Build Work Zone and SAP Build Apps. To consume such applications or features, switch to using OpenID Connect \(OIDC\) with SAP Cloud Identity Services.



<a name="loio827ae664cf5448b1a2fa993a8372aafc__prereq_znq_pz3_dxb"/>

## Prerequisites

-   The prerequisites for working with the SAP BTP command line interface \(CLI\) are fulfilled \(see [Log in](log-in-e241b30.md)\).

-   In the SAP BTP cockpit under *Custom Identity Provider for Applications*, there are no trust configurations with the OpenID Connect protocol and no more than one with SAML trust configuration that is used for interactive user login \(*Available for User Logon*\); namely the configuration that you want to migrate.

    > ### Note:  
    > SAML trust configurations that are used for principal propagation from other applications are not relevant and can remain unchanged.

    For more information, see [Migration from SAML Trust to OpenID Connect Trust with SAP Cloud Identity Services](migration-from-saml-trust-to-openid-connect-trust-with-sap-cloud-identity-services-d097ce2.md).




## Procedure

1.  Find the origin key of the identity provider that you want to switch.

    You can look up the origin key in the trust configuration in the SAP BTP cockpit using the btp CLI, or the Identity Provider Management API.

      
      
    **Finding the Origin Key in the Cockpit**

    ![](images/Show_Origin_Key_in_cockpit_7e03dc2.png "Finding the Origin Key in the Cockpit")

2.  To migrate the trust configuration from SAML to OIDC, use the SAP BTP command line interface \(CLI\).

    For more information, see [Managing Trust from SAP BTP to an SAP Cloud Identity Services Tenant](managing-trust-from-sap-btp-to-an-sap-cloud-identity-services-tenant-6140107.md).

3.  Log on to the btp CLI \(see [Log in](log-in-e241b30.md)\).

4.  Make sure that you set the target to the relevant SAP BTP subaccount.

5.  Find the name of the SAP Cloud Identity Services tenant you want to migrate to OpenID Connect. Use the following command:

    `btp list security/available-idp`

    You receive a list of all SAP Cloud Identity Services tenants that are available in this subaccount. It's a good idea to copy the name of the SAP Cloud Identity Services tenant that you want to migrate.

6.  Migrate your trust configuration using the following command:

    `btp migrate security/trust ORIGIN --idp TENANT`

    > ### Example:  
    > `btp migrate security/trust my-origin-key --idp myidp.accounts.ondemand.com`

    The btp CLI returns that the trust configuration is active and that the protocol is OIDC.

7.  Check that your SAML trust configuration was migrated to a trust configuration with the OpenID Connect protocol. Go to your subaccount in the SAP BTP cockpit and choose *Security* \> *Trust Configuration*.




<a name="loio827ae664cf5448b1a2fa993a8372aafc__result_ktm_pfj_dxb"/>

## Results

In the cockpit, there's a new OIDC trust configuration for your SAP Cloud Identity Services tenant. The original SAML trust configuration has been set to inactive and has received a new ***oidc-migration-backup*** origin key. If you need to roll back the change, the service uses this configuration to restore your original configuration.

In your SAP Cloud Identity Services tenant, there's a new application that represents the trust configuration. The name is ***SAP BTP subaccount *<subaccount\_display\_name\>****.



<a name="loio827ae664cf5448b1a2fa993a8372aafc__postreq_dpv_pfj_dxb"/>

## Next Steps

Configure your new SAP Cloud Identity Services application to match your old configuration. Check that your users can log on with all the required attributes. If necessary, configure your new application to consume your corporate identity provider.

> ### Note:  
> If everything works, you can delete the original SAML trust configuration. If you do so, you can't restore it.

**Related Information**  


[Configuration of SAP Cloud Identity Services After Migration from SAML to OIDC](configuration-of-sap-cloud-identity-services-after-migration-from-saml-to-oidc-1fa7273.md "You replaced an SAML trust configuration to your custom identity provider with an OIDC trust configuration to SAP Cloud Identity Services. Now, you need to make sure that the subaccount gets the same user attributes (names and values) as before.")

[Restore SAML Trust Configuration](restore-saml-trust-configuration-21d86cf.md "You replaced a SAML trust configuration to your custom identity provider with an OpenID Connect (OIDC) trust configuration to SAP Cloud Identity Services, and the authentication of application users in the subaccount isn't working as you expected. Restore your SAML configuration to get your applications working again.")

