<!-- loio096332dc230e413eac72b15fb0b0930f -->

# Exporting SAP Cloud for Customer Users

Use this procedure to export SAP Cloud for Customer users and save the user data in CSV format.



<a name="loio096332dc230e413eac72b15fb0b0930f__context_gfl_mdx_k2b"/>

## Context

You need to export the users from the SAP Cloud for Customer system, adapt the data and save it in CSV format so that you can import the data in the Identity Authentication tenant and thus allow your company employees to authenticate with their corporate credentials.

> ### Note:  
> It is mandatory to have an e-mail for every user that you replicate from the SAP Cloud for Customer system in your Identity Authentication tenant.
> 
> Although in the SAP Cloud for Customer system having an e-mail for a user is not obligatory, you need to have this e-mail as a parameter when you export the users and import them in your subaccount in SAP BTP.

The CSV file with the SAP Cloud for Customer user data must contain the following columns:

-   `status`

-   `loginName`
-   `mail`
-   `firstName`

-   `lastName`




<a name="loio096332dc230e413eac72b15fb0b0930f__steps_ofl_mdx_k2b"/>

## Procedure

1.  Log on to your SAP Cloud for Customer system as an administrator.

2.  Open the *Business Users* view. To do so, choose *ADMINISTRATOR* \> *GENERAL SETTINGS* \> *Business Users*.

3.  To export the users, choose *Export* \> *To Microsoft Excel®*.

    The system exports the users in a Microsoft Excel® spreadsheet. The spreadsheet contains the following columns: *User Locked*, *Password Locked*, *User ID*, *Name*, *Technical ID*. The spreadsheet does not contain a column with the user e-mails and the user status.

4.  Modify the spreadsheet as follows:

    1.  Remove the superfluous data and leave only the *User ID* and *Name* columns.

    2.  Rename the *User ID* column to `loginName` and split the *Name* column to `firstName` and `lastName`columns.

        The data in the *loginName* stays the same, while the names from the former *Name* columns are split in the following way: first names go to the *firstName* column and last names go to the *lastName* column.

    3.  Insert a new column before the *loginName* column and name it `status`. The status can be `active` or `inactive`.

    4.  Insert a new column between *loginName* and *firstName* and name it `mail`.

        Go to the SAP Cloud for Customer system. To get the e-mail of a user, select the user. The e-mail is displayed on the *General Data* tab page.

        > ### Note:  
        > -   The *status*, *loginName*, *mail* and *firstName* columns must be with a string value of up to 32 characters. The *lastName* column must be with a string value of up to 64 characters.
        > 
        > -   The names in the *mail* and *loginName* columns must be unique.
        > 
        > -   You cannot change the e-mail of an existing user.
        > 
        > -   The *status* column defines whether the user is still active in the system and is able to work with any tenant applications. When a user is deleted, it is rendered inactive.

    5.  Save the file in CSV format.

        After you have modified and saved your file, you should have a CSV file with the following columns and similar data.


        <table>
        <tr>
        <th valign="top">

        status


        
        </th>
        <th valign="top">

        loginName


        
        </th>
        <th valign="top">

        mail


        
        </th>
        <th valign="top">

        firstName


        
        </th>
        <th valign="top">

        lastName


        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
                active


        
        </td>
        <td valign="top">
        
                EID00001


        
        </td>
        <td valign="top">
        
                michael.adams@example.com


        
        </td>
        <td valign="top">
        
                Michael


        
        </td>
        <td valign="top">
        
                Adams


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
                active


        
        </td>
        <td valign="top">
        
                EID00002


        
        </td>
        <td valign="top">
        
                julie.armstrong@example.com


        
        </td>
        <td valign="top">
        
                Julie


        
        </td>
        <td valign="top">
        
                Armstrong


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
                active


        
        </td>
        <td valign="top">
        
                EID00003


        
        </td>
        <td valign="top">
        
                donna.moore@example.com


        
        </td>
        <td valign="top">
        
                Donna


        
        </td>
        <td valign="top">
        
                Moore


        
        </td>
        </tr>
        </table>
        


