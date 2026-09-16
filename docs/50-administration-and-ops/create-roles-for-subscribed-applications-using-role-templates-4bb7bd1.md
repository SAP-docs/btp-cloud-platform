<!-- loio4bb7bd1804a8437287abff56f4956814 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Create Roles for Subscribed Applications Using Role Templates

Use the SAP BTP cockpit to create a role for a subscribed application using a role template. You can refine the role by assigning attributes and add the role to role collections.



<a name="loio4bb7bd1804a8437287abff56f4956814__context_hf3_qwf_r4b"/>

## Context

You can use role templates to create new roles. An SAP BTP cockpit wizard helps you configure new roles.

> ### Note:  
> You can only create roles from role templates that come with attributes.



<a name="loio4bb7bd1804a8437287abff56f4956814__steps_if3_qwf_r4b"/>

## Procedure

1.  Open the SAP BTP cockpit.

2.  Go to your subaccount \(see [Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md)\).

3.  In the navigation pane, choose *Services* \> ***Instances and Subscriptions*.

4.  To view your subscribed application, choose the *Subscriptions* tab.

5.  Choose <span class="SAP-icons-V5"></span> \(Actions\) next to your subscribed application, then choose *Manage Roles*.

    A complete list of all roles opens, sorted by the role template. The list also contains role names and role descriptions.

6.  Choose *Create*.

    The *Create Role* wizard opens.

7.  Enter a role name and description, then choose *Next*.

8.  Configure the attributes, then choose *Next*. Attributes further refine the role. For more information, see the related link.

9.  Select the available role collections for your new role, then choose *Next*.

10. Review your role configuration, then choose *Finish*.




## Next Steps

If needed, use :heavy_plus_sign: \(Add to role collection\) to add a role to a role collection.

**Related Information**  


[Attributes](attributes-713f52a.md "Attributes use information that is specific to the user, for example the user's country. If the application developer in the Cloud Foundry environment of SAP BTP has created a country attribute to a role, this restricts the data a business user can see based on this attribute.")

[Create Roles for Applications Using Existing Role Templates](create-roles-for-applications-using-existing-role-templates-2670fd2.md "Use the SAP BTP cockpit to create a role using an existing role template. You can refine the role by assigning attributes and add the role to role collections.")

