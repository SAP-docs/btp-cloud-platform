<!-- loio0b947d490dd540aab009d9eac4b83885 -->

# Safely Switching to Another Identity Provider

Safely move a trust configuration to another identity provider without losing user data, such as authorizations or user-related data in applications. It's possible for OIDC and SAML trust configurations.

> ### Note:  
> For such a consolidation, it's not a good idea to delete your old trust configuration and then create a new identity provider. When you delete a trust configuration, you lose all role collection assignments and the shadow users in SAP BTP. User-related data in applications and services might be affected as well.

> ### Remember:  
> This change requires planned downtime. Reconfigure the trust in SAP BTP and SAP Cloud Identity Services so that SAP BTP receives exactly the same user data as before. Some time is needed before sign-in is available again.

> ### Recommendation:  
> Practice this procedure in your development or test subaccounts before carrying it out in your productive subaccounts.

As a subaccount administrator, you want to consolidate your landscape. You want to use a different identity provider than the one you used so far. Be aware that data provided by identity providers and key data of trust configurations are used to store user-related data, so you want to ensure that this change doesn't impact any user data. To avoid any impact, safely update your trust configuration and switch to another identity provider.

We offer solutions for changing the trust configuration of the SAP Cloud Identity Services tenant and of a corporate identity provider.

-   Change the SAP Cloud Identity Services tenant by editing your trust configuration.

    1.  \(For SAML trust configurations\) Migrate the SAML trust configuration to OIDC \(see [Migration from SAML Trust to OpenID Connect Trust with SAP Cloud Identity Services](migration-from-saml-trust-to-openid-connect-trust-with-sap-cloud-identity-services-d097ce2.md)\).
    2.  To change the SAP Cloud Identity Services tenant of your trust configuration, go to the custom trust configuration for applications that you want to switch to another identity provider.

    3.  Select the trust configuration.

    4.  Choose the *Edit* button.

    5.  Select the new SAP Cloud Identity Services tenant in the field *SAP Cloud Identity Tenant*.

        > ### Caution:  
        > The origin, user names, and shadow user IDs remain the same. Make sure you keep the same authentication settings, subject identifier, and user attributes.

    6.  With the new tenant, the cockpit automatically suggests you a domain of the new tenant. Check the domain and adapt it if required.

    7.  Save your changes.

        > ### Caution:  
        > The origin, user names, and shadow user IDs remain the same. Make sure you keep the same subject identifier and user attributes.

    8.  Sign in to the administration console of SAP Cloud Identity Services.

    9.  Choose the corresponding application in the new SAP Cloud Identity Services tenant. After you updated the trust configuration in SAP BTP, the newly created application has the default settings.

    10. Customize the application settings as required. Take care that SAP BTP receives exactly the same user data as from the original identity provider, such as the same subject name ID and user attributes.


-   In rare cases, your trust configuration remains a SAML trust. Update the metadata of the existing trust configuration with the data of the new SAP Cloud Identity Services tenant. Take care that SAP BTP receives exactly the same user data as from the original identity provider, such as the same subject name ID and user attributes.


