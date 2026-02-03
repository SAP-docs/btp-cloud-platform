<!-- loiof65e51a7203443efb58fe535c3d13e5f -->

# How to Create a New Business Role

Get an overview of how to create a new business role from scratch based on selected business catalogs.



<a name="loiof65e51a7203443efb58fe535c3d13e5f__HowToCreateBusinessRoleFromScratch_context"/>

## Context

You use business roles to control the access to your applications. To create a business role, you add one or multiple business catalogs to it. These predefined catalogs contain the actual authorizations that allow users to access apps and allow to define instance based restrictions where necessary. Business catalogs bundle authorizations for a specific business area. Once you have created a business role, you can assign it to multiple business users who perform similar business tasks.

> ### Note:  
> Please note that this document describes how to create a business role without a template. For more information on how to create a business role from a template, see the *Related information* section.



<a name="loiof65e51a7203443efb58fe535c3d13e5f__HowToCreateBusinessRoleFromScratch_steps"/>

## Procedure

1.  Open the *Maintain Business Roles* app.

2.  Choose *New*.

3.  Add general role details, such as business role name, ID and description.

4.  On the *Assigned Business Catalogs* tab, select *Add* to add the required business catalogs. Select the catalogs according to the business activities that the users with this role need to perform. Select *Apply*.

    > ### Note:  
    > Some business catalogs require additional dependent catalogs to be assigned to enable access to associated master data information \(for example, for business partners or customers\). These additionally required catalogs ensure access to all business objects used with the SAP Fiori apps of the main catalog. When you select the business catalogs you want to add to the business role and click *Add*, a list of dependent business catalogs is displayed. You can then select all the dependencies you want to add.

5.  By default, the value help and read access for each business catalog is set to unrestricted and there is no write access. If you want to change these restrictions, select *Maintain Restrictions*.

6.  Maintain instance-based restrictions for all required business objects \(following the requirements of your local authorization concept\).

7.  If required, click *Manage Launchpad Space* to create a new space or use an existing space. For more information, see the *Related information* section below.

8.  On the *Assigned Business Users* tab, you can assign the business users to your new business role. These users will receive the authorizations as defined in the business role.

9.  To activate the business role, save it.

    > ### Note:  
    > If you go back to the business roles overview **without saving** the business role, the business role will automatically be saved in a draft status. You can access it again and edit it from the business roles overview. Before saving the role, consider double-checking the following document [Best Practices for Business Roles](best-practices-for-business-roles-98f69bc.md).


**Related Information**  


[Step by Step: Create a New Space and Page for a Business Role](https://help.sap.com/viewer/4fc8d03390c342da8a60f8ee387bca1a/latest/en-US/ab05d9e086554a08af88d6482deb1bcb.html)

[How to Create a Business Role from a Template](how-to-create-a-business-role-from-a-template-ec310a8.md "Get an overview of how to create a business role from a template.")

