<!-- loio0874895f1f78459f9517da55a11ffebd -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Navigate in the Cockpit

Learn how to navigate to your global accounts and subaccounts in the SAP BTP cockpit.



<a name="loio0874895f1f78459f9517da55a11ffebd__prereq_uww_m2c_nbb"/>

## Prerequisites

-   Sign up for an enterprise or a trial account and receive your logon data. For more information, see [Get a Trial Account](../20-getting-started/getting-a-global-account-d61c281.md#loio42e7e54590424e65969fced1acd47694) or [Sign up for a Customer Account](../20-getting-started/getting-a-global-account-d61c281.md#loioa71a081b39e343e097046bf487f57af3).




<a name="loio0874895f1f78459f9517da55a11ffebd__steps_hbw_vy2_knb"/>

## Procedure

1.  Find out which cloud management tools feature set your global account uses. For more information, see [Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md).

2.  Become familiar with the navigation behavior in the SAP BTP cockpit.

    -    [Navigate in the Cockpit to Global Accounts and Subaccounts \[Feature Set A\]](navigate-in-the-cockpit-0874895.md#loio0874895f1f78459f9517da55a11ffebd__Navigate-FSA) 

    -   [Navigate in the Cockpit to Global Accounts and Subaccounts \[Feature Set B\]](navigate-in-the-cockpit-0874895.md#loio0874895f1f78459f9517da55a11ffebd__Navigate-FSB)


**Related Information**  


[Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

 <a name="Navigate-FSA"/>

<!-- Navigate-FSA -->

## Navigate in the Cockpit to Global Accounts and Subaccounts \[Feature Set A\]



<a name="Navigate-FSA__steps_bhk_my2_knb"/>

## Procedure

1.  Navigate to a global account.

    You can see the following path in the breadcrumbs:

    <span class="SAP-icons"></span> Home / <span class="SAP-icons"></span> <global\_account\>

2.  Navigate to a subaccount.

    1.  Select the global account that contains the subaccount you'd like to navigate to by following the steps described above.

    2.  Select the subaccount.


    You can see the following path in the breadcrumbs:

    <span class="SAP-icons"></span> Home / <span class="SAP-icons"></span> <global\_account\> / <span class="SAP-icons"></span> <subaccount\>


 <a name="Navigate-FSB"/>

<!-- Navigate-FSB -->

## Navigate to Global Accounts, Directories, and Subaccounts \[Feature Set B\]



<a name="Navigate-FSB__steps_ibv_bhf_mqb"/>

## Procedure

1.  Navigate to a global account.

    -   **You have only one global account:**

        When you log on to the cockpit you’re automatically taken into your global account, to the *Account Explorer* page.

    -   **You have multiple global accounts:**

        When you log on to the cockpit, a dialog opens up containing the list of all global accounts that you’re part of. In this dialog, select the global account you want to navigate to.

        > ### Tip:  
        > If you have one global account you usually navigate to, you can choose *Remember my selection* in the initial dialog. This means you’ll be automatically redirected to your preferred global account after logging on, without seeing the dialog with all the options each time.
        > 
        > If you've chosen a default global account, you can change or remove it anytime. To do so, navigate to the *Account Explorer* page of any global account, choose *Switch Global Account*.
        > 
        > To change it, choose the desired new default global account from the list, select *Save new selection as default global account* and choose *Continue*. Your new default is savedand you’re redirected to that global account.
        > 
        > To delete the default global account and go back to seeing the selection dialog after each logon, simply choose the <span class="SAP-icons"></span> icon next to your default global account name in the dialog and choose *Close*.


    You can see which global account you are in at any time by looking at the first item in the breadcrumbs. It looks like this: <span class="SAP-icons"></span> *<global account name\>*

2.  Navigate to a different global account.

    -   Navigate to the *Account Explorer* page at global account level and choose *Switch Global Account*.

    -   Use the dropdown menu next to the <span class="SAP-icons"></span> *<global account name\>*.

3.  \(Optional\) Navigate to directories.

    1.  When you enter your global account, you are by default taken to the *Account Explorer* page of that global account. To navigate to a directory, choose the corresponding entry in one of the views in the *Directories & Subaccounts* tab.


4.  Navigate to subaccounts.

    1.  When you enter your global account, you are by default taken to the *Account Explorer* page of that global account. To navigate to a subaccount, choose the corresponding entry from one of the views.

        Once you've entered a subaccount, the breadcrumbs look like this: <span class="SAP-icons"></span> *<global account name\> /* <span class="SAP-icons"></span> *<subaccount name\>*



