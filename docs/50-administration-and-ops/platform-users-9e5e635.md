<!-- loio9e5e635e45eb4fc99a00060043285649 -->

# Platform Users

**User accounts** enable users to log on to SAP BTP and access subaccounts and use services according to the permissions given to them. In this context, it's important to understand the difference between the 2 types of users that we refer to: **Platform users** and **[business users](business-users-3a3f0e1.md)**.

**Platform users** are usually developers, administrators or operators who deploy, administer, and troubleshoot applications and services on SAP BTP. 

Platform users who were added as members and have administrative permissions can view or manage the list of global accounts, subaccounts, and Cloud Foundry orgs and spaces that are available to them. Members access them using the SAP BTP Cockpit or the SAP BTP command-line interface \(btp CLI\).

For platform users, there's a [default identity provider](default-identity-provider-d6a8db7.md). We expect that you have your own user base.

We recommend that you configure the Identity Authentication service as the identity provider and connect Identity Authentication to your own corporate identity provider.

