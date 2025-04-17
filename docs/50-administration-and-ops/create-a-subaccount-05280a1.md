<!-- loio05280a123d3044ae97457a25b3013918 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Create a Subaccount

Create subaccounts in your global account using the SAP BTP cockpit.

<a name="task_dvg_gmd_cqb"/>

<!-- task\_dvg\_gmd\_cqb -->

## Create a Subaccount



<a name="task_dvg_gmd_cqb__prereq_qcg_tmd_cqb"/>

## Prerequisites

You are a global account administrator.

> ### Note:  
> If you are creating a subaccount in an entitlement-managed or user-managed directory, then you must be either a global account administrator or a directory administrator. See [Configure Entitlements and Quotas for Directories](configure-entitlements-and-quotas-for-directories-37f8871.md) and [Manage Users in Directories](manage-users-in-directories-ff4d4a4.md).

> ### Recommendation:  
> Before creating your subaccounts, we recommend you learn more about [Setting Up Your Account Model](https://help.sap.com/viewer/df50977d8bfa4c9a8a063ddb37113c43/Cloud/en-US/2db81f42f5194454beecde6cd4994dda.html "Learn how to set up your account model with global accounts and subaccounts, and how to use directories, spaces and namespaces to match your business and development needs.") :arrow_upper_right:.



<a name="task_dvg_gmd_cqb__context_rcg_tmd_cqb"/>

## Context

You create subaccounts in your global account. Once you create a new subaccount, you see a tile for it in the global account view, and you are automatically assigned to it as an administrator.



<a name="task_dvg_gmd_cqb__steps_scg_tmd_cqb"/>

## Procedure

1.  From your global account, navigate to the *Account Explorer* page.

2.  Select *Create* \> *Subaccount* to create a subaccount from scratch.

    > ### Tip:  
    > You can also create a subaccount from scratch by selecting *Create Subaccount* from the <span class="SAP-icons-V5"></span> \(Actions\) context menu of the global account or a directory.

    > ### Tip:  
    > Alternatively, you can create a new subaccount from an existing subaccount. For more information, see the [Create a Subaccount from an Existing Subaccount](https://help.sap.com/docs/btp/sap-business-technology-platform/create-subaccount?version=Cloud#create-a-subaccount-from-an-existing-subaccount) procedure below.

3.  Specify a display name.

4.  **Optional:** Enter a description.

5.  Enter a subdomain for your subaccount. This will become part of the URL for accessing applications that you subscribe to from this subaccount.

    > ### Note:  
    > The subdomain can contain up to 63 characters such as letters, digits and hyphens \(not allowed in the beginning or at the end\), and must be unique across all subaccounts in the same region. Uppercase and lowercase letters can be used, however that alone does not qualify as a means to differentiate subdomains \(e.g. `SUBDOMAIN` and `subdomain` are considered to be the same\).

6.  Choose the desired region for your subaccount.

7.  Select a parent for your subaccount. The parent can either be the global account or a directory.

8.  If your subaccount is to be used for production purposes, select the *Used for production* option.

    > ### Note:  
    > This does not change the configuration of your subaccount. Use this flag for your internal use to operate your production subaccounts in your global account and systems more efficiently. Your cloud operator may also use this flag to take appropriate action when handling incidents related to mission-critical accounts in production systems.
    > 
    > You can change your selection at any time by editing the subaccount properties. Do not select this option if your account is used for non-production purposes, such as development, testing, and demos.

9.  **Optional:** To use beta services and applications in the current subaccount, under *Advanced*, select *Enable beta features*.

    > ### Caution:  
    > You shouldn't use SAP BTP beta features in subaccounts that belong to productive enterprise accounts. For more information, see [Important Disclaimers and Legal Information](https://help.sap.com/viewer/disclaimer).

    > ### Note:  
    > Once you have enabled this setting in a subaccount you cannot disable it.

10. **Optional:** Under *Advanced* \> *Labels*, assign labels to the subaccount to make organizing and filtering your subaccounts easier. For more information, see [Labels](../10-concepts/account-model-8ed4a70.md#loioe8663c08ead648faa673b0d63c5b478e).

    > ### Tip:  
    > -   When adding multiple values to a label, press [Enter\] after each value.
    > -   When you start typing, any matching label names and values that are already assigned to other subaccounts in your global account are offered as suggestions.

11. Save your changes.




<a name="task_dvg_gmd_cqb__postreq_ucg_tmd_cqb"/>

## Next Steps

Once your new subaccount is set up, navigate to it to enable the environment that you wish to use and add users.

<a name="task_ltb_jzk_5bc"/>

<!-- task\_ltb\_jzk\_5bc -->

## Create a Subaccount from an Existing Subaccount



<a name="task_ltb_jzk_5bc__prereq_cml_mzk_5bc"/>

## Prerequisites

You are a global account administrator.



<a name="task_ltb_jzk_5bc__context_gml_mzk_5bc"/>

## Context

Instead of creating a subaccount from scratch, you can create one from an existing subaccount that is similar to the one you want to create. This saves you valuable time since all the properties, labels, and service plan assignments are copied from the existing subaccount to the new subaccount.

> ### Note:  
> This option is available only on the AWS, Azure, or GCP region.



<a name="task_ltb_jzk_5bc__steps_jml_mzk_5bc"/>

## Procedure

1.  From your global account, navigate to the *Account Explorer* page.

2.  Do one of the following:

    -   Select *Create* \> *Create from Existing Subaccount* and then choose the source subaccount.

    -   Locate the source subaccount in your account hierarchy and then choose *Create as New Subaccount* option in its <span class="SAP-icons-V5"></span> \(Actions\)context menu.


3.  Edit the new subaccount's properties and labels, as needed.

    Refer to [Create a Subaccount](https://help.sap.com/docs/btp/sap-business-technology-platform/create-subaccount?version=Cloud#create-a-subaccount) above to find out more information about the various subaccount properties.

4.  **Optional:** If you don't want all the assigned service plans in the selected subaccount to be copied to the new subaccount, turn off the *Copy service plan assignments* option.

5.  Click *Create*.

    > ### Note:  
    > If you selected the option to copy the assigned service plans from the source subaccount to your new subaccount, and any of the required plans are missing in the target location of the new subaccount, or if there is insufficient quota, you'll be informed before the subaccount creation process begins so that you or another global account admin can make the necessary adjustments before you try again.




<a name="task_ltb_jzk_5bc__postreq_hnl_mzk_5bc"/>

## Next Steps

After the new subaccount has been created, you can complete its setup, including its authorization configuration, instances, subscriptions, and environment setups.

**Related Information**  


[Global Accounts](../10-concepts/account-model-8ed4a70.md#loioc165d95ee700407eb181770901caec94 "A global account is the realization of a contract you or your company has made with SAP.")

[Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md "Learn how to navigate to your global accounts, directories, and subaccounts in the SAP BTP cockpit.")

[Account Model](../10-concepts/account-model-8ed4a70.md#loio8ed4a705efa0431b910056c0acdbf377 "Learn more about the different types of accounts on SAP BTP and how they relate to each other.")

