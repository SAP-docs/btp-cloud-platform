<!-- loio0513c2e22fc54a398d4bc0a924cb865b -->

# Creating a Subaccount in the Global Account

A subaccount enables you to run applications and services in the global account of your ABAP environment.



<a name="loio0513c2e22fc54a398d4bc0a924cb865b__prereq_wx2_r1d_1kb"/>

## Prerequisites

You need SAP administrator permission to create subaccounts.



## Context

You want to establish an RFC connection to your on-premise system to be checked. To do this, you need to create a subaccount for the Cloud Foundry environment.

> ### Note:  
> If you use the `Prepare an Account for ABAP Development` booster, you can skip this step. The booster will perform this task.



## Procedure

1.  As an SAP administrator, select the *Global Accounts* navigation pane and open the relevant global account in the *SAP BTP Cockpit*.

2.  Select the *Subaccounts* navigation pane.

3.  Choose the *New Subaccount* button from the header toolbar to create a new subaccount in the Cloud Foundry environment.

4.  In the dialog, enter the following data:

    1.  Define and enter a *Display Name*.

    2.  \[Optional:\] Provide a *Description*.

    3.  Make sure that the *Neo* checkbox is unmarked.

    4.  Choose the *Provider* and *Region* of your system connection.

    5.  Define and enter the *Subdomain* to use a custom domain for your company.

    6.  \[Optional:\] If required, choose the following checkboxes:

        -   *Use for production*

        -   *Enable beta features*



5.  Choose *Create*.

    The subaccount will be created and added to your subaccounts. This will take a few moments.

6.  Open the subaccount you just created.

7.  In the *Cloud Foundry* tile, choose *Enable Cloud Foundry*.

8.  Choose *Create*.




<a name="loio0513c2e22fc54a398d4bc0a924cb865b__result_xfv_4w3_1kb"/>

## Results

The new subaccount for the `Cloud Foundry` environment appears in the global account page and displays the details.

This subaccount enables you to connect your cloud connector, which contains the RFC connection\(s\), to your on-premise system\(s\).

