<!-- loio05280a123d3044ae97457a25b3013918 -->

# Create a Subaccount

Create subaccounts in your global account using the SAP BTP cockpit.

 <a name="task_pdx_hmd_cqb"/>

<!-- task\_pdx\_hmd\_cqb -->

## Create a Subaccount \[Feature Set A\]



<a name="task_pdx_hmd_cqb__prereq_eds_lmd_cqb"/>

## Prerequisites

You are a global account administrator.

> ### Recommendation:  
> Before creating your subaccounts, we recommend you learn more about [Setting Up Your Account Model](https://help.sap.com/viewer/a04508c1a6b24e2fa0cbabc8b8e361ad/Internal/en-US/2db81f42f5194454beecde6cd4994dda.html "The hierarchical structure between global accounts, directories, and subaccounts lets you define an account model that accurately fits your business and development needs.") :arrow_upper_right:.



<a name="task_pdx_hmd_cqb__context_fds_lmd_cqb"/>

## Context

You create subaccounts in your global account. Once you create a new subaccount, you see a tile for it in the global account view, and you are automatically assigned to it as an administrator.



<a name="task_pdx_hmd_cqb__steps_gds_lmd_cqb"/>

## Procedure

1.  From your global account, choose *New Subaccount*.

2.  Specify a display name.

3.  Enter a description.

4.  Leave the *Neo Environment* checkbox deselected. This ensures that a multi-environment subaccount is created.

5.  Choose the desired infrastructure provider and region for your subaccount.

6.  Enter a subdomain for your subaccount. This will become part of the URL for accessing applications that you subscribe to from this subaccount.

    > ### Note:  
    > The subdomain can contain only letters, digits and hyphens \(not allowed in the beginning or at the end\), and must be unique across all subaccounts in the same region. Uppercase and lowercase letters can be used, however that alone does not qualify as a means to differentiate subdomains \(e.g. ***SUBDOMAIN*** and ***subdomain*** are considered to be the same\).
    > 
    > The subdomain can't be changed once you have created the subaccount.

7.  If your subaccount is to be used for production purposes, select the *Used for production* option.

    > ### Note:  
    > This does not change the configuration of your subaccount. Use this flag for your internal use to operate your production subaccounts in your global account and systems more efficiently. Your cloud operator may also use this flag to take appropriate action when handling incidents related to mission-critical accounts in production systems.
    > 
    > You can change your selection at any time by editing the subaccount properties. Do not select this option if your account is used for non-production purposes, such as development, testing, and demos.

8.  To use beta services and applications in the subaccount, select *Enable beta features*.

    > ### Caution:  
    > You shouldn't use SAP BTP beta features in subaccounts that belong to productive enterprise accounts. For more information, see [Important Disclaimers and Legal Information](https://help.sap.com/viewer/disclaimer).

    > ### Note:  
    > Once you have enabled this setting in a subaccount you cannot disable it.

9.  Save your changes.




<a name="task_pdx_hmd_cqb__result_hds_lmd_cqb"/>

## Results

A new tile appears in the global account page with the subaccount details.



<a name="task_pdx_hmd_cqb__postreq_ids_lmd_cqb"/>

## Next Steps

Once you've created your subaccount, navigate to it to enable the environment that you wish to use.

 <a name="task_dvg_gmd_cqb"/>

<!-- task\_dvg\_gmd\_cqb -->

## Create a Subaccount \[Feature Set B\]



<a name="task_dvg_gmd_cqb__prereq_qcg_tmd_cqb"/>

## Prerequisites

You are a global account administrator.

> ### Recommendation:  
> Before creating your subaccounts, we recommend you learn more about [Setting Up Your Account Model](https://help.sap.com/viewer/a04508c1a6b24e2fa0cbabc8b8e361ad/Internal/en-US/2db81f42f5194454beecde6cd4994dda.html "The hierarchical structure between global accounts, directories, and subaccounts lets you define an account model that accurately fits your business and development needs.") :arrow_upper_right:.



<a name="task_dvg_gmd_cqb__context_rcg_tmd_cqb"/>

## Context

You create subaccounts in your global account. Once you create a new subaccount, you see a tile for it in the global account view, and you are automatically assigned to it as an administrator.



<a name="task_dvg_gmd_cqb__steps_scg_tmd_cqb"/>

## Procedure

1.  From your global account, navigate to the *Account Explorer* page.

2.  Select *Create* \> *Subaccount*.

3.  Specify a display name.

4.  Enter a description.

5.  Enter a subdomain for your subaccount. This will become part of the URL for accessing applications that you subscribe to from this subaccount.

    > ### Note:  
    > The subdomain can contain up to 63 characters such as letters, digits and hyphens \(not allowed in the beginning or at the end\), and must be unique across all subaccounts in the same region. Uppercase and lowercase letters can be used, however that alone does not qualify as a means to differentiate subdomains \(e.g. ***SUBDOMAIN*** and ***subdomain*** are considered to be the same\).

6.  Choose the desired region for your subaccount.

7.  Select a parent for your subaccount. The parent can either be the global account or a directory.

8.  If your subaccount is to be used for production purposes, select the *Used for production* option.

    > ### Note:  
    > This does not change the configuration of your subaccount. Use this flag for your internal use to operate your production subaccounts in your global account and systems more efficiently. Your cloud operator may also use this flag to take appropriate action when handling incidents related to mission-critical accounts in production systems.
    > 
    > You can change your selection at any time by editing the subaccount properties. Do not select this option if your account is used for non-production purposes, such as development, testing, and demos.

9.  To use beta services and applications in the subaccount, under *Advanced*, select *Enable beta features*.

    > ### Caution:  
    > You shouldn't use SAP BTP beta features in subaccounts that belong to productive enterprise accounts. For more information, see [Important Disclaimers and Legal Information](https://help.sap.com/viewer/disclaimer).

    > ### Note:  
    > Once you have enabled this setting in a subaccount you cannot disable it.

10. Under *Advanced* \> *Labels*, assign labels to the subaccount to make organizing and filtering your subaccounts easier. For more information, see [Labels \[Feature Set B\]](../10-concepts/account-model-8ed4a70.md#loioe8663c08ead648faa673b0d63c5b478e).

    > ### Tip:  
    > -   When adding multiple values to a label, press [Enter\] after each value.
    > -   When you start typing, any matching label names and values that are already assigned to other subaccounts in your global account are offered as suggestions.

11. Save your changes.




<a name="task_dvg_gmd_cqb__result_tcg_tmd_cqb"/>

## Results

A new tile appears in the global account page with the subaccount details.



<a name="task_dvg_gmd_cqb__postreq_ucg_tmd_cqb"/>

## Next Steps

Once you've created your subaccount, navigate to it to enable the environment that you wish to use.

**Related Information**  


[Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

[Global Accounts](../10-concepts/account-model-8ed4a70.md#loioc165d95ee700407eb181770901caec94 "A global account is the realization of a contract you or your company has made with SAP.")

[Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md "Learn how to navigate to your global accounts and subaccounts in the SAP BTP cockpit.")

[Account Model](../10-concepts/account-model-8ed4a70.md#loio8ed4a705efa0431b910056c0acdbf377 "Learn more about the different types of accounts on SAP BTP and how they relate to each other.")

