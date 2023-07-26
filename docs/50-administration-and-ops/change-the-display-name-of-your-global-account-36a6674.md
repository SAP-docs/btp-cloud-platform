<!-- loio36a6674cf7184907aca3f062f83588e8 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Change the Display Name of Your Global Account

Change the display name for the global account using the SAP BTP cockpit.



<a name="loio36a6674cf7184907aca3f062f83588e8__context_a3l_2rb_r1b"/>

## Context

> ### Tip:  
> To find out how to tell which cloud management tools feature set your global account uses, see [Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md).

<a name="task_af5_xsw_2qb"/>

<!-- task\_af5\_xsw\_2qb -->

## Changing the global account name \[Feature Set A\]



<a name="task_af5_xsw_2qb__prereq_sf1_vtw_2qb"/>

## Prerequisites

You are a member of the global account that you'd like to edit.



<a name="task_af5_xsw_2qb__context_tf1_vtw_2qb"/>

## Context

The overview of global accounts available to you is your starting point for viewing and changing global account details in the cockpit. To view or change the display name for a global account, trigger the intended action directly from the tile for the relevant global account.



<a name="task_af5_xsw_2qb__steps_uf1_vtw_2qb"/>

## Procedure

1.  Choose the global account for which you'd like to change the display name and choose ![](images/Edit_Icon_abfe424.png) on its tile.

    A new dialog shows up with the mandatory *Display Name* field that is to be changed.

2.  Enter the new human-readable name for the global account.

3.  Save your changes.


<a name="task_o14_g5w_2qb"/>

<!-- task\_o14\_g5w\_2qb -->

## Changing the global account name \[Feature Set B\]



<a name="task_o14_g5w_2qb__prereq_p14_g5w_2qb"/>

## Prerequisites

You are an admin of the global account that you'd like to edit.



<a name="task_o14_g5w_2qb__context_q14_g5w_2qb"/>

## Context

> ### Tip:  
> You can also change the account's display name using the SAP BTP command line interface \(btp CLI\) with the `btp update accounts/global-account` command. See [Account Administration Using the SAP BTP Command Line Interface \(btp CLI\)](account-administration-using-the-sap-btp-command-line-interface-btp-cli-7c6df2d.md).



<a name="task_o14_g5w_2qb__steps_r14_g5w_2qb"/>

## Procedure

1.  Open your global account in the SAP BTP cockpit.

2.  Navigate to the *Account Explorer* page.

3.  In the *Directories & Subaccounts* view, locate the first entry in your account structure, which is your global account, and click <span class="SAP-icons"></span> Actions. Then select *Edit*.

4.  In the *Edit Global Account* dialog box, enter the new human-readable name for the global account.

5.  Save your changes.


**Related Information**  


[Account Model](../10-concepts/account-model-8ed4a70.md#loio8ed4a705efa0431b910056c0acdbf377 "Learn more about the different types of accounts on SAP BTP and how they relate to each other.")

