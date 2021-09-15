<!-- loioec310a8b669a45ca898dc4dd91d97de2 -->

# How to Create a Business Role from a Template

Get an overview of how to create a business role from a template.



<a name="loioec310a8b669a45ca898dc4dd91d97de2__HowToCreateBusinessRoleFromTemplate_context"/>

## Context

Instead of creating a business role from scratch, you can also create it from a business role template. A business role template is defined by SAP to make it easier for you to find the business catalogs that might be relevant for the corresponding role in your company. Usually, the business role templates have a very broad job profile to show all options.

> ### Note:  
> SAP does not recommend using them in their full scope, as the business catalogs might even conflict from a business perspective. Instead, adjust them to the tasks of the role in your company by choosing only the relevant business catalogs.

If changes to the template were included in an upgrade, the *Business Role Templates* app informs you about these changes and how they affect your business roles. For more information, see *Business Role Templates* \(Related Information\).

When you create a role based on a template, as a default the read and value help access are unrestricted, and write access is not granted. You can change this and define for each field to which a catalog provides access what a user is allowed to see and to edit. This allows you to shape your business roles in a very detailed way. For example, you can create two roles that comprise the same catalogs, but role 1 is restricted to work with data for the US, and role 2 is restricted to work only with data for Germany.



### Process Steps

 ![](images/How_to_Create_a_Business_Role_from_a_Template_7d0a47f.png) 



<a name="loioec310a8b669a45ca898dc4dd91d97de2__HowToCreateBusinessRoleFromTemplate_steps"/>

## Procedure

1.  Select the tile of the Maintain Business Roles app on the SAP Fiori Launchpad to open the app. On the initial screen select *Create From Template*.

2.  Select the required template. Define the ID and the name of the new business role. If required, select *Create and Assign Launchpad Space Based on Space Template*and define the new space ID \(for more information, see [How to Create a Space and Page for a Business Role](https://help.sap.com/viewer/4fc8d03390c342da8a60f8ee387bca1a/latest/en-US/ab05d9e086554a08af88d6482deb1bcb.html)\). Click *OK*.

3.  A template already contains one or more business catalogs that will be assigned to. Adjust the displayed template to your requirements, for example, change the general role details, and add or delete catalogs.

4.  By default the value help and read access for each business catalog is set to unrestricted and there is no write access. If you want to change these restrictions, select *Maintain Restrictions*.

5.  Maintain instance-based restrictions for all required business objects \(following the requirements of your local authorization concept\).

6.  On the *Assigned Business Users* tab you can assign the business users to your new business role. These users will receive the authorizations as defined in the business role.

7.  Save the business role to activate it.

    > ### Note:  
    > If you go back to the business roles overview **without saving** the business role, the business role will automatically be saved in a draft status. You can access it again and edit it from the business roles overview.


**Related Information**  


[Business Role Templates](Business_Role_Templates_223dfd3.md "You can use this app to you get an overview of the business role templates delivered by SAP.")

