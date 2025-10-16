<!-- loio65c62c9b10ec468983e6cc007a8717ff -->

# There Was an Error When Authenticating Against the External Identity Provider



<a name="loio65c62c9b10ec468983e6cc007a8717ff__section_abs_b3h_hgc"/>

## Symptom

You have configured a custom identity provider for applications in the SAP BTP cockpit, such as the SAP Cloud Identity Services.

When you open an SAP BTP application, such as a custom developed application or a subscribed application like SAP Business Application Studio, you receive the following error:

***There was an error when authenticating against the external identity provider: The user account must be pre-created. Please contact your system administrator.***



<a name="loio65c62c9b10ec468983e6cc007a8717ff__section_zd2_yzg_hgc"/>

## Reason and Prerequisites

The user from the custom identy provider for applications doesn't exist in the list of users of the SAP BTP cockpit.

When a user authenticates at an application in your subaccount using any identity provider, the User Account and Authentication always stores user-related data provided by the identity provider in the form of shadow users. It uses details of the shadow users to issue tokens that refer to a specific user.

By default, the User Account and Authentication allows any user of any connected identity provider to authenticate to applications in the subaccount. When there’s no corresponding shadow user, it automatically creates one based on the information received from the identity provider.

However if *Create Shadow Users on User Logon* is turned off, shadow users aren't created, which causes the issue.



<a name="loio65c62c9b10ec468983e6cc007a8717ff__section_b22_yzg_hgc"/>

## Solution

To resolve the issue, use one of the following options:

-   Enable *Create Shadow Users on User Logon* for the custom identity provider in the SAP BTP cockpit:

    1.  In the SAP BTP cockpit, go to your subaccount \(see [Navigate in the Cockpit](../50-administration-and-ops/navigate-in-the-cockpit-0874895.md)\) and choose *Security* \> *Trust Configuration*.

    2.  Select your custom identity provider for applications.

    3.  Choose *Edit*.

    4.  Activate *Create Shadow Users During Logon*.

    5.  Choose *Save*.


-   Manually create a user for yor the respective identity provider in the SAP BTP cockpit \(see [Create Users](../50-administration-and-ops/create-users-a3bc7e8.md)\).

    1.  In the SAP BTP cockpit, go to your subaccount \(see [Navigate in the Cockpit](../50-administration-and-ops/navigate-in-the-cockpit-0874895.md)\) and choose *Security* \> *Users*.

    2.  Create a new user for the respective identity provider by using *Create*.


-   Use the SAP Cloud Identity Services - Identity Provisioning to import users from a source system to the respective subaccount. Follow the instructions in [SAP BTP XS Advanced UAA \(Cloud Foundry\)](https://help.sap.com/docs/identity-provisioning/identity-provisioning/target-sap-btp-xs-advanced-uaa-cloud-foundry).


> ### Note:  
> After creating the users in the subaccount, add the relevant role collection for users. The users must have the authorization to access the application \(see [Assign Users to Role Collections](../50-administration-and-ops/assign-users-to-role-collections-c576676.md)\).

**Related Information**  


[Create Users](../50-administration-and-ops/create-users-a3bc7e8.md "As an administrator, you can create shadow users in your subaccount. When you create a shadow user, you must know and specify which identity provider stores the user.")

[Switch Off Automatic Creation of Shadow Users](../50-administration-and-ops/switch-off-automatic-creation-of-shadow-users-d852567.md "To switch off the creation of shadow users in the trust configuration of custom identity providers, administrators must explicitly allow users to log on. Administrators then have full control over who is allowed to log on.")

[SAP BTP XS Advanced UAA \(Cloud Foundry\)](https://help.sap.com/docs/identity-provisioning/identity-provisioning/target-sap-btp-xs-advanced-uaa-cloud-foundry)

