<!-- loio5ab1e0b9734f4babb56073def1e1889b -->

# Third-Party Cookies and SAP Authorization and Trust Management Service

Browser manufacturers are phasing out support for third-party cookies. This change can prevent embedded BTP applications and their logon screens from functioning.

To prevent your logon scenarios from failing, make sure that all multi-environment subaccounts, which contain these embedded applications, are configured to use a tenant of SAP Cloud Identity Services as the trusted identity provider.

> ### Caution:  
> Migrate your trust before the browser vendors phase out support.
> 
> Trusting your SAP Cloud Identity Services tenant enables your applications to integrate with the overall solution provided by SAP.
> 
> For more information about the overall solution, see [SAP BTP and Third-Party Cookies Deprecation](https://community.sap.com/t5/technology-blogs-by-sap/sap-btp-and-third-party-cookies-deprecation/ba-p/13665375) and SAP Note [3409306](https://me.sap.com/notes/3409306).

To migrate an existing trust configuration, see [Migration from SAML Trust to OpenID Connect Trust with Identity Authentication](https://help.sap.com/docs/btp/sap-business-technology-platform/migration-from-saml-trust-to-openid-connect-trust-with-identity-authentication).

If your framing and framed applications run under different domains, you must still maintain trust between the domains as before. For more information, see [Configure Trusted Domains for SAP Authorization and Trust Management Service \[Feature Set B\]](https://help.sap.com/docs/btp/sap-business-technology-platform/configure-trusted-domains-for-sap-authorization-and-trust-management-service).

> ### Recommendation:  
> Test your solutions before third-party cookies have been phased out. To test how your solutions function once third-party cookies have been phased out, enable the `partitionedCookies` property of the Security Settings API of the SAP Authorization and Trust Management service and run your tests. If your business scenarios fail, set `partitionedCookies` to false to help troubleshoot the source of the problem.
> 
> For more information, see the following:
> 
> -   How to test: [Preparing and Testing Your Solution for Third-Party Cookie Phase-Out](https://help.sap.com/viewer/25b384c4cc9c472f9e056ebca95fa6ff/Cloud/en-US/70d545de1931484c9efbc2cda6519fa7.html "The focus of this guide is to identify issues related to the phase out of third-party cookies. You will learn how to test your application your extensions and assess whether they are affected. Mitigation strategies are covered in Implementing a Permanent Solution for the Third-Party Cookie Phase-Out guide.") :arrow_upper_right:
> 
> -   How to use the API: [Accessing Administration Using APIs of the SAP Authorization and Trust Management Service](https://help.sap.com/docs/btp/sap-business-technology-platform/accessing-administration-using-apis-of-sap-authorization-and-trust-management-service)
> 
> 
> In subaccounts created before May 30, 2024, the `partitionedCookies` property has a default value of ***false***. In subaccounts created afterward, the property has a default value of ***true***. When Google begins large-scale phase-out of third-party cookies, we plan to set this property to ***true*** and read-only in all subaccounts.

**Related Information**  


[Trust and Federation with Identity Providers](../50-administration-and-ops/trust-and-federation-with-identity-providers-cb1bc8f.md "When setting up accounts you need to assign users. While we provide you with your first users from the default identity provider to get you started, your organization has identity providers that you want to integrate.")

