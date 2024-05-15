<!-- loio9e5e635e45eb4fc99a00060043285649 -->

# Platform Users

**User accounts** enable users to log on to SAP BTP, access subaccounts, and to use services according to the permissions granted to them. In this context, it's important to understand the difference between the two types of users that we refer to: Platform users and business users.

**Platform users** are usually developers, administrators or operators who deploy, administer, and troubleshoot applications and services on SAP BTP. 

Platform users who were added as members and have administrative permissions can view or manage the list of global accounts, directories \(Feature Set B\), subaccounts, and Cloud Foundry orgs and spaces that are available to them. Members access them using the SAP BTP Cockpit, the SAP BTP command-line interface \(btp CLI\) \(available only for Feature Set B\), or the Cloud Foundry command-line interface \(CF CLI\).

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

For platform users, there's a [default identity provider](default-identity-provider-d6a8db7.md). We expect that you have your own user base. We recommend that you configure the Identity Authentication service as the custom identity provider and connect Identity Authentication to your own corporate identity provider.

**Related Information**  


[Business Users](business-users-3a3f0e1.md "User accounts enable users to log on to SAP BTP, access subaccounts, and to use services according to the permissions granted to them. In this context, it's important to understand the difference between the two types of users that we refer to: business users and platform users.")

[Establish Trust and Federation of Custom Identity Providers for Platform Users in Multi-Environment Subaccounts \[Feature Set A\]](establish-trust-and-federation-of-custom-identity-providers-for-platform-users-in-multi-8600afb.md "By default, platform users in multi-environment subaccounts are users in SAP ID service. The use of your own identity provider requires integration between the user bases of multi-environment and Neo subaccounts.")

[Establish Trust and Federation of Custom Identity Providers for Platform Users \[Feature Set B\]](establish-trust-and-federation-of-custom-identity-providers-for-platform-users-feature-c368984.md "You want to use a custom identity provider for the platform users of SAP BTP in different environments and at the different account levels: global account, directory, and subaccount. By default, platform users in multi-environment subaccounts are users in the default identity provider.")

[Supported Tools and Services When Using Custom Identity Providers for Platform Users](supported-tools-and-services-when-using-custom-identity-providers-for-platform-users-94ef515.md "Not all tools and services of SAP BTP support the use of custom identity providers with platform users. We provide a list of tools and services, which support this feature and any restrictions that apply.")

[Log On with a Custom Identity Provider to the Cloud Foundry Environment Using the Cloud Foundry Command-Line Interface](log-on-with-a-custom-identity-provider-to-the-cloud-foundry-environment-using-the-cloud-d477618.md "Learn how to use different methods to log on to Cloud Foundry using a custom identity provider (IdP).")

[Log on with a Browser to the Cloud Foundry CLI and Service Dashboards](log-on-with-a-browser-to-the-cloud-foundry-cli-and-service-dashboards-7eb0943.md "Platform users of the Cloud Foundry environment have the option to log on with a custom identity provider or the default identity provider.")

