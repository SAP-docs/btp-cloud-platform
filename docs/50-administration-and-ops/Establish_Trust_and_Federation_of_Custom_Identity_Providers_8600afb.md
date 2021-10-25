<!-- loio8600afb350114462ae8b3475a3ccea54 -->

# Establish Trust and Federation of Custom Identity Providers for Platform Users in Multi-Environment Subaccounts \[Feature Set A\]

> ### Note:  
> The content in this section is only relevant for cloud management tools feature set A. For more information, see [Cloud Management Tools - Feature Set Overview](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/caf4e4e23aef4666ad8f125af393dfb2.html).

> ### Note:  
> The content in this section is only relevant for **platform users** and **not** business users.
> 
> For more information about establishing trust for subaccounts for business users, see [Establish Trust and Federation Between UAA and Identity Authentication](Establish_Trust_and_Federation_Between_UAA_and_Identity_Authentication_161f8f0.md#loio161f8f0cfac64c4fa2d973bc5f08a894).

By default, platform users in multi-environment subaccounts are users in SAP ID service. The use of your own identity provider requires integration between the user bases of multi-environment and Neo subaccounts.



<a name="loio8600afb350114462ae8b3475a3ccea54__prereq_wtn_c5p_jlb"/>

## Prerequisites

-   You've an Identity Authentication tenant.

    > ### Restriction:  
    > Trial accounts of SAP BTP don’t provide an Identity Authentication tenant. Without an Identity Authentication tenant, you can't configure a custom platform identity provider in a trial account.

    For more information, see the [documentation](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/d17a116432d24470930ebea41977a888.html) for SAP BTP Identity Authentication service.

-   You've a subaccount with the Neo environment in addition to your multienvironment subaccount.

    You need this subaccount in the Neo environment to access the SAP BTP cockpit. We’re using the subaccount in the Neo environment with a configured trust to an Identity Authentication tenant, and then establish trust between the Identity Authentication tenant and multi-environment subaccounts.

    For more information setting up a Neo subaccount, see [Create a Subaccount](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/c48c2985de5a4fa692f03b7ee3f563b2.html "Create subaccounts in your global account using the SAP BTP cockpit.") :arrow_upper_right: and [Platform Identity Provider](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/80edbe70b8f3478d8a59c21a91a47aa6.html "The platform identity provider is the user base for access to your SAP BTP subaccount in the Neo environment. The default user base is provided by SAP ID Service. You can switch to an Identity Authentication tenant if you want to use a custom user base.") :arrow_upper_right:.

    If you run you own identity provider, connect it to the Identity Authentication service, which has a custom trust configuration with SAP BTP.

    For more information, see [Configure Trust with Corporate Identity Provider](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/33832e58695345eea2cd91a2cc8ab24c.html) in the documentation for the Identity Authentication service.

-   Make sure that the e-mail addresses of all users in your identity provider are correct since the e-mail address is the unique identifier of users in the Cloud Foundry environment.




<a name="loio8600afb350114462ae8b3475a3ccea54__context_f1m_fht_ylb"/>

## Context

Platform users perform technical development, deployment, and administration tasks. They perform subaccount administration in the SAP BTP cockpit or access the Cloud Foundry command-line interface \(CF CLI\). By hosting these users in your own identity provider, you gain a number of advantages over hosting them in SAP ID service.

-   Integrate the management of these users with your broader identity management strategy, hosted on your own identity providers. You control your own user lifecycle and single sign-on strategies throughout the entire landscape.

-   Enforce your own password and authentication policies, such as stronger passwords or multifactor authentication.


For more information, see [Supported Tools and Services When Using Custom Identity Providers for Platform Users\[Feature Set A\]](Supported_Tools_and_Services_When_Using_Custom_Identity_Providers_94ef515.md).



<a name="loio8600afb350114462ae8b3475a3ccea54__steps_g1m_fht_ylb"/>

## Procedure

1.  Connect your Identity Authentication tenant to your subaccount in the Neo environment.

    For more information, see *Create Trust with the Identity Authentication Tenant* under [Platform Identity Provider](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/80edbe70b8f3478d8a59c21a91a47aa6.html "The platform identity provider is the user base for access to your SAP BTP subaccount in the Neo environment. The default user base is provided by SAP ID Service. You can switch to an Identity Authentication tenant if you want to use a custom user base.") :arrow_upper_right: in the documentation for SAP BTP, Neo Environment.

2.  In your Identity Authentication tenant, create an application of type *OpenID Connect*, and configure it. For configuring the Identity Authentication tenant, see [Configure OpenID Connect Application for Resource Owner Password Credentials Flow](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/cafba7730eeb4d4bbfaa0b200e8cfbac.html) in the documentation for Identity Authentication service.

    > ### Note:  
    > Use the complete URL of the Identity Authentication tenant starting with `https` as name of the identity provider settings. The OIDC protocol uses the name as the issuer of the Identity Authentication tenant.

    Skip creating redirect URIs for now. SAP Support provides the redirect URIs later.

3.  In your Identity Authentication application, add a client ID and client secret for the application.

    For more information, see [Configure Secrets for API Authentication](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/5c3c35e01e3c4e7e8dd72af60c997c5d.html) in the documentation for the Identity Authentication service.

4.  Open a ticket with SAP Support \(for the component, see [Monitoring and Troubleshooting](../60-security/Monitoring_and_Troubleshooting_1b3e89e.md)\) and provide the following information:

    -   Component \(`BC-CP-CF-SEC-IAM`\)

    -   Multi-environment regions that you want to access using the SAP BTP cockpit.

    -   URL of your Identity Authentication tenant.

        For example: `https://caev6ngwk.accounts.ondemand.com`

    -   Client ID and client secret of the Identity Authentication application connected to the Cloud Foundry landscape for the OIDC token of your Identity Authentication account.

        > ### Caution:  
        > Enter the client secret in the secure area of the ticket.

    -   Origin that identifies the identity provider during logon using Cloud Foundry command-line interface and during the assignment of platform authorizations to users.

        > ### Restriction:  
        > The origin has a 1-to-1 relationship with the user base of the Identity Authentication tenant. This origin must be unique for all customers of SAP BTP. The origin is used in the list of members. It shows in which identity provider the user is stored. Provide an origin name with a maximum of 36 7-bit ASCII characters. SAP support will get back to you if necessary.
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
    > Our operations team needs to make manual adjustments in the SAP BTP regions to establish trust between the Identity Authentication tenant and Neo regions.

    For more information about opening a ticket, see [Getting Support](../70-getting-support/Getting_Support_5dd7398.md).

    SAP answers with redirect URIs and test instructions to confirm that everything has been set up correctly.

5.  In your Identity Authentication application, update your *OpenID Connect Configuration* with the redirect URIs provided by SAP Support.

    For more information, see [Configure OpenID Connect Application for Resource Owner Password Credentials Flow](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/cafba7730eeb4d4bbfaa0b200e8cfbac.html) in the documentation for the Identity Authentication service.

6.  Test the login redirect URI.

    With the instructions provided by the support ticket, log on with a user in your custom identity provider.

    For more information about the Identity Authentication tenant, see [Configuring Tenant Settings](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/d4d6fdc8745f41ce8001c818e66c5e45.html?q=Cofiguring%20tenant%20settings) in the documentation for the Identity Authentication service.

7.  To find the SAP BTP cockpit logon URL of the custom platform identity provider, go to the *Platform Identity Provider* tab of the Neo subaccount in **<trusted\_\_subaccount\>** \> *Security* \> *Trust*.

8.  To start the logon page of the custom platform identity provider, choose the *Cockpit* button.

    You can now log on with your user of the custom identity provider.




<a name="loio8600afb350114462ae8b3475a3ccea54__postreq_o22_ptn_llb"/>

## Next Steps

-   Add platform users to your orgs and spaces.

    For more information about adding members with the SAP BTP cockpit, see [Add Org Members Using the Cockpit](Add_Org_Members_Using_the_Cockpit_a4eeaf1.md) and [Add Space Members Using the Cockpit](Add_Space_Members_Using_the_Cockpit_81d0b4d.md).

    For more information about adding members with the command-line interface, see [Add Organization Members Using the Cloud Foundry Command Line Interface](Add_Organization_Members_Using_the_Cloud_Foundry_Command_Line_Interface_1422a5d.md) and [Add Space Members Using the Cloud Foundry Command Line Interface](Add_Space_Members_Using_the_Cloud_Foundry_Command_Line_Interface_d23ea8b.md).

-   Work in the Cloud Foundry command-line interface.

    For more information, see [Log On with a Custom Identity Provider to the Cloud Foundry Environment Using the Cloud Foundry Command-Line Interface](Log_On_with_a_Custom_Identity_Provider_d477618.md).

-   If you want to impose, for example, two-factor authentication to protect your subaccounts, you must configure two-factor authentication in all Identity Authentication applications involved.

    For more information, see [Configure Risk-Based Authentication](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/bc52fbf3d59447bbb6aa22f80d8b6056.html#loiobc52fbf3d59447bbb6aa22f80d8b6056) in the documentation for the Identity Authentication service.

    -   In the application of the Identity Authentication tenant for your Neo subaccount \(required for SAP BTP cockpit access\)

    -   In the application of the Identity Authentication tenant for the Cloud Foundry environment



**Related Information**  


[User and Member Management](../10-concepts/User_and_Member_Management_cc1c676.md "On the cloud platform, member management happens at all levels from global account to space, while user management is done for deployed applications.")

[Bringing Your Corporate Identity Provider for Platform Users \[Feature Set A\]](../10-concepts/Bringing_Your_Corporate_Identity_Provider_for_Platform_Users_Feature_Set_A_783ff50.md "SAP BTP supports the use of your own identity provider for platform users. The use of your own identity provider requires integration between the user bases of Cloud Foundry and Neo environments.")

[SAP Note 2964274 - Establish Trust and Federation for Cloud Foundry Platform Users for Custom Identity Providers \[Feature Set A\]](https://launchpad.support.sap.com/#/notes/2964274)

