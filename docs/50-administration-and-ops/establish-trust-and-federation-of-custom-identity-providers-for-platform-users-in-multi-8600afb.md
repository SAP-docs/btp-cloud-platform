<!-- loio8600afb350114462ae8b3475a3ccea54 -->

# Establish Trust and Federation of Custom Identity Providers for Platform Users in Multi-Environment Subaccounts \[Feature Set A\]

> ### Note:  
> The content in this section is only relevant for cloud management tools feature set A. For more information, see [Cloud Management Tools - Feature Set Overview](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/caf4e4e23aef4666ad8f125af393dfb2.html).

> ### Note:  
> The content in this section is only relevant for **platform users** and **not** business users.
> 
> For more information about establishing trust for subaccounts for business users, see [Establish Trust and Federation Between SAP Authorization and Trust Management Service and SAP Cloud Identity Services](establish-trust-and-federation-between-sap-authorization-and-trust-management-service-a-161f8f0.md).

By default, platform users in multi-environment subaccounts are users in SAP ID service. The use of your own identity provider requires integration between the user bases of multi-environment and Neo subaccounts.



<a name="loio8600afb350114462ae8b3475a3ccea54__prereq_wtn_c5p_jlb"/>

## Prerequisites

-   You have an SAP Cloud Identity Services tenant.

    For more information, see the [documentation](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/d17a116432d24470930ebea41977a888.html) for SAP Cloud Identity Services.

