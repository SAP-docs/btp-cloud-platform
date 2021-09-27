<!-- loioc926d691d7144f7dba16f8e12ad81d28 -->

# How to Maintain Restrictions



<a name="loioc926d691d7144f7dba16f8e12ad81d28__HowToMaintainAccessResctrictions_context"/>

## Context

By maintaining restrictions you can define the subset of all existing business objects a user can view or edit when working with this business role. The access restrictions allow you to differentiate your business roles on a fine-granular level. When you specify for a business role that a certain object should not be visible or editable, this applies to all apps included in this role.

If you assign multiple business roles that contain the same business catalogs, but different access restrictions, all restrictions are aggregated to the business user.

Using the *Maintain Business Roles* app, you have the following options for maintaining restrictions:



<a name="loioc926d691d7144f7dba16f8e12ad81d28__HowToMaintainAccessResctrictions_steps"/>

## Procedure

-   On the *Maintain Restrictions* tab, you can maintain restrictions for business roles.

    The business catalog defines which access categories are available for maintaining and for which fields restriction values can be maintained. The following access categories can be available:

    -   *Value Help* \(value help access\)
    -   *Read, Value Help* \(read access\)
    -   *Write, Read, Value Help* \(write access\)
    The business role aggregates these restrictions.

    The available restriction fields represent the authorization-relevant attributes of the business objects that are used in a role and for which instanced based access restrictions for value help, read and write access can be granted \(for example for a particular sales area\).

    Please note that not all restriction fields support number ranges. You can display the information whether a restriction field supports number ranges in the *Display Restriction Types* app. For more information, see *Display Restriction Types* \(Related Information\).

    Depending on the required authorization concept for the business role, you can restrict data access for the following separately:

    -   *Value Help*
    -   *Read, Value Help*
    -   *Write, Read, Value Help*
    > ### Note:  
    > When you set an access category to *Restricted* and it is not included implicitly according to the rule above, you either need to maintain a particular field value or you need to grant unrestricted access for this restriction field.

-   **Value Help** 
-   You can define access restrictions for value helps that are used in a business role. Leaving fields empty will typically mean *No Access* for this restriction field.

    These value help restrictions will not influence the defined restrictions for read access.

    In the context of a business role, you can restrict the value help access, for example to business partners that belong to certain authorization groups.

-   **Read / Write** 
-   As a default, read access is unrestricted, and write access is not granted to business roles. You can add or remove restrictions or you can choose *Unrestricted \(‘\*’\)* in cases where you want to grant full access for a field.

    Switching the read or write access to *Restricted* allows you to define which data can be seen and edited by the users assigned to this business role.

-   In the *Restrictions and Values* section, you can define the instance-based restrictions for the desired restriction fields used for value helps.

    If you want to make clear that you have not maintained a field on purpose and not by accident, click *Not maintained*.




For example, you have created the business roles 1 and 2 that both include the business catalog A. In business role 1, you restricted the access rights for sales organization to A. In business role 2, you allowed to work with data for all sales organizations. The business user to whom you assign both roles will then have full access to the data for all sales organizations.

-   **Leading Restriction**

    For general organizational fields that are used in several different restriction types, you can define a restriction as leading. That means the value in this field is automatically passed on to other restriction types the field is used in as well.

    Select the required field under *Restriction and Values* \> *General* and click the pencil icon. In the dialog box that opens, select the values you want to define as leading and switch *Leading Restriction* on. These values are then automatically transferred to the other restriction types the field used in.

    You want to, for example, define that the values for the country templates for Austria and Switzerland are applied in all restriction types the *Company Code* field is used in. So you select the values *AU01* \(Country Template AU\) and *CH01* \(Country Template CH\) and switch*Leading Restriction* on. Then these values are automatically distributed to all occurrences of the *Company Code* field.


**Related Information**  


[Display Restriction Types](Display_Restriction_Types_9203905.md "You can use this app to display restriction types and their validity.")





