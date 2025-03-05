<!-- loio38958e5398d04669aa359b18ee92cd77 -->

# Unexpected User in Subaccount



<a name="loio38958e5398d04669aa359b18ee92cd77__section_k4w_1gk_ddc"/>

## Symptom

As a subaccount administrator, you find a user you didn't add to your subaccount and are concerned how it got there.



<a name="loio38958e5398d04669aa359b18ee92cd77__section_l4w_1gk_ddc"/>

## Reason and Prerequisites

-   Another subaccount administrator added the user without your knowledge.

-   The user was added by a background job, which syncs the Cloud Foundry users from orgs or spaces in that subaccount.

-   The user was unexpectedly added by a provisioning job.




<a name="loio38958e5398d04669aa359b18ee92cd77__section_ekn_bgk_ddc"/>

## Solution

Check the audit log of the SAP Authorization and Trust Management service. See [Auditing and Logging Information for SAP Authorization and Trust Management Service](auditing-and-logging-information-for-sap-authorization-and-trust-management-service-d8f4b7c.md).

There, you can see who created the user and coordinate your processes.

-   If the creator was the CLOUD\_FOUNDRY\_SNYC user, the user was created by the background job for synchronizing Cloud Foundry users. If you don't want SAP BTP to create these users you can disable this job for your subaccount. See [Switch Off Automatic Creation of Shadow Users](../50-administration-and-ops/switch-off-automatic-creation-of-shadow-users-d852567.md).

-   If the creator was a provisioning job, check with the solution used for provisioning and check for errors in configuration. For more information, see [Provision Users to SAP BTP Accounts](../50-administration-and-ops/provision-users-to-sap-btp-accounts-bb1b2f4.md).


**Related Information**  


[Working with Users](../50-administration-and-ops/working-with-users-2c91f88.md "In the SAP BTP cockpit, you can see the users of your global account or subaccount, user-related identity provider information, and their authorizations. In a user's overview, you can create and delete users, and assign role collections. You can also display an overview of the role collections, where you can drill down all the way to the role, and see the application that the role belongs to.")

[About User Management in the Cloud Foundry Environment](../50-administration-and-ops/about-user-management-in-the-cloud-foundry-environment-8e6ce96.md "The Cloud Foundry environment has its own store for user data within SAP BTP. Understanding the relationship between SAP BTP and the Cloud Foundry environment is useful.")

[Add Members to Your Subaccount](../50-administration-and-ops/add-members-to-your-subaccount-1e1b7b6.md "Add members to your subaccount to enable users to access resources available there. Platform users manage subaccounts with cloud management tools, while business users consume applications and services.")

[Add Members to Your Global Account](../50-administration-and-ops/add-members-to-your-global-account-4a04913.md "Add users as global account members using the SAP BTP cockpit.")