-   You've a subaccount with the Neo environment in addition to your multienvironment subaccount.

    You need this subaccount in the Neo environment to access the SAP BTP cockpit. We’re using the subaccount in the Neo environment with a configured trust to an SAP Cloud Identity Services tenant, and then establish trust between the SAP Cloud Identity Services tenant and multi-environment subaccounts.

    For more information setting up a Neo subaccount, see [Managing Global Accounts Using the Cockpit](https://help.sap.com/docs/BTP/ea72206b834e4ace9cd834feed6c0e09/55d0b6d8b96846b8ae93b85194df0944.html?version=Cloud) and [Platform Identity Provider](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/80edbe70b8f3478d8a59c21a91a47aa6.html "The platform identity provider is the user base for access to your SAP BTP subaccount in the Neo environment. The default user base is provided by SAP ID Service. You can switch to an Identity Authentication tenant if you want to use a custom user base.") :arrow_upper_right:.

    If you run you own identity provider, connect it to SAP Cloud Identity Services, which has a custom trust configuration with SAP BTP.

    For more information, see [Configure Trust with Corporate Identity Provider](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/33832e58695345eea2cd91a2cc8ab24c.html) in the documentation for SAP Cloud Identity Services.

-   Make sure that the e-mail addresses of all users in your identity provider are correct since the e-mail address is the unique identifier of users in the Cloud Foundry environment.




<a name="loio8600afb350114462ae8b3475a3ccea54__context_f1m_fht_ylb"/>

## Context

Platform users perform technical development, deployment, and administration tasks. They perform subaccount administration in the SAP BTP cockpit or access the Cloud Foundry command-line interface \(CF CLI\). By hosting these users in your own identity provider, you gain a number of advantages over hosting them in SAP ID service.

-   Integrate the management of these users with your broader identity management strategy, hosted on your own identity providers. You control your own user lifecycle and single sign-on strategies throughout the entire landscape.

-   Enforce your own password and authentication policies, such as stronger passwords or multifactor authentication.


For more information, see [Supported Tools and Services When Using Custom Identity Providers for Platform Users](supported-tools-and-services-when-using-custom-identity-providers-for-platform-users-94ef515.md).



<a name="loio8600afb350114462ae8b3475a3ccea54__steps_g1m_fht_ylb"/>

## Procedure

1.  Connect your SAP Cloud Identity Services tenant to your subaccount in the Neo environment.

    For more information, see *Create Trust with the SAP Cloud Identity Services Tenant* under [Platform Identity Provider](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/80edbe70b8f3478d8a59c21a91a47aa6.html "The platform identity provider is the user base for access to your SAP BTP subaccount in the Neo environment. The default user base is provided by SAP ID Service. You can switch to an Identity Authentication tenant if you want to use a custom user base.") :arrow_upper_right: in the documentation for SAP BTP, Neo Environment.

2.  In your SAP Cloud Identity Services tenant, create an application of type *OpenID Connect*, and configure it. For configuring the SAP Cloud Identity Services tenant, see [Configure OpenID Connect Application for Resource Owner Password Credentials Flow](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/cafba7730eeb4d4bbfaa0b200e8cfbac.html) in the documentation for SAP Cloud Identity Services.

    > ### Note:  
    > Use the complete URL of the SAP Cloud Identity Services tenant starting with `https` as name of the identity provider settings. The OIDC protocol uses the name as the issuer of the SAP Cloud Identity Services tenant.

    Skip creating redirect URIs for now. SAP Support provides the redirect URIs later.

3.  In your SAP Cloud Identity Services application, add a client ID and client secret for the application.

    For more information, see [Configure Secrets for API Authentication](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/5c3c35e01e3c4e7e8dd72af60c997c5d.html) in the documentation for SAP Cloud Identity Services.

4.  Open a ticket with SAP Support \(for the component, see [Monitoring and Troubleshooting](../60-security/monitoring-and-troubleshooting-1b3e89e.md)\) and provide the following information:

    -   Component \(`BC-CP-CF-SEC-IAM`\)

    -   Multi-environment regions that you want to access using the SAP BTP cockpit.

    -   URL of your SAP Cloud Identity Services tenant.

        For example: `https://caev6ngwk.accounts.ondemand.com`

    -   Client ID and client secret of the SAP Cloud Identity Services application connected to the Cloud Foundry landscape for the OIDC token of your SAP Cloud Identity Services account.

        > ### Caution:  
        > Enter the client secret in the secure area of the ticket.

    -   Origin that identifies the identity provider during logon using Cloud Foundry command-line interface and during the assignment of platform authorizations to users.

        > ### Restriction:  
        > The origin has a 1-to-1 relationship with the user base of the SAP Cloud Identity Services tenant. This origin must be unique for all customers of SAP BTP. The origin is used in the list of members. It shows in which identity provider the user is stored. Provide an origin name with a maximum of 36 7-bit ASCII characters. SAP support will get back to you if necessary.
        > 
        > We recommend using the tenant ID as the origin. For example:
        > 
        > -   `caev6ngwk` from `https://caev6ngwk.accounts.ondemand.com`
        > 
        > -   `acme-test` from `https://acme-test.accounts.ondemand.com`
        > 
        > 
        > Or choose a name that's easier for you to remember. Whatever you choose, choose your origin carefully. We don't support changing the origin after configuration.


    > ### Note:  
    > Our operations team needs to make manual adjustments in the SAP BTP regions to establish trust between the SAP Cloud Identity Services tenant and Neo regions.

    For more information about opening a ticket, see [Getting Support](../70-getting-support/getting-support-5dd7398.md).

    SAP answers with redirect URIs and test instructions to confirm that everything has been set up correctly.

5.  In your SAP Cloud Identity Services application, update your *OpenID Connect Configuration* with the redirect URIs provided by SAP Support.

    > ### Remember:  
    > If the OIDC issuer was changed in the trust configuration, the trust breaks, but the global account automatically repairs the trust after 24 hours.
    > 
    > To adapt the trust configuration on SAP BTP side, use the `btp update security/trust` command of the SAP BTP command line interface together with the `--refresh` parameter. This parameter immediately refreshes the trust configuration to reflect changes in the SAP Cloud Identity Services tenant, for example the issuer value. For more information, see [Managing Trust from SAP BTP to an SAP Cloud Identity Services Tenant](managing-trust-from-sap-btp-to-an-sap-cloud-identity-services-tenant-6140107.md).

    For more information, see [Configure OpenID Connect Application for Resource Owner Password Credentials Flow](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/cafba7730eeb4d4bbfaa0b200e8cfbac.html) in the documentation for SAP Cloud Identity Services.

6.  Test the login redirect URI.

    With the instructions provided by the support ticket, log on with a user in your custom identity provider.

    For more information about the SAP Cloud Identity Services tenant, see [Configuring Tenant Settings](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/d4d6fdc8745f41ce8001c818e66c5e45.html?q=Cofiguring%20tenant%20settings) in the documentation for SAP Cloud Identity Services.

7.  To find the SAP BTP cockpit logon URL of the custom platform identity provider, go to the *Platform Identity Provider* tab of the Neo subaccount in **<trusted\_\_subaccount\>** \> *Security* \> *Trust*.

8.  To start the logon page of the custom platform identity provider, choose the *Cockpit* button.

    You can now log on with your user of the custom identity provider.

    > ### Restriction:  
    > This location does not support use of a custom domain.




<a name="loio8600afb350114462ae8b3475a3ccea54__postreq_o22_ptn_llb"/>

## Next Steps

-   Add platform users to your orgs and spaces.

    For more information about adding members with the SAP BTP cockpit, see [Add Org Members](add-org-members-a4eeaf1.md) and [Add Space Members](add-space-members-81d0b4d.md).

    For more information about adding members with the command-line interface, see [Add Organization Members Using the Cloud Foundry Command Line Interface](add-organization-members-using-the-cloud-foundry-command-line-interface-1422a5d.md) and [Add Space Members Using the Cloud Foundry Command Line Interface](add-space-members-using-the-cloud-foundry-command-line-interface-d23ea8b.md).

-   Work in the Cloud Foundry command-line interface.

    For more information, see [Log On with a Custom Identity Provider to the Cloud Foundry Environment Using the Cloud Foundry Command-Line Interface](log-on-with-a-custom-identity-provider-to-the-cloud-foundry-environment-using-the-cloud-d477618.md).

-   If you want to impose, for example, two-factor authentication to protect your subaccounts, you must configure two-factor authentication in all SAP Cloud Identity Services applications involved.

    For more information, see [Configure Risk-Based Authentication](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/bc52fbf3d59447bbb6aa22f80d8b6056.html#loiobc52fbf3d59447bbb6aa22f80d8b6056) in the documentation for SAP Cloud Identity Services.

    -   In the application of the SAP Cloud Identity Services tenant for your Neo subaccount \(required for SAP BTP cockpit access\)

    -   In the application of the SAP Cloud Identity Services tenant for the Cloud Foundry environment



**Related Information**  


[User and Member Management](../10-concepts/user-and-member-management-cc1c676.md "On SAP BTP, member management takes place at all levels from global account to environment, while user management is relevant for business applications.")

[Bringing Your Corporate Identity Provider for Platform Users \[Feature Set A\]](../10-concepts/bringing-your-corporate-identity-provider-for-platform-users-feature-set-a-783ff50.md "SAP BTP supports the use of your own identity provider for platform users.")

[SAP Note 2964274 - Establish Trust and Federation for Cloud Foundry Platform Users for Custom Identity Providers \[Feature Set A\]](https://launchpad.support.sap.com/#/notes/2964274)

