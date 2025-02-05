<!-- loioc36898473d704e07a33268c9f9d29515 -->

# Establish Trust and Federation of Custom Identity Providers for Platform Users

You want to use a custom identity provider for the platform users of SAP BTP in different environments and at the different account levels: global account, directory, and subaccount. By default, platform users in multi-environment subaccounts are users in the default identity provider.



<a name="loioc36898473d704e07a33268c9f9d29515__prereq_avv_mp1_5tb"/>

## Prerequisites

-   You've a tenant of SAP Cloud Identity Services.

    For more information, see [Tenant Model and Licensing](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/93160ebd2dcb40e98aadcbb9a970f2b9.html?version=Cloud) in the documentation for SAP Cloud Identity Services.

-   The SAP Cloud Identity Services tenant is associated with the customer IDs of the relevant global account of SAP BTP.

    For more information, see [Reuse SAP Cloud Identity Services Tenants for Different Customer IDs](https://help.sap.com/docs/identity-authentication/identity-authentication/reuse-sap-cloud-identity-services-tenants-for-different-customer-ids) in the documentation for SAP Cloud Identity Services.

-   Make sure that the email addresses of all users in your identity provider are unique and correct.

    > ### Note:  
    > The email address of the user is the user identifier for all account levels \(global account, directory, multi-environment subaccount\) and for the Cloud Foundry environment.




<a name="loioc36898473d704e07a33268c9f9d29515__context_b1g_rq1_5tb"/>

## Context

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

Platform users perform technical development, deployment, and administration tasks. For example, they perform subaccount administration in the SAP BTP cockpit or access the Cloud Foundry command line interface \(CF CLI\). By hosting these users in your own identity provider, you gain a number of advantages over hosting them in the default identity provider.

-   Integrate the management of these users with your corporate identity management strategy, hosted on your own identity providers. You control your own user lifecycle and single sign-on strategies throughout the entire landscape.

-   Enforce your own password and authentication policies, such as stronger passwords or multifactor authentication.


> ### Note:  
> The content in this section is only relevant for **platform users** and **not** business users.
> 
> For more information about establishing trust for business users, see [Establish Trust and Federation Between SAP Authorization and Trust Management Service and SAP Cloud Identity Services](establish-trust-and-federation-between-sap-authorization-and-trust-management-service-a-161f8f0.md).

You must establish a trust relationship with a custom identity provider in your global account in SAP BTP. The following procedure guides you through the trust configuration in your custom identity provider.



<a name="loioc36898473d704e07a33268c9f9d29515__steps_epg_gr1_5tb"/>

## Procedure

1.  Go to your global account\(see [Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md)\) and choose *Security* \> *Trust Configuration* in the SAP BTP cockpit.

2.  Choose *Establish Trust*.

    The identity providers listed are the SAP Cloud Identity Services tenants associated with your customer ID.

3.  Select an identity provider from the list of available tenants and choose *Next*.

4.  Choose your desired domain of the tenant and continue with *Next*. For a good single sign-on experience, choose the same domain for all SAP BTP accounts and non SAP BTP applications that use this tenant.

5.  Enter a name and a description of the new trust configuration. If possible, set the origin key. The origin key always ends with *\-platform*. Continue with *Next*.

    > ### Note:  
    > The origin key is a technical identifier of an identity provider for platform users. Administrators need it when managing users. Platform users from the identity provider need the origin key when signing in with certain tools, such as the Cloud Foundry command line interface or service dashboards.
    > 
    > You can only set the origin key once for the whole landscape. You can't change the origin key later.
    > 
    > The whole origin key including `-platform` can have at maximum 36 characters. Only use the following characters for the origin key of the trust configuration.
    > 
    > `aA`–`zZ`, `0`–`9`, `-` \(hyphen\), `_` \(underscore\)

6.  The wizard shows you a preview of your configuration. To complete your new trust configuration, choose *Finish*.

    > ### Remember:  
    > If the OIDC issuer was changed in the trust configuration, the trust breaks, but the global account automatically repairs the trust after 24 hours.
    > 
    > To adapt the trust configuration on SAP BTP side, use the `btp update security/trust` command of the SAP BTP command line interface together with the `--refresh` parameter. This parameter immediately refreshes the trust configuration to reflect changes in the SAP Cloud Identity Services tenant, for example the issuer value. For more information, see [Managing Trust from SAP BTP to an SAP Cloud Identity Services Tenant](managing-trust-from-sap-btp-to-an-sap-cloud-identity-services-tenant-6140107.md).




<a name="loioc36898473d704e07a33268c9f9d29515__result_brm_352_tmb"/>

## Results

You've configured trust in your tenant of SAP Cloud Identity Services, which is your identity provider. SAP Cloud Identity Services creates an application with the name *SAP Business Technology Platform*.

> ### Tip:  
> To troubleshoot problems with tokens from SAP Cloud Identity Services, see [Logging OpenID Connect Tokens](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/b6c42b53518b46de8b4dffd8c4c52ed7.html?version=Cloud) in the documentation for SAP Cloud Identity Services.



<a name="loioc36898473d704e07a33268c9f9d29515__postreq_z32_k52_tmb"/>

## Next Steps

-   Add platform users to your orgs and spaces.

    For more information about adding members with the SAP BTP cockpit, see [Add Org Members](add-org-members-a4eeaf1.md) and [Add Space Members](add-space-members-81d0b4d.md).

    For more information about adding members with the command-line interface, see [Add Organization Members Using the Cloud Foundry Command Line Interface](add-organization-members-using-the-cloud-foundry-command-line-interface-1422a5d.md) and [Add Space Members Using the Cloud Foundry Command Line Interface](add-space-members-using-the-cloud-foundry-command-line-interface-d23ea8b.md).

-   Add platform users at different levels \(global account, directory, subaccount\) from the custom identity provider.

    For more information, see [Working with Users](working-with-users-2c91f88.md).

    > ### Note:  
    > For subaccounts in the Neo environment, the identity provider will be offered in the value help only if a user in that identity provider has created at least one Neo subaccount in the corresponding global account and Neo region.
    > 
    > > ### Tip:  
    > > If the identity provider isn't available in the value help for Neo subaccount members, log on to the global account with a user from that identity provider and create a new Neo subaccount. If it's not needed otherwise, you can delete it.

    > ### Recommendation:  
    > We recommend that you keep at least one global account administrator from the default identity provider. You can then use this administrator to log on in the rare instance that access to the custom identity provider fails.

-   Log on to the SAP BTP cockpit as a user from the custom identity provider. In the *Trust Configuration* page, the *Open* link in the *SAP BTP Cockpit* column contains the URL \(for example, *https://emea.cockpit.btp.cloud.sap/cockpit/?idp=cidppuxhm.accounts.ondemand.com*\) for the user to log on with the custom identity provider. Copy the link and send it to your platform user colleagues. Remember if you have the cockpit open and if you want to work in parallel, your current session may be shared by your browser. Open the link in a private or incognito browsing mode.

    For more information, see [Log On with a Custom Identity Provider to the SAP BTP Cockpit](log-on-with-a-custom-identity-provider-to-the-sap-btp-cockpit-0bef982.md).

-   If you want to impose, for example, two-factor authentication for platform users, you must configure [two-factor authentication](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/596e7f8b3f0441aaa8736be6bb368d5f.html) in **all** the SAP Cloud Identity Services applications involved. Multifactor authentication is just used as an example.

    For more information, see [Multi-Factor Authentication](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/596e7f8b3f0441aaa8736be6bb368d5f.html) in the documentation for the SAP Cloud Identity Services service. Keep all settings for SAP Cloud Identity Services applications the same.

    > ### Tip:  
    > Instead of configuring two-factor authentication in all the SAP Cloud Identity Services applications, you could also configure it once in your corporate identity provider.

    > ### Note:  
    > For all the Neo datacenters where you have subaccounts, you might have to configure a separate SAML application \(for example, *SAP Cloud Platform hhw9g3jrxa*\) in SAP Cloud Identity Services.

-   Integrate your SAP Cloud Identity Services tenant with your identity authentication management solution.

    For more information, see [Corporate Identity Provider](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/19f3eca47db643b6aad448b5dc1075ad.html) in the documentation for SAP Cloud Identity Services.

-   Work in the SAP BTP command line interface \(btp CLI\).

    To log on to a global account, you need to provide the hostname of the tenant \(for example, *ar9ibaxhm*\) with the `--idp` parameter. See [Log in with a Custom Identity Provider](log-in-with-a-custom-identity-provider-e48e486.md).

    To work with users and role collections on global account, directory, or subaccount level, you need to provide the origin key with the `--of-idp` parameter in the following commands: `btp list security/user`, `btp get security/user`, `btp delete security/user`, `btp assign security/role-collection`, `btp unassign security/role-collection`.

    Both values can be found in the cockpit under *Security* → *Trust Configuration* → *Custom Platform Identity Providers*.

    As an administrator, you want to determine which of the SAP Cloud Identity Services tenants' domains SAP BTP should use for platform user logon. For this reason, you specify a custom domain for an SAP Cloud Identity Services tenant. You can use the `btp update security/trust` command and specify the domain in the `--domain` parameter.

-   Work in the Cloud Foundry command line interface \(CF CLI\).

    For more information, see [Log On with a Custom Identity Provider to the Cloud Foundry Environment Using the Cloud Foundry Command-Line Interface](log-on-with-a-custom-identity-provider-to-the-cloud-foundry-environment-using-the-cloud-d477618.md).

-   The Kyma environment has a separate configuration for the identity provider. We recommend that you also configure your Kyma environment to use SAP Cloud Identity Services as your custom identity provider.

    For more information, see [Configure a Custom Identity Provider for Kyma](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/67bcc6e2d4d749659faf3ede1853f19e.html).


**Related Information**  


[User and Member Management](../10-concepts/user-and-member-management-cc1c676.md "On SAP BTP, user management takes place at all levels from global account to environment. There are different types of users, such as depending on their roles in the company.")

