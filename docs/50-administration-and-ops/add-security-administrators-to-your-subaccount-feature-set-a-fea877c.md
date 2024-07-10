<!-- loiofea877c449ba4c5fbb0aafd92a80afb4 -->

# Add Security Administrators to Your Subaccount \[Feature Set A\]

Running on the cloud management tools feature set A: Security administrators manage the user and role assignments in their subaccounts. They also determine which identity providers their subaccounts trust.

> ### Note:  
> The content in this section is only relevant for cloud management tools feature set A. For more information, see [Cloud Management Tools - Feature Set Overview](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/caf4e4e23aef4666ad8f125af393dfb2.html).



<a name="loiofea877c449ba4c5fbb0aafd92a80afb4__prereq_q24_by4_4cb"/>

## Prerequisites

Your user is already a security administrator:

-   Your user inherited the role as the global account administrator, who created this subaccount.

-   Another security administrator assigned the `User & Role Administrator` role to your user using this procedure.




## Context

The users can come from different identity providers. The origin uniquely identifies the identity provider that stores the users. If the platform users are stored in SAP ID service, the origin of the users is *sap.ids*. If your platform users are stored in a custom identity provider, the users have a different origin.



## Procedure

1.  In the SAP BTP cockpit, go to your subaccount.

    Your user is a security administrator in your subaccount, so you see *Security* in the navigation area.

2.  Choose *Security* \> *Administrators*.

3.  Choose *Add Administrators*.

    A popup appears, where you can enter the user ID and the origin and assign roles.

4.  Enter the required data.

    If the origin of the platform users is the default identity provider \(SAP ID service\), choose *sap.ids*.

    If the origin of the platform users is a custom identity provider, choose the name of the origin or *Other* and enter the name of the origin. The origin of a custom identity provider is provided during the configuration of the platform identity provider. For more information, see the related link.

5.  Save your entries.




<a name="loiofea877c449ba4c5fbb0aafd92a80afb4__postreq_xbq_fjm_t4b"/>

## Next Steps

To see *Security* in the navigation area, the users must also have one of the following member roles:

-   The users are members of the Cloud Foundry organization in the subaccount.

    To add members to the Cloud Foundry organization, you must enable Cloud Foundry for your subaccount, even if you don't otherwise use the Cloud Foundry environment.

    > ### Note:  
    > Once you add organization membership to such users, the system can take up to 30 minutes to replicate the required data so these users can view the subaccount in the SAP BTP cockpit.

-   The users are members of the global account that contains your subaccount.

    > ### Tip:  
    > Making users administrators of the global account adds wide ranging authorizations, such as the ability to create new subaccounts. Ask yourself if users really need these authorizations before adding members to the global account.


**Related Information**  


[Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md "Learn how to navigate to your global accounts and subaccounts in the SAP BTP cockpit.")

[Add Org Members](add-org-members-a4eeaf1.md "In the cockpit, add users as org members and assign roles to grant the users access to information, such as user and quota information in a Cloud Foundry org.")

[User and Member Management](../10-concepts/user-and-member-management-cc1c676.md "On SAP BTP, member management takes place at all levels from global account to environment, while user management is relevant for business applications.")

[Establish Trust and Federation of Custom Identity Providers for Platform Users in Multi-Environment Subaccounts \[Feature Set A\]](establish-trust-and-federation-of-custom-identity-providers-for-platform-users-in-multi-8600afb.md "By default, platform users in multi-environment subaccounts are users in SAP ID service. The use of your own identity provider requires integration between the user bases of multi-environment and Neo subaccounts.")

