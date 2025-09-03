<!-- loio161f8f0cfac64c4fa2d973bc5f08a894 -->

# Establish Trust and Federation Between SAP Authorization and Trust Management Service and SAP Cloud Identity Services

Use your SAP Cloud Identity Services tenant as an identity provider or a proxy to your own identity provider hosting your business users. This method avoids the upload and download of SAML meta data by using OpenID Connect \(OIDC\) to establish trust.



<a name="loio161f8f0cfac64c4fa2d973bc5f08a894__prereq_dvg_xgj_p1b"/>

## Prerequisites

-   You have subaccount administrator permissions.

-   You have a tenant of SAP Cloud Identity Services.

    For more information, see [Get Your Tenant](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/get-your-tenant?version=Cloud) in the documentation for SAP Cloud Identity Services.

-   The SAP Cloud Identity Services tenant is associated with the customer IDs of the relevant global account of SAP BTP.

    For more information, see [Reuse SAP Cloud Identity Services Tenants for Different Customer IDs](https://help.sap.com/docs/identity-authentication/identity-authentication/reuse-sap-cloud-identity-services-tenants-for-different-customer-ids) in the documentation for SAP Cloud Identity Services.




<a name="loio161f8f0cfac64c4fa2d973bc5f08a894__context_tzl_st2_tmb"/>

## Context

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

Consider the following restrictions and tips before you start.

> ### Restriction:  
> -   You can only establish trust with a single tenant of SAP Cloud Identity Services per subaccount using this method.
> 
> -   Your SAP Cloud Identity Services tenant can be changed only when no SAP Cloud Identity Services-based subscriptions \(for example, SAP Build Work Zone using authentication with SAP Cloud Identity Services, SAP Build Apps, or SAP Integration Suite, advanced event mesh\) exist.
> 
> -   If you have an SAML trust configuration for a certain tenant already, you can't add an OIDC trust configuration to the same tenant in addition. Instead, migrate the SAML trust configuration to OIDC \(see [Migration from SAML Trust to OpenID Connect Trust with SAP Cloud Identity Services](migration-from-saml-trust-to-openid-connect-trust-with-sap-cloud-identity-services-d097ce2.md)\).
> 
>     Consider the upper limits for trust configurations in the subaccount. See [Limits for the Subaccount](../60-security/limits-for-technical-artifacts-of-the-sap-authorization-and-trust-management-service-6d3ef52.md#loio6d3ef5260f4a4232ad43542ab1441694__section_ddk_bhf_fzb).

> ### Tip:  
> -   We recommend that you use SAP Cloud Identity Services as identity provider and connect a potential corporate identity provider there. If you don't have a tenant yet, check [Getting a Tenant](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/93160ebd2dcb40e98aadcbb9a970f2b9.html#getting-a-tenant).
> 
>     For more information, see [Corporate Identity Providers](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/19f3eca47db643b6aad448b5dc1075ad.html) and [Configure Conditional Authentication for an Application](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/0143dce88a604533ab5ab17e639fec09.html) in [What Is Identity Authentication](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/27882717f44b445fa287936c6f43dc1f.html) and [SAP Cloud Identity Services](https://help.sap.com/viewer/product/IDENTITY_AUTHENTICATION/Cloud/en-US)
> 
> -   We provide APIs so you can perform this procedure programmatically. For more information, see the [Identity Provider Management API](https://api.sap.com/api/TrustConfigurationAPI/resource) on [SAP Business Accelerator Hub](https://api.sap.com/package/authtrustmgmnt/rest).



<a name="loio161f8f0cfac64c4fa2d973bc5f08a894__steps_a2x_wfg_wmb"/>

## Procedure

1.  In the SAP BTP cockpit, go to your subaccount\(see [Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md)\) and choose *Security* \> *Trust Configuration*.

2.  Choose *Establish Trust*.

    The *Configure Tenant* wizard opens.

3.  Choose the SAP Cloud Identity Services tenant and choose *Next*.

    The identity providers listed are the SAP Cloud Identity Services tenants associated with your customer ID.

    For more information, see the preceding prerequisites.

4.  Choose the domain configured with the SAP Cloud Identity Services tenant and continue with *Next*.

5.  You can change the name and the description of the tenant, display and change the origin key.

    The origin key can have 36 characters at maximum. Only use the following characters for the origin key of the trust configuration.

    `aA`–`zZ`, `0`–`9`, `-` \(hyphen\), `_` \(underscore\)

6.  Provide a link text for user logon \(see [Using Multiple Identity Providers from the Same Subaccount](using-multiple-identity-providers-from-the-same-subaccount-b8c0aac.md)\). Continue with *Next*.

7.  Review your configuration and confirm using *Finish*.




<a name="loio161f8f0cfac64c4fa2d973bc5f08a894__result_brm_352_tmb"/>

## Results

You've configured trust in your tenant of the SAP Cloud Identity Services, which is your identity provider. SAP Cloud Identity Services creates an application with the prefix *SAP BTP subaccount* and the display name of your subaccount in the administration console for SAP Cloud Identity Services. Some attributes of the application are managed by SAP, such as the application type, and are read-only.

> ### Example:  
> If your subaccount is named *My Subaccount*, the resulting application in SAP Cloud Identity Services would be *SAP BTP subaccount My Subaccount*.
> 
> Older applications start with *XSUAA\_*.

> ### Tip:  
> To troubleshoot problems with tokens from SAP Cloud Identity Services, see [Logging OpenID Connect Tokens](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/b6c42b53518b46de8b4dffd8c4c52ed7.html?version=Cloud) in the documentation for SAP Cloud Identity Services.

> ### Restriction:  
> If the OIDC issuer is changed in the trust configuration, the trust breaks. To update the trust configuration on the SAP BTP side, open the details of the trust configuration and choose *Refresh*. This button refreshes the trust configuration to reflect changes in the SAP Cloud Identity Services tenant, for example the issuer value.



<a name="loio161f8f0cfac64c4fa2d973bc5f08a894__postreq_z32_k52_tmb"/>

## Next Steps

If you don't need the default identity provider anymore, set it to inactive or hide the logon link.

**Related Information**  


[Default Identity Provider](default-identity-provider-d6a8db7.md "SAP ID service is the default identity provider for both platform users and business users (in applications) at SAP BTP. You can start using it without further configuration.")

