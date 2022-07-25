<!-- loio9e5e635e45eb4fc99a00060043285649 -->

# Platform Users

**User accounts** enable users to log on to SAP BTP and access subaccounts and use services according to the permissions given to them. In this context, it's important to understand the difference between the 2 types of users that we refer to: **Platform users** and **[business users](business-users-3a3f0e1.md)**.

**Platform users** are usually developers, administrators or operators who deploy, administer, and troubleshoot applications and services on SAP BTP. 

Platform users who were added as members and have administrative permissions can view or manage the list of global accounts, directories \(Feature Set B\), subaccounts, and Cloud Foundry orgs and spaces that are available to them. Members access them using the SAP BTP Cockpit, the SAP BTP command-line interface \(btp CLI\) \(available only for Feature Set B\), or the Cloud Foundry command-line interface \(CF CLI\).

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

For platform users, there's a [default identity provider](default-identity-provider-d6a8db7.md). We expect that you have your own user base. We recommend that you configure the Identity Authentication service as the custom identity provider and connect Identity Authentication to your own corporate identity provider.

**Related Information**  


[8600afb350114462ae8b3475a3ccea54.md](establish-trust-and-federation-of-custom-identity-providers-for-platform-users-in-multi-8600afb.md)

[c36898473d704e07a33268c9f9d29515.md](establish-trust-and-federation-of-custom-identity-providers-for-platform-users-feature-c368984.md)

[94ef5154e384408796c035a82b043f82.md](supported-tools-and-services-when-using-custom-identity-providers-for-platform-users-94ef515.md)

[d477618e861c48d2976e03f9b6a3cfe8.md](log-on-with-a-custom-identity-provider-to-the-cloud-foundry-environment-using-the-cloud-d477618.md)

[7eb094334422418f8909647699fea598.md](log-on-with-a-browser-to-the-cloud-foundry-cli-and-service-dashboards-7eb0943.md)

