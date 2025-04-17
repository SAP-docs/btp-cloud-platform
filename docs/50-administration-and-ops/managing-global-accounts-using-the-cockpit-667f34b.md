<!-- loio667f34ba9222450491c2b848cd17e189 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Managing Global Accounts Using the Cockpit

Your SAP BTP global account is the entry point for managing the resources, landscape, and entitlements for your departments and projects in a self-service manner.



<a name="loio667f34ba9222450491c2b848cd17e189__section_mr1_jjq_lnb"/>

## Global Account Settings

As a global account administrator, you can access the global account settings by clicking :gear: in the SAP BTP cockpit.

In the *General* tab of the global account settings, you can obtain general information about your global account, including your global account ID, global account name, account type, payment models, contract status, global account subdomain, geographic access restrictions, and when your account was created.

> ### Note:  
> In this tab, you cannot change any of the values. The only value that you can edit is the global account name, and you can do this in the *Account Explorer* page \(see [Change the Display Name of Your Global Account](change-the-display-name-of-your-global-account-36a6674.md)\).

In the *Subaccounts* tab in the global account settings, you can

-   Define default settings that are used when creating a new subaccount in this global account.

    You can set the supported providers, the default provider, and the default region.

-   Set the option to enable the force deletion of subaccounts.

    If this option is selected, all global account admins can force delete subaccounts that are not marked as "used for production". The force deletion of a subaccount permanently deletes all its data, including applications, service instances, spaces, active subscriptions, and members. The force deletion is permanent and irreversible. This option also enables the force deletion of subaccounts using the btp CLI or the SAP Cloud Management APIs. Subaccounts that are marked as "used for production" cannot be force deleted.


**Related Information**  


[Setting Up Your Account Model](https://help.sap.com/viewer/df50977d8bfa4c9a8a063ddb37113c43/Cloud/en-US/2db81f42f5194454beecde6cd4994dda.html "Learn how to set up your account model with global accounts and subaccounts, and how to use directories, spaces and namespaces to match your business and development needs.") :arrow_upper_right:

[Managing Directories Using the Cockpit](managing-directories-using-the-cockpit-f495ac1.md "Learn how to organize and manage your subaccounts according to your technical and business needs by using directories in the SAP BTP cockpit.")

[Managing Subaccounts Using the Cockpit](managing-subaccounts-using-the-cockpit-55d0b6d.md "Learn how to structure a global account according to your organization’s and project’s requirements with regard to members, authorizations, and entitlements by managing subaccounts.")

