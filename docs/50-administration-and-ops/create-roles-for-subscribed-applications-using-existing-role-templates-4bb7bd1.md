<!-- loio4bb7bd1804a8437287abff56f4956814 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Create Roles for Subscribed Applications Using Existing Role Templates

Use the SAP BTP cockpit to create a role for a subscribed application using an existing role template. You can refine the role by assigning attributes and add the role to role collections.



<a name="loio4bb7bd1804a8437287abff56f4956814__context_hf3_qwf_r4b"/>

## Context

You can use existing role templates to create new roles. An SAP BTP cockpit wizard helps you to configure new roles.

> ### Note:  
> You can only create roles from roles templates that come with attributes.



<a name="loio4bb7bd1804a8437287abff56f4956814__steps_if3_qwf_r4b"/>

## Procedure

1.  Open the SAP BTP cockpit.

2.  Go to your global account and subaccount \(see [Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md)\).

3.  Choose *Services* \> ***Instances and Subscriptions* in the navigation pane.

4.  To see your subscribed application, choose the *Subscriptions* tab.

5.  To get to the place where you can manage roles, choose the chevron next to your subscribed application.

    Here you see a complete list of all existing roles sorted by the role template. It also contains the role names and the role description. On the right side, you find the action buttons.

6.  To add more roles, choose *Create*.

    The *Create Role* wizard opens.

7.  Enter a role name and a description, and choose *Next*.

8.  Configure the attributes and choose *Next*. The attributes further refine the role. For more information, see the related link.

9.  Select the available role collections for your new role and choose *Next*.

10. You can review your role configuration in the next window and complete the creation of the role by choosing *Finish*.

11. \(Optional\) Use :heavy_plus_sign: \(Add to role collection\) to add a role to a role collection.


**Related Information**  


[Configure Application Roles and Assign Roles to Users](configure-application-roles-and-assign-roles-to-users-56a7153.md "View, create, and modify application roles and then assign users to these roles using the SAP BTP cockpit.")

[Attributes](attributes-713f52a.md "Attributes use information that is specific to the user, for example the user's country. If the application developer in the Cloud Foundry environment of SAP BTP has created a country attribute to a role, this restricts the data a business user can see based on this attribute.")

