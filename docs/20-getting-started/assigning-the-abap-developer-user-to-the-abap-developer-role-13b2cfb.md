<!-- loio13b2cfb49c8046d8a031e137b6142127 -->

# Assigning the ABAP Developer User to the ABAP Developer Role

Add the developer user as business user to the ABAP instance.



You have created an employee record for the new developer user \(see [Creating an Employee Record for a New Developer](creating-an-employee-record-for-a-new-developer-a66fdc5.md)\).

> ### Caution:  
> The `SAP_BR_ADMINISTRATOR` role is pre-defined by SAP and only intended for the initial set-up of a system. Please create your own business roles based on the required business role template.

For information about creating a business role based on a development-related business catalog, see [Business Catalogs for Development Tasks](../50-administration-and-ops/business-catalogs-for-development-tasks-a9f4278.md).

1.  Log on to the administration launchpad of the ABAP environment as administrator \(see [Logging on to the Administration Launchpad of the ABAP Environment](logging-on-to-the-administration-launchpad-of-the-abap-environment-11e765e.md)\).
2.  On the SAP Fiori launchpad, choose the *Maintain Business Users* tile.
3.  Choose *New*.
4.  In the following dialog, choose the employee record of the new developer user from the list.
5.  Confirm the system message that you want to create a new user.
6.  On the *Assigned Business Roles* tab, choose *Add*.
7.  Select the checkbox for the ABAP developer role that you have created before \(see *Prerequisites*\).
8.  Choose *OK* and save your entries.

