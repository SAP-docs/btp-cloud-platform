<!-- loio419dc3d380e74f1abb06ba44d61e71ae -->

# Delete a Subaccount

Delete subaccounts using the SAP BTP cockpit.

 <a name="task_mjr_kgv_f5b"/>

<!-- task\_mjr\_kgv\_f5b -->

## Delete a Subaccount \[Feature Set A\]



<a name="task_mjr_kgv_f5b__prereq_x3p_lgv_f5b"/>

## Prerequisites

-   You're a global account administrator.

-   The subaccount doesn't contain any active subscriptions, service instances, brokers, or platforms. Active subscriptions, service instances, brokers, or platforms can be removed by roles that are environment-specific, for example an org manager in a Cloud Foundry environment.




<a name="task_mjr_kgv_f5b__context_bjp_lgv_f5b"/>

## Context

To prevent accidental deletion of subaccounts and creation of orphaned data, any active subscriptions, service instances, brokers, or platforms must be removed from the subaccount before it can be deleted. Only subaccount administrators can remove such content from a subaccount.



<a name="task_mjr_kgv_f5b__steps_cjp_lgv_f5b"/>

## Procedure

1.  Choose the subaccount that you want to delete.

2.  Choose *Delete Subaccount* and confirm the operation.


**Related Information**  


[Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md "Learn how to navigate to your global accounts and subaccounts in the SAP BTP cockpit.")



[Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

 <a name="task_k2h_zfv_f5b"/>

<!-- task\_k2h\_zfv\_f5b -->

## Delete a Subaccount \[Feature Set B\]



<a name="task_k2h_zfv_f5b__prereq_dhn_pr2_qbb"/>

## Prerequisites

-   You're a global account administrator.




<a name="task_k2h_zfv_f5b__steps_jgs_mxw_z5"/>

## Procedure

1.  Choose the subaccount that you want to delete.

2.  Choose *Delete Subaccount*.

    The cockpit checks if the subaccount contains data, such as active subscriptions, service instances, brokers, or platforms.

3.  If the subaccount is empty, then confirm the operation, after which the subaccount is deleted.

    If the subaccount contains data, such as applications, service instances, spaces, active subscriptions, brokers, and members, then you'll see a recommendation to visit the *Instances and Subscriptions* page to first review the content in the subaccount and to manually remove the content from there. Then you can come back and safely delete the subaccount.

    > ### Note:  
    > If you are not a subaccount administrator, then you won't be able to access the *Instances and Subscriptions*. Instead, you'll be requested to ask a subaccount administrator to review the content in this subaccount and to manually remove the content from there.

    You'll also be given the option to use the *Force Delete* option, which deletes the subaccount and all its data for you. This option must be used with extreme caution because data in the subaccount is deleted permanently, including productive data, if it exists. Before using this option, you are still required to have the instances and subscriptions in the subaccount reviewed by other members of the subaccount to ensure that it is safe to have the data in the subaccount removed without any recovery option.

    > ### Note:  
    > The deletion may take a while depending on the amount of content in your subaccount.


**Related Information**  


[Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md "Learn how to navigate to your global accounts and subaccounts in the SAP BTP cockpit.")



[Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

