<!-- loiof25f9108740442c3804370f2d88a9bdd -->

# Identity and Access Management

Identity and Access Management \(IAM\) enables you to control user access to apps and specify what business users can do and see in the apps.



The main elements of IAM are business catalogs, business roles, and business users. The IAM apps secure the access to your solution based on these elements. Please see *Business Roles, Business Catalogs, and Restrictions* in the *Related Information* section for a more detailed description of how these elements interrelate.

Access to business apps is controlled by a role-based authorization management. That means you assign roles to users and these roles provide access to certain business tasks.

You can also assign users to roles in the **Maintain Business Roles** app. The main purpose of the app though is to create and adapt business roles. You create business roles by combining pre-defined business catalogs that contain the actual authorizations that allow users to access apps for a specific business area. If necessary, you can change the restrictions for the access categories value help, read, and write on field level. Once you have created a business role, you can assign it to multiple business users who perform similar business tasks in the **Maintain Business Users** app. Business users are all persons that need access to your solution, such as employees or contractors.

As opposed to business users, technical users aren't persons, but rather services that are used to automate technical tasks in the system, for example, a communication user. The **Display Technical Users** app shows you what technical users are available in your solution.

> ### Note:  
> We recommend that you use the *Manage Business Role Changes After Upgrade* app as a starting point to carry out regular release activities. For more information, see *Manage Business Role Changes After Upgrade* in the *Related Information* section.

> ### Note:  
> To find out which business roles grant access to which apps, you can use the*IAM Information System* app. On the *Business Role - Application* tab, you can display all apps per business role as well as the corresponding business catalog IDs. If you select *Application* in the *Main Entity* dropdown list, you can search for apps and see which business roles and business catalogs provide access to them. For more information, see *IAM Information System* in the *Related Information* section.
> 
> If you don’t have access to the *IAM Information System* app, you can still find out which business catalogs grant access to which apps using the SAP Fiori Apps Reference Library. For more information, see SAP Note [2832524](https://me.sap.com/notes/2832524).



<a name="loiof25f9108740442c3804370f2d88a9bdd__section_IAM_Overview2"/>

## Component for Customer Incidents

If you need support or experience issues, please report an incident under component `BC-SRV-APS-IAM`.



<a name="loiof25f9108740442c3804370f2d88a9bdd__section_IAM_Overview3"/>

## Access to the Apps

To have access to these apps, your user needs to be assigned to a business role which contains one of the following business catalogs:

-   *Identity and Access Management*
-   *User Management*
-   *Role Management*
-   *Role Assignment*

For more information, see sections *Maintain Business Users* and *Business Catalogs for Identity and Access Management Apps* linked below or ask your administrator.

**Related Information**  


[Maintain Business Users](maintain-business-users-e40e710.md "You use this app to provide business users with access rights and to maintain business user settings.")

[Display Technical Users](display-technical-users-7fb79d7.md "This app shows all technical users that exist in the system. To call the app, log on to your SAP Fiori Launchpad and go to Identity and Access Management > Display Technical Users .")

[Business Catalogs](business-catalogs-dd0abf5.md "You use this app to display all available business catalogs.")

[IAM Information System](iam-information-system-82d17cf.md "With this app you can get an overview of business users in your system and what roles and restrictions are assigned to them.")

[Business Role Templates](business-role-templates-223dfd3.md "You can use this app to you get an overview of the business role templates delivered by SAP.")

[Business Catalogs for Identity and Access Management Apps](business-catalogs-for-identity-and-access-management-apps-9bbbfc7.md "Get an overview of available business role catalogs and their restrictions.")

[Maintain Deleted Business Users](maintain-deleted-business-users-a904bdd.md)

[Manage Business Role Changes After Upgrade](manage-business-role-changes-after-upgrade-2e2f201.md)

[IAM Key Figures](iam-key-figures-f249696.md)

[Display Authorization Trace](display-authorization-trace-79b3c9b.md)

[Display Restriction Types](display-restriction-types-9203905.md "You can use this app to display restriction types and their validity.")

[Maintain Business Roles](maintain-business-roles-365b0d6.md)

[Business Roles, Business Catalogs and Restrictions](business-roles-business-catalogs-and-restrictions-d45c96e.md "")

