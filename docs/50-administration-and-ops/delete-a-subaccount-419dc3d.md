<!-- loio419dc3d380e74f1abb06ba44d61e71ae -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Delete a Subaccount

Delete subaccounts using the SAP BTP cockpit to clean up your account hierarchy, free up quota used by services in your subaccounts, and to reduce overall costs. 

<a name="task_a4g_zp3_bvb"/>

<!-- task\_a4g\_zp3\_bvb -->

## Delete a Subaccount \[Feature Set B\]



<a name="task_a4g_zp3_bvb__prereq_b4g_zp3_bvb"/>

## Prerequisites

-   You're a global account administrator.




<a name="task_a4g_zp3_bvb__steps_d4g_zp3_bvb"/>

## Procedure

1.  In the cockpit, go to the *Account Explorer* page of your global account.

2.  In the account hierarchy, locate the subaccount that you want to delete.

3.  In the *Actions* \(<span class="SAP-icons"></span> \) context menu of the subaccount, choose *Delete*.

    The cockpit first checks if the subaccount contains data, such as active subscriptions, service instances, brokers, or platforms.

4.  If the subaccount is empty, then confirm the operation, after which the subaccount is deleted.

    If you are a subaccount administrator and the subaccount contains data, such as applications, service instances, spaces, active subscriptions, brokers, and members, then we strongly recommended that you visit the *Instances and Subscriptions* page to review the content in the subaccount and to manually remove the content from there. Then you can come back and safely delete the subaccount.

    > ### Note:  
    > If you are not a subaccount administrator, then you won't be able to access the *Instances and Subscriptions*. Instead, you'll have to ask a subaccount administrator in your organization to review the content in this subaccount and to manually remove the content from there.

    > ### Caution:  
    > If the subaccount contains data, then you're also given the option to use the **force-delete** option, which deletes the subaccount and all its data for you.
    > 
    > You must use this option with extreme caution because any data in the subaccount is deleted permanently, including productive data, without any recovery option.
    > 
    > It is your responsibility to confirm that the subaccount is safe to delete before using the force-delete option. If you cannot check the content of the subaccount, you can get the subaccount reviewed by other qualified members of your organization.

    > ### Note:  
    > The deletion may take up to 12 hours to complete depending on the amount of content in your subaccount. If your subaccount contains service instances, subscriptions, and runtime environments, these need to be deprovisioned as part of the purge operation, which is a timely process. After the subaccount is deleted, it could take a few more days for some related services to be deleted. Note that you won't be charged for any continued usage of these services in the subaccount during the deletion cleanup.


**Related Information**  


[Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md "Learn how to navigate to your global accounts and subaccounts in the SAP BTP cockpit.")

[Relationship Between Global Accounts, Subaccounts, and Directories \[Feature Set B\]](../10-concepts/account-model-8ed4a70.md#loio20828fc639954939890d3d74a22c5f66 "A global account can group together different directories and subaccounts that an administrator makes available to users. Administrators can assign the available entitlements and quotas of a global account to its different subaccounts and move it between subaccounts that belong to the same global account.")

[Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

<a name="task_hm1_y43_bvb"/>

<!-- task\_hm1\_y43\_bvb -->

## Delete a Subaccount \[Feature Set A\]



<a name="task_hm1_y43_bvb__prereq_im1_y43_bvb"/>

## Prerequisites

-   You're a global account administrator.

-   The subaccount doesn't contain any active subscriptions, service instances, brokers, or platforms. Active subscriptions, service instances, brokers, or platforms can be removed by roles that are environment-specific, for example an org manager in a Cloud Foundry environment.




<a name="task_hm1_y43_bvb__context_lm1_y43_bvb"/>

## Context

To prevent accidental deletion of subaccounts and creation of orphaned data, any active subscriptions, service instances, brokers, or platforms must be removed from the subaccount before it can be deleted. Only subaccount administrators can remove such content from a subaccount.



<a name="task_hm1_y43_bvb__steps_mm1_y43_bvb"/>

## Procedure

1.  In the cockpit, navigate into the subaccount that you want to delete.

2.  Choose *Delete Subaccount* and confirm the operation.


**Related Information**  


[Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md "Learn how to navigate to your global accounts and subaccounts in the SAP BTP cockpit.")

[Relationship Between Global Accounts and Subaccounts \[Feature Set A\]](../10-concepts/account-model-8ed4a70.md#loioeeda449cf252418a97e0f7c9abd30b9a "A global account can group together different subaccounts that an administrator makes available to users. Administrators can assign the available quotas of a global account to its different subaccounts and move it between subaccounts that belong to the same global account.")

[Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

