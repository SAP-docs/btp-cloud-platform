<!-- loio6ed5101e19184d10942eb6eeb7190d57 -->

# Administrating User Assignments

The user assignment describes the relevant roles that a user requires to access SAP BTP ABAP environment using the Analyze Custom Code app.



## Context

You want to enable business users to access the Analyze Custom Code app.

For more information see, [How to Create a Business Role from a Template](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/ec310a8b669a45ca898dc4dd91d97de2.html).

> ### Note:  
> If you use `Prepare an Account for ABAP Development` booster, you can skip this step. The booster will perform this task.



## Procedure

1.  In the SAP Fiori launchpad, navigate to the *Identity and Access Management* section and open the `Maintain Business Roles` app.

2.  On the initial screen, select *Create from Template* from the bottom of the page.

    The *Create Business Role from Template* wizard is opened.

3.  Use the value help to choose *SAP\_BR\_IT\_PROJECT\_MANAGER* as the underlying *Template*.

4.  Enter *BR\_IT\_PROJECT\_MANAGER* as the name of the *New Business Role ID*.

5.  Enter a *New Business Role Description*.

6.  The checkbox *Create and Assign Spaces Based on SAP-Delivered Spaces* provides you with the following two options:

    1.  **Mark**the checkbox to create a new space for the Analyze Custom Code app in your subaccount. Define and enter a *New Space ID*.

    2.  **Unmark** the checkbox to use an existing space for the Analyze Custom Code app. Consequently, you must allocate the Analyze Custom Code app to the existing space and page in your subaccount. For more information, see [Working with Predefined Spaces and Pages](https://help.sap.com/viewer/4fc8d03390c342da8a60f8ee387bca1a/latest/en-US/2a8b991e64f84721ab6eb26398de7998.html).


7.  Confirm the creation with *OK*.

    The new business role is created and opened in the *Maintain Business Role* page.

8.  Select *Maintain Restrictions* from the title toolbar.

    The relevant subpage is opened.

9.  In the *Write, Read, Value Help* tab, choose *Unrestricted* from the drop-down list to enable write access for this business role.

10. Navigate back to the main page of your new business role.

11. Open the *Assigned Business Users* tab and add the relevant users using the *Search* field or the *Add* button.

12. *Save* the changes from the bottom.




## Results

The business role is created and added. The assigned users now have access to the Analyze Custom Code app.

