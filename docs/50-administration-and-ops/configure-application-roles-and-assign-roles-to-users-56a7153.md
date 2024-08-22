<!-- loio56a71531fc154717bf221f9e293ba215 -->

# Configure Application Roles and Assign Roles to Users

View, create, and modify application roles and then assign users to these roles using the SAP BTP cockpit.



<a name="loio56a71531fc154717bf221f9e293ba215__prereq_mnq_jdl_3cb"/>

## Prerequisites

Your subaccount is subscribed to a multitenant application in the Cloud Foundry environment. See [Subscribe to Multitenant Applications Using the Cockpit](subscribe-to-multitenant-applications-using-the-cockpit-7a3e396.md).



<a name="loio56a71531fc154717bf221f9e293ba215__context_pff_3xn_s2b"/>

## Context

You can use any SAML 2.0 standard compliant identity provider. See [Trust and Federation with Identity Providers](trust-and-federation-with-identity-providers-cb1bc8f.md).

<a name="task_fqg_rdl_3cb"/>

<!-- task\_fqg\_rdl\_3cb -->

## View, Create, and Modify Application Roles



<a name="task_fqg_rdl_3cb__steps_abj_tdl_3cb"/>

## Procedure

1.  Navigate to your subaccount. For more information, see [Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md).

2.  In the navigation area, choose *Services* \> *Instances and Subscriptions*.

3.  Under the *Subscriptions* table, click on the row with the application for which you want to manage app roles to open its *Overview* page.

4.  Open the tab *Roles* to view, create, and modify the application roles.

    > ### Tip:  
    > You can also manage roles without opening the application overview page, by selecting the three dots at the end of the application row. Choose *Manage Roles* from the drop-down menu.


<a name="task_vvv_12l_3cb"/>

<!-- task\_vvv\_12l\_3cb -->

## Assign Users to Application Roles



<a name="task_vvv_12l_3cb__steps_oyn_c2l_3cb"/>

## Procedure

1.  Navigate to your subaccount. For more information, see [Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md).

2.  Choose *Security* \> *Roles Collections* in the navigation area and include the roles into the roles collection.

3.  Choose *Security* \> *Trust Configuration* and assign role collections to users.


**Related Information**  


[User and Member Management](../10-concepts/user-and-member-management-cc1c676.md "On SAP BTP, user management takes place at all levels from global account to environment.")

