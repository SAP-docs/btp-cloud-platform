<!-- loio5c92cbc690584089ac1e4872db2f8917 -->

# The Security Tab is Missing in the Subaccount



<a name="loio5c92cbc690584089ac1e4872db2f8917__section_k4w_1gk_ddc"/>

## Symptom

If you navigate to your subaccount in the SAP BTP Cockpit, you can't see the Security tab.



<a name="loio5c92cbc690584089ac1e4872db2f8917__section_l4w_1gk_ddc"/>

## Reason and Prerequisites

The problem here is that only the user that created the subaccount is granted the security administrator role. If other subaccount users should be able to see the security tab and make changes to the security configuration, the creator of the subaccount has to grant them the security administrator role.



The creator of the subaccount and the users that should be added must have at least one of the following member roles:

-   They are members of the Cloud Foundry organization \(if available\) in the subaccount.

-   They are members of any Cloud Foundry space that belongs to the organization.

-   They are members of the global account that contains your subaccount.




<a name="loio5c92cbc690584089ac1e4872db2f8917__section_ekn_bgk_ddc"/>

## Solution

The creator of the subaccount has to grant the security administrator role. To do this, follow these steps:

1.  Open your SAP BTP Cockpit.
2.  Navigate to your subaccount.
3.  Choose the **Security** tab and choose **Administrators**.
4.  Choose **Add Administrators**.

    A popup opens, where you can enter the user ID and assign roles.

5.  Type in the ID \(e-mail\) of the user, that you want to add as a security administrator.
6.  To assign roles, make sure that the **User & Role Administrator** checkbox is selected.
7.  Choose **OK**.

After the role has been granted, the user needs to log out and log back in again to make sure the changes are applied to their subaccount user.

