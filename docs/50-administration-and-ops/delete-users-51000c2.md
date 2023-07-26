<!-- loio51000c2254864a39b9f8629715f2c5f1 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Delete Users

As an administrator, you can delete users from your subaccount. When you delete a user, you also delete the user's role collection assignments.



<a name="loio51000c2254864a39b9f8629715f2c5f1__prereq_kyb_mkt_bnb"/>

## Prerequisites

You have the required authorizations.

For more information, see [Security Administration: Managing Authentication and Authorization](security-administration-managing-authentication-and-authorization-1ff47b2.md) or [Role Collections and Roles in Global Accounts, Directories, and Subaccounts \[Feature Set B\]](../10-concepts/role-collections-and-roles-in-global-accounts-directories-and-subaccounts-feature-set-b-0039cf0.md).



<a name="loio51000c2254864a39b9f8629715f2c5f1__context_lny_4b5_bnb"/>

## Context

All users in the subaccounts of SAP BTP are shadow users. As an administrator, you might want to clean up users from your subaccount. Or for data protection and privacy reasons, it might be a legal obligation that administrators delete shadow users who belonged to employees who left the company. For more information, see [Working with Users](working-with-users-2c91f88.md).

It's also possible to delete users using APIs. For more information, see the related links.

Keep in mind that you also delete the user's role collection assignments.

> ### Remember:  
> When you delete a user at the Cloud Foundry level, SAP BTP doesn’t delete the corresponding shadow user at the subaccount level.
> 
> When you delete a user at the subaccount level, ensure that you delete the user at the Cloud Foundry level too. Otherwise, if the Cloud Foundry user logs on again, the system automatically creates the corresponding user at the subaccount level.
> 
> So ensure that you delete the shadow users on all levels.

> ### Caution:  
> You cannot undo the deletion of a user.



<a name="loio51000c2254864a39b9f8629715f2c5f1__steps_b4y_4b5_bnb"/>

## Procedure

1.  Open the SAP BTP cockpit.

2.  Go to your global account, directory, or subaccount \(see [Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md)\).

3.  Choose *Security* \> *Users*.

    > ### Note:  
    > For directories, choose *Users*. There is no *Security* menu item.

4.  Choose from the following options:


    <table>
    <tr>
    <th valign="top">

    Options


    
    </th>
    <th valign="top">

    Procedure


    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Delete a single user


    
    </td>
    <td valign="top">
    
    1.  Select the row of a user.

    2.  Choose :wastebasket:.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Delete multiple users


    
    </td>
    <td valign="top">
    
    1.  Choose <span class="SAP-icons"></span> Select multiple users and select users \(see the related link\).

    2.  Choose *Delete*.



    
    </td>
    </tr>
    </table>
    

**Related Information**  


[Working with Users](working-with-users-2c91f88.md "In the SAP BTP cockpit, you can see the users of your global account or subaccount, user-related identity provider information, and their authorizations. In a user's overview, you can create and delete users, and assign role collections. You can also display an overview of the role collections, where you can drill down all the way to the role, and see the application that the role is belongs to.")

[Deletion](../60-security/deletion-25e3cc6.md "The processing of personal data is subject to applicable laws related to the deletion of this data when the specified, explicit, and legitimate purpose for processing this personal data has expired. If there is no longer a legitimate purpose that requires the retention and use of personal data, it must be deleted.")

[Delete Shadow Users for Data Protection and Privacy Using APIs](../60-security/delete-shadow-users-for-data-protection-and-privacy-using-apis-eb70f16.md "Data privacy regulations or policies may require you to delete this data, for example, when the user has left your organization. To delete shadow users using APIs, set up access to the API and then use the SCIM REST APIs to retrieve and delete the users.")

