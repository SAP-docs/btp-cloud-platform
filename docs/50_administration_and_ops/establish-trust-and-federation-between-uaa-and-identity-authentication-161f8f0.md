<!-- loio161f8f0cfac64c4fa2d973bc5f08a894 -->

# Establish Trust and Federation Between UAA and Identity Authentication

Use your SAP Cloud Identity Services - Identity Authentication tenant as an identity provider or a proxy to your own identity provider hosting your business users. This method avoids the upload and download of SAML meta data by using Open ID Connect \(OIDC\) to establish trust.



<a name="loio161f8f0cfac64c4fa2d973bc5f08a894__prereq_dvg_xgj_p1b"/>

## Prerequisites

-   You've subaccount administrator permissionsor you are a security administrator \(cloud management tools feature set A\) of this account. For more information, see the related link.

-   You've a tenant of SAP Cloud Identity Services - Identity Authentication.

    For more information, see [Initial Setup](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/31af7da133874e199a7df1d42905241b.html) in the documentation for Identity Authentication.

-   The Identity Authentication tenant must be associated with the same customer ID as the relevant global account of SAP BTP.




<a name="loio161f8f0cfac64c4fa2d973bc5f08a894__context_tzl_st2_tmb"/>

## Context

> ### Note:  
> The content in this topic is relevant for cloud management tools feature set A and cloud management tools feature set B.

> ### Restriction:  
> You can only establish trust with a single tenant of Identity Authentication per subaccount using this method.
> 
> Also, when the chosen Identity Authentication service tenant has a custom domain, the trust works only when the server certificate of the IAS tenant has been issued by a trusted CA. See [Trusted Certificate Authentication](../60_security/trusted-certificate-authentication-790cb76.md) for more information.

> ### Recommendation:  
> We recommend that you use SAP Cloud Identity Services - Identity Authentication as a hub, especially if your business users are stored in multiple corporate identity providers.
> 
> For this scenario, connect Identity Authentication as single custom identity provider to SAP BTP. Next use Identity Authentication to integrate your corporate identity providers.
> 
> For more information, see [Corporate Identity Providers](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/19f3eca47db643b6aad448b5dc1075ad.html) and [Configure Conditional Authentication for an Application](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/0143dce88a604533ab5ab17e639fec09.html) in [What Is Identity Authentication](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/27882717f44b445fa287936c6f43dc1f.html) and [SAP Cloud Identity Services - Identity Authentication](https://help.sap.com/viewer/product/IDENTITY_AUTHENTICATION/Cloud/en-US)

> ### Tip:  
> We provide APIs so you can perform this procedure programmatically. For more information, see the [Identity Provider Management API](https://api.sap.com/api/TrustConfigurationAPI/resource) on *SAP API Business Hub*.



<a name="loio161f8f0cfac64c4fa2d973bc5f08a894__steps_a2x_wfg_wmb"/>

## Procedure

1.  In the SAP BTP cockpit, go to your subaccount\(see [Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md)\) and choose *Security* \> *Trust Configuration*.

2.  Choose *Establish Trust*.

3.  Select an identity provider from the list of available and choose *Establish Trust*.

    The identity providers listed are the Identity Authentication tenants associated with your customer account.




<a name="loio161f8f0cfac64c4fa2d973bc5f08a894__result_brm_352_tmb"/>

## Results

You've configured trust in your tenant of the Identity Authentication service, which is your identity provider. Identity Authentication creates an application with the prefix *XSUAA\_* and the display name of your subaccount in the administration console for Identity Authentication.

> ### Example:  
> If your subaccount was named *My Subaccount*, the resulting application in Identity Authentication would be *XSUAA\_My Subaccount*.



<a name="loio161f8f0cfac64c4fa2d973bc5f08a894__postreq_z32_k52_tmb"/>

## Next Steps

If you don't need SAP ID service anymore, set it to inactive.

**Related Information**  


[Managing Security Administrators in Your Subaccount \[Feature Set A\]](managing-security-administrators-in-your-subaccount-feature-set-a-6752c4b.md "Running on the cloud management tools feature set A: When you create a subaccount, SAP BTP automatically grants your user the role for the administration of business users and their authorizations in the subaccount. Having this role, you can also add or remove other users who will then also be user and role administrators of this subaccount.")

