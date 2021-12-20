<!-- loioa4eeaf179ee646b99558f27c0bae7b3e -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Add Org Members Using the Cockpit

You can add org members and assign roles to them at the subaccount level in the cockpit.



## Prerequisites

You have the Org Manager role for the org in question.

> ### Note:  
> You automatically have the Org Manager role in a subaccount that you created.



<a name="loioa4eeaf179ee646b99558f27c0bae7b3e__steps_jrg_wt4_zl"/>

## Procedure

1.  Choose the subaccount that contains the org to which you'd like to add members.

2.  In the navigation area, choose *Cloud Foundry* \> *Org Members*.

    All members currently assigned to the org are shown in a list.

3.  Choose *Add Members*.

4.  Enter one or more e-mail addresses.

    You can use commas, spaces, semicolons, or line breaks to separate members.

5.  Feature Set A: Choose the *Origin*.

    If you want to use a custom user base, choose *Other* for *Origin* and then enter the corresponding Identity Authentication tenant name. For more information, see [Establish Trust and Federation of Custom Identity Providers for Platform Users in Multi-Environment Subaccounts \[Feature Set A\]](establish-trust-and-federation-of-custom-identity-providers-for-platform-users-in-multi-e-8600afb.md).

6.  Select the roles for the members and save your changes.




<a name="loioa4eeaf179ee646b99558f27c0bae7b3e__postreq_ocr_wj2_nbb"/>

## Next Steps

-   To select or unselect roles for a member, choose <span class="SAP-icons"></span> \(Edit\). The changes you make to the roles of a member take effect immediately.
-   To remove all the roles of a member, choose <span class="SAP-icons"></span> \(Delete\). This removes the member from the organization.

    > ### Note:  
    > You can only remove org members who are no longer assigned to any space in the org.


**Related Information**  


[Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

[Log On to Your Global Account](log-on-to-your-global-account-77be288.md "Use the SAP BTP cockpit to log on to your global account and start working in SAP BTP.")

[Navigate to Orgs and Spaces](navigate-to-orgs-and-spaces-5bf8735.md "To administer your Cloud Foundry environment, navigate to orgs, and spaces in the SAP BTP cockpit.")

