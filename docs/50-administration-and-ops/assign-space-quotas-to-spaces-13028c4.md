<!-- loio13028c44698e4a1a919fd5f96e9c28a5 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Assign Space Quotas to Spaces

You can use the SAP BTP cockpit to assign space quotas to spaces.



<a name="loio13028c44698e4a1a919fd5f96e9c28a5__prereq_jjr_15b_dcb"/>

## Prerequisites

-   You have the Org Manager role for the org in which you want to create and assign a space quota.

-   You have at least one space quota. For more information, see [Create Space Quotas](create-space-quotas-b13c4a2.md).




<a name="loio13028c44698e4a1a919fd5f96e9c28a5__steps_zrm_2mw_dzb"/>

## Procedure

1.  Navigate to the subaccount that contains the spaces to which you want to assign space quotas.

2.  In the navigation menu, choose *Cloud Foundry* \> *Space Quotas*.

3.  Open the *Quota Assignments* tab.

4.  Select one of the existing quota assignments and choose :pencil2: to make changes.

5.  Select either a specific *Space Quota* from the drop-down or the *Org Quota*.

    If you select *Org Quota*, the space will use the consumption limits defined in the org quota.

6.  To assign the selected space or org quota to the space, choose *Save*.


**Related Information**  


[Entitlements and Quotas](../10-concepts/entitlements-and-quotas-00aa2c2.md "When you purchase an enterprise account, you’re entitled to use a specific set of resources, such as the amount of memory that can be allocated to your applications.")

[Create Space Quotas Using the Cockpit](create-space-quotas-b13c4a2.md "You can use the SAP BTP cockpit to create space quotas.")

[Assign Quota Plans to Spaces Using the Cloud Foundry Command Line Interface](assign-quota-plans-to-spaces-using-the-cloud-foundry-command-line-interface-d1e4203.md "You use the Cloud Foundry Command Line Interface to assign the quotas available in your global account to your subaccounts.")

