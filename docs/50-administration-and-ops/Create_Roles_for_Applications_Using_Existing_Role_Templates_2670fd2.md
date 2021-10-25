<!-- loio2670fd27fc804ad99313385711d644f6 -->

# Create Roles for Applications Using Existing Role Templates

Use the SAP BTP cockpit to create a role using an existing role template. You can refine the role by assigning attributes and add the role to role collections.



## Context

You can use existing role templates to create new roles. A SAP BTP cockpit wizard helps you to configure new roles.



## Procedure

1.  Open the SAP BTP cockpit.

2.  Go to your global account and subaccount \(see [Navigate in the Cockpit](Navigate_in_the_Cockpit_0874895.md)\).

3.  Choose *Security* in the navigation pane.

4.  Choose *Roles*.

    Here you see a complete list of all existing roles sorted by application name. It also contains the role template, role names, and role description. On the right side, you find the action buttons.

5.  Choose *Add Using Same Role Template* in the row of the role template that you want to use.

    The *Create Role* wizard opens.

6.  Enter a role name and a description, and choose *Next*.

7.  Configure the attributes and choose *Next*. The attributes further refine the role. For more information, see the related link.

8.  Select the available role collections for your new role and choose *Next*.

9.  You can review your role configuration in the next window and complete the creation of the role by choosing *Finish*.


**Related Information**  


[Attributes](Attributes_713f52a.md "Attributes use information that is specific to the user, for example the user's country. If the application developer in the Cloud Foundry environment of SAP BTP has created a country attribute to a role, this restricts the data a business user can see based on this attribute.")

