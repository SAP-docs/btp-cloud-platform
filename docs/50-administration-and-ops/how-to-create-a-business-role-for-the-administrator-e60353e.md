<!-- copye60353e435df45b8ab753281102738c4 -->

# How to Create a Business Role for the Administrator

Get an overview of how to create a business role for the administrator if you haven't used the system before.



<a name="copye60353e435df45b8ab753281102738c4__HowToCreateBuisnessRolesForKeyUser_context"/>

## Context

If you as an administrator haven't used the Fiori apps before, you have to create an administrator business role first. Otherwise the app tiles are not visible on the Fiori Launchpad. With this role, you can create all other business roles according to the needs of your company.

> ### Caution:  
> The SAP\_BR\_ADMINISTRATOR role is pre-defined by SAP and only intended for the initial set-up of a system. Please create your own business roles based on the required business role template for productive use.

To create a business role for the administrator, proceed as follows:



### Process Steps

 ![](images/Create_Business_Role_for_the_Key_User_ef4396e.png) 



<a name="copye60353e435df45b8ab753281102738c4__HowToCreateBuisnessRolesForKeyUser_steps"/>

## Procedure

1.  Use the initial credentials that you have received separately e.g. via email, to log in to the system. On the SAP Fiori Launchpad select the tile *Maintain Business Roles* to open the app.

2.  Select *Create From Template*. The *Create Business Role from Template* window opens. In the field *Template*, search for `SAP_BR_ADMINISTRATOR`. Define the ID and the name of the new business role.

3.  A predelivered template contains a number of catalogs that in this case an administrator could need to perform tasks. These catalogs are displayed on the *Assigned Business Catalogs* tab. By default for each catalog the read access is unrestricted and there is no write access. If you want to change the restrictions, for example, to allow unrestricted write access for all catalogs, proceed as follows:

    1.  Select *Maintain Restrictions*.

    2.  On the new screen, select the restriction you would like to change.

        Under *Write*, select *Unrestricted*.

    3.  Select *Back to Main Page* to save the changes.


4.  On the *Assigned Business Users* tab, all users that are assigned to the selected catalogs are listed. To add a business user, proceed as follows:

    1.  Select *Add*.

    2.  In the *Add Business Users* window, search for your own business user and select *Apply*.


5.  Save the business role to activate it.

    > ### Note:  
    > If you go back to the business roles overview **without saving** the business role, the business role will automatically be saved in a draft status. You can access it again and edit it from the business roles overview.

    You can now log out from the system and log in with your own credentials and proceed creating further business roles according to the needs of your company


