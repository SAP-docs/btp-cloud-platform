<!-- loio161f8f0cfac64c4fa2d973bc5f08a894 -->

# Establish Trust and Federation Between UAA and Identity Authentication

Use your SAP Cloud Identity Services - Identity Authentication tenant as an identity provider or a proxy to your own identity provider hosting your business users. This method avoids the upload and download of SAML meta data by using Open ID Connect \(OIDC\) to establish trust.



<a name="loio161f8f0cfac64c4fa2d973bc5f08a894__prereq_dvg_xgj_p1b"/>

## Prerequisites

-   You've subaccount administrator permissionsor you are a security administrator \(cloud management tools feature set A\) of this account. For more information, see the related link.

-   You've a tenant of SAP Cloud Identity Services - Identity Authentication.

    For more information, see [Tenant Model and Licensing](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/93160ebd2dcb40e98aadcbb9a970f2b9.html#getting-a-tenant) in the documentation for Identity Authentication.

-   The Identity Authentication tenant is associated with the customer IDs of the relevant global account of SAP BTP.

    For more information, see [**Reuse SAP Cloud Identity Services Tenants for Different Customer IDs**](https://help.sap.com/docs/identity-authentication/identity-authentication/reuse-sap-cloud-identity-services-tenants-for-different-customer-ids) in the documentation for Identity Authentication.




<a name="loio161f8f0cfac64c4fa2d973bc5f08a894__context_tzl_st2_tmb"/>

## Context

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

> ### Restriction:  
> You can only establish trust with a single tenant of Identity Authentication per subaccount using this method.
> 
> Your Identity Authentication tenant can be changed only when no Identity Authentication-based subscriptions \(for example, SAP Build or SAP Integration Suite, advanced event mesh\) exist.

> ### Recommendation:  
> We recommend that you always use SAP Cloud Identity Services - Identity Authentication as single identity provider for SAP BTP. If you use corporate identity providers, connect them to your Identity Authentication tenant, which then acts as a hub. We especially recommend this if you are using multiple corporate identity providers. For platform users, the use of SAP Cloud Identity Services - Identity Authentication is mandatory.
> 
> For more information, see [Corporate Identity Providers](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/19f3eca47db643b6aad448b5dc1075ad.html) and [Configure Conditional Authentication for an Application](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/0143dce88a604533ab5ab17e639fec09.html) in [What Is Identity Authentication](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/27882717f44b445fa287936c6f43dc1f.html) and [SAP Cloud Identity Services - Identity Authentication](https://help.sap.com/viewer/product/IDENTITY_AUTHENTICATION/Cloud/en-US)

> ### Tip:  
> We provide APIs so you can perform this procedure programmatically. For more information, see the [Identity Provider Management API](https://api.sap.com/api/TrustConfigurationAPI/resource) on [SAP Business Accelerator Hub](https://api.sap.com/package/authtrustmgmnt/rest).



<a name="loio161f8f0cfac64c4fa2d973bc5f08a894__steps_a2x_wfg_wmb"/>

## Procedure

1.  In the SAP BTP cockpit, go to your subaccount\(see [Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md)\) and choose *Security* \> *Trust Configuration*.

2.  Choose *Establish Trust*.

    The *Configure Tenant* wizard opens.

3.  Choose the Identity Authentication tenant. The identity providers listed are the Identity Authentication tenants associated with your customer ID. Continue with *Next*.

4.  Choose the domain configured with the Identity Authentication tenant and continue with *Next*.

5.  You can change the name and the description of the tenant, display the resulting origin key, and enter a link text for user logon \(see [Provide Logon Link Help to Identity Provider for Business Users](provide-logon-link-help-to-identity-provider-for-business-users-b8c0aac.md)\). Continue with *Next*.

6.  Review your configuration and confirm using *Finish*.




<a name="loio161f8f0cfac64c4fa2d973bc5f08a894__result_brm_352_tmb"/>

## Results

You've configured trust in your tenant of the Identity Authentication service, which is your identity provider. Identity Authentication creates an application with the prefix *XSUAA\_* and the display name of your subaccount in the administration console for Identity Authentication.

> ### Example:  
> If your subaccount was named *My Subaccount*, the resulting application in Identity Authentication would be *XSUAA\_My Subaccount*.

> ### Tip:  
> To troubleshoot problems with tokens from Identity Authentication, see [Logging OpenID Connect Tokens](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/b6c42b53518b46de8b4dffd8c4c52ed7.html?version=Cloud) in the documentation for Identity Authentication.

> ### Restriction:  
> If the OIDC issuer is changed in the trust configuration, the trust breaks. To adapt the trust configuration on SAP BTP side, use the `btp update security/trust` command of the SAP BTP command line interface together with the `--refresh` parameter. This parameter refreshes the trust configuration to reflect changes in the Identity Authentication tenant, for example the issuer value. For more information, see [Managing Trust from SAP BTP to an Identity Authentication Tenant](managing-trust-from-sap-btp-to-an-identity-authentication-tenant-6140107.md).



<a name="loio161f8f0cfac64c4fa2d973bc5f08a894__postreq_z32_k52_tmb"/>

## Next Steps

If you don't need the default identity provider anymore, set it to inactive or hide the logon link.

**Related Information**  


[Managing Security Administrators in Your Subaccount \[Feature Set A\]](managing-security-administrators-in-your-subaccount-feature-set-a-6752c4b.md "Running on the cloud management tools feature set A: When you create a subaccount, SAP BTP automatically grants your user the role for the administration of business users and their authorizations in the subaccount. Having this role, you can also add or remove other users who will then also be user and role administrators of this subaccount.")

[Default Identity Provider](default-identity-provider-d6a8db7.md "SAP ID service is the default identity provider for both platform users and business users (in applications) at SAP BTP. You can start using it without further configuration.")

