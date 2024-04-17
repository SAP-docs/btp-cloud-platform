<!-- loio5ab1e0b9734f4babb56073def1e1889b -->

# Third-Party Cookies and SAP Authorization and Trust Management Service

Browser manufacturers are ending support for third-party cookies. This change can prevent embedded BTP applications and their logon screens from functioning.

To prevent your logon scenarios from failing, make sure that all multi-environment subaccounts, which contain these embedded applications, are configured to use a tenant of SAP Cloud Identity Services - Identity Authentication as the trusted identity provider.

> ### Caution:  
> Migrate your trust before the browser vendors deprecate support.
> 
> Trusting your Identity Authentication tenant enables your applications to integrate with the overall solution provided by SAP.
> 
> For more information about the overall solution, see [SAP BTP and Third-Party Cookies Deprecation](https://community.sap.com/t5/technology-blogs-by-sap/sap-btp-and-third-party-cookies-deprecation/ba-p/13665375) and SAP Note [3409306](https://me.sap.com/notes/3409306).

To migrate an existing trust configuration, see [Migration from SAML Trust to OpenID Connect Trust with Identity Authentication](https://help.sap.com/docs/btp/sap-business-technology-platform/migration-from-saml-trust-to-openid-connect-trust-with-identity-authentication).

If your framing and framed applications run under different domains, you must still maintain trust between the domains as before. For more information, see [Configure Trusted Domains for SAP Authorization and Trust Management Service \[Feature Set B\]](https://help.sap.com/docs/btp/sap-business-technology-platform/configure-trusted-domains-for-sap-authorization-and-trust-management-service).

**Related Information**  


[Trust and Federation with Identity Providers](../50-administration-and-ops/trust-and-federation-with-identity-providers-cb1bc8f.md "When setting up accounts you need to assign users. While we provide you with your first users to get you started, your organization has identity providers that you want to integrate.")

