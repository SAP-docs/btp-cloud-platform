<!-- loio419dc3d380e74f1abb06ba44d61e71ae -->

# Delete a Subaccount

Delete subaccounts using the SAP BTP cockpit.



<a name="loio419dc3d380e74f1abb06ba44d61e71ae__prereq_dhn_pr2_qbb"/>

## Prerequisites

-   You're a global account administrator.

-   The subaccount doesn't contain any active subscriptions, service instances, brokers, or platforms.

    -   When using cloud management tools feature set A, active subscriptions, service instances, brokers, or platforms can be removed by roles that are environment-specific, for example an org manager in a Cloud Foundry environment.

    -   When using cloud management tools feature set B, subaccount administrators can remove active subscriptions, service instances, brokers, or platforms.




<a name="loio419dc3d380e74f1abb06ba44d61e71ae__context_usz_pr2_qbb"/>

## Context

To prevent accidental deletion of subaccounts and creation of orphaned data, any active subscriptions, service instances, brokers, or platforms must be removed from the subaccount before it can be deleted. Only subaccount administrators can remove such content from a subaccount.



<a name="loio419dc3d380e74f1abb06ba44d61e71ae__steps_jgs_mxw_z5"/>

## Procedure

1.  Choose the subaccount that you want to delete.

2.  Choose *Delete Subaccount* and confirm the operation.


**Related Information**  


[Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md "Learn how to navigate to your global accounts and subaccounts in the SAP BTP cockpit.")



