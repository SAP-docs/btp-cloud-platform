<!-- loio7c4ce35dfeaf4bc295f6fbc211f195f8 -->

# Importing or Updating SAP Cloud for Customer Users in Identity Authentication

As a tenant administrator of the Identity Authentication, you can import new users or update existing ones for a specific application with a CSV file, and send activtation e-mails to the users that have not received activation e-mails for that application so far.



<a name="loio7c4ce35dfeaf4bc295f6fbc211f195f8__prereq_spt_qdx_k2b"/>

## Prerequisites

-   You are assigned the *Manage Applications* and *Manage Users* roles. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/86ee37423f8945a1898faff1e6308756.html).

-   You have configured the trust between Identity Authentication tenant and the SAP Cloud for Customer system. For more information see [Setting Up Trust Between Identity Authentication and SAP Cloud for Customer](setting-up-trust-between-identity-authentication-and-sap-cloud-for-customer-2903a3c.md).

    > ### Note:  
    > You need the metadata to configure the trust between the service provider and Identity Authentication, which is in the role of identity provider.




<a name="loio7c4ce35dfeaf4bc295f6fbc211f195f8__context_tpt_qdx_k2b"/>

## Context

By importing new users with a CSV file, you create user profiles without passwords in Identity Authentication. As a result, the users receive e-mails with instructions how to activate their user accounts. After the users set their passwords, they can log on to the application for which they were imported. Based on the user access configuration of the application, the users can log on to other applications connected with the tenant in Identity Authentication.

> ### Note:  
> When a new application is created in the Identity Authentication tenant, the default value for user access is internal and you have to keep it like this. If you decide to change the user access to private for your subaccount in SAP BTP or for the SAP Cloud for Customer system, you have to make sure you import the users into that application. For more details, see

In addition to the new user import, you can specify existing users in the imported CSV file. You thus define the users to be updated in Identity Authentication.

The CSV file contains these columns *status*, *loginName*, *mail*, *firstName*, *lastName*. These columns are mandatory and they must always have values.

The *status*, *loginName*, *mail* and *firstName* columns must be with a string value of up to 32 characters. The *lastName* column must be with a string value of up to 64 characters.

The names in the *mail* and *loginName* columns must be unique.

> ### Caution:  
> You cannot change the e-mail of an existing user.

The *status* column defines whether the user is still active in the system and is able to work with any tenant applications. When a user is deleted, it is rendered inactive.

> ### Example:  
> 
> <table>
> <tr>
> <th valign="top">
> 
> status
> 
> 
> 
> </th>
> <th valign="top">
> 
> loginName
> 
> 
> 
> </th>
> <th valign="top">
> 
> mail
> 
> 
> 
> </th>
> <th valign="top">
> 
> firstName
> 
> 
> 
> </th>
> <th valign="top">
> 
> lastName
> 
> 
> 
> </th>
> </tr>
> <tr>
> <td valign="top">
> 
> active
> 
> 
> 
> </td>
> <td valign="top">
> 
> EID00001
> 
> 
> 
> </td>
> <td valign="top">
> 
> michael.adams@example.com
> 
> 
> 
> </td>
> <td valign="top">
> 
> Michael
> 
> 
> 
> </td>
> <td valign="top">
> 
> Adams
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> active
> 
> 
> 
> </td>
> <td valign="top">
> 
> EID00002
> 
> 
> 
> </td>
> <td valign="top">
> 
> julie.armstrong@example.com
> 
> 
> 
> </td>
> <td valign="top">
> 
> Julie
> 
> 
> 
> </td>
> <td valign="top">
> 
> Armstrong
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> active
> 
> 
> 
> </td>
> <td valign="top">
> 
> EID00003
> 
> 
> 
> </td>
> <td valign="top">
> 
> donna.moore@example.com
> 
> 
> 
> </td>
> <td valign="top">
> 
> Donna
> 
> 
> 
> </td>
> <td valign="top">
> 
> Moore
> 
> 
> 
> </td>
> </tr>
> </table>

To import users for an application into Identity Authentication, and to send activation e-mails, proceed as follows:



<a name="loio7c4ce35dfeaf4bc295f6fbc211f195f8__steps_upt_qdx_k2b"/>

## Procedure

1.  Access the tenant's administration console for Identity Authentication by using the console's URL.

    > ### Note:  
    > The URL has the `https://<tenant ID>.subaccounts.ondemand.com/admin` pattern.
    > 
    > *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation e-mail with a URL in it. This URL contains the *tenant ID*.

2.  Choose the *Import Users* tile.

    This operation opens the *Import Users* page.

3.  Choose the application that you want to edit. This is the application you created in [Setting Up Trust Between Identity Authentication and SAP Cloud for Customer](setting-up-trust-between-identity-authentication-and-sap-cloud-for-customer-2903a3c.md).

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you do not have a created application in your list, you can create one. For more information, see [Setting Up Trust Between Identity Authentication and SAP Cloud for Customer](setting-up-trust-between-identity-authentication-and-sap-cloud-for-customer-2903a3c.md).

4.  Choose the *Browse...* button and specify the location of the CSV file.

    > ### Note:  
    > Use a file smaller than 100 KB and with an extension `.csv`. If your file is 100 KB or larger, you have to import the user information in iterations with smaller size files.

5.  Choose the *Import* button.

    If the operation is successful, the system displays the message ***Users imported or updated***.

6.  Choose the one of the following options:


    <table>
    <tr>
    <th valign="top">

    Option


    
    </th>
    <th valign="top">

    Description


    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
        **Do nothing**


    
    </td>
    <td valign="top">
    
        The users are imported or updated for the selected application, but they will not receive activation e-mails. The activation e-mails will be sent when you choose *Send E-Mails* \> *Send*.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        **Repeat steps 2 to 5**


    
    </td>
    <td valign="top">
    
        The users are imported or updated for the selected application, but they will not receive activation e-mails. The activation e-mails will be sent when you choose *Send E-Mails* \> *Send*.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        Choose *Send E-Mails* \> *Send*


    
    </td>
    <td valign="top">
    
        This will send activation e-mails to all users that are imported for the selected application, but have not received activation e-mails so far.

    > ### Note:  
    > The *Send* button is inactive if *Home URL* or SAML 2.0 configuration of the application is missing. You can only import users, but you cannot send activation emails.
    > 
    > You need the *Home URL* configured for the specific application to be able to send the activation e-mails to the imported new users. For more information, see [Configuring the Application's Home URL](configuring-the-application-s-home-url-e3ff30e.md).
    > 
    > To access the application, the users have to activate their user accounts by following the link they receive in the e-mails.


    
    </td>
    </tr>
    </table>
    

