<!-- loiodb1d0b4119d74dc6970adde9c85069b4 -->

# How to Maintain Business Users



<a name="loiodb1d0b4119d74dc6970adde9c85069b4__HowToMaintainBusinessUsers_context"/>

## Context

Business users are replicated from your central HR system. You can change user data \(for example, the user name\) and regional settings \(for example, the date and time format\).

   
  
**How users get access to SAP Fiori apps**

 ![](images/How_users_get_access_to_SAP_Fiori_apps_9ff1771.png "How users get access to SAP Fiori apps") 



<a name="loiodb1d0b4119d74dc6970adde9c85069b4__HowToMaintainBusinessUsers_steps"/>

## Procedure

**Creating New Business Users**

-   To create a new business user, proceed as follows:

    1.  Choose *Create* on the main screen of the app.

    2.  Select the employee you want to create the user for, and fill in the required fields.

        For *User Name*, enter a name or ID that is identical with the login name of the same user in the on-premise identity provider.

        The name the user enters to log on to the SAP Fiori launchpad. The user name can only contain uppercase letters, numbers, and underscores. It must have a maximum length of 40 characters and must not start with an underscore, or with SAP.



**Assigning Roles to Business Users**

-   To grant users access to applications, you assign the respective business roles to them.

    1.  Select the required user.

    2.  Click *Add Business Roles*.

    3.  Search for the required roles and select them.

    4.  Click *Apply* and *Save*.

        You can navigate from the Maintain Business Users app to the Maintain Business Roles app by choosing a business role ID in the list of assigned business roles.

        The user then sees the respective app tiles in the tile catalogs.



**Removing Role Assignments from Business Users**

-   To remove a role assignment from a user, proceed as follows:

    1.  Select the business user and then the assigned business role.

    2.  Choose *Remove* above the list or *Remove Business Roles* at the bottom of the screen.



**Updating User Role Assignments**

-   To update the assignments of roles to a user individually, edit the affected business user.

-   To mass update user role assignments, upload a `CSV` file.

    > ### Note:  
    > The CSV file needs to be UTF-8-encoded and must comply with the following pattern:
    > 
    > 
    > <table>
    > <tr>
    > <td valign="top">
    > 
    >  `User Name` 
    > 
    > 
    > 
    > </td>
    > <td valign="top">
    > 
    >  `User ID` \(Optional\)
    > 
    > 
    > 
    > </td>
    > <td valign="top">
    > 
    > `Role ID`
    > 
    > 
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    >  *<User name 1\>* 
    > 
    > 
    > 
    > </td>
    > <td valign="top">
    > 
    >  *<Business user ID 1\>* 
    > 
    > 
    > 
    > </td>
    > <td valign="top">
    > 
    > *<Business role ID 1\>*
    > 
    > 
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    >  *<User name 2\>* 
    > 
    > 
    > 
    > </td>
    > <td valign="top">
    > 
    >  *<Business user ID 2\>* 
    > 
    > 
    > 
    > </td>
    > <td valign="top">
    > 
    > *<Business role ID 2\>*
    > 
    > 
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    >  *<User name 3\>* 
    > 
    > 
    > 
    > </td>
    > <td valign="top">
    > 
    >  *<Business user ID 3\>* 
    > 
    > 
    > 
    > </td>
    > <td valign="top">
    > 
    > *<Business role ID 3\>*
    > 
    > 
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    >  *<User name n\>* 
    > 
    > 
    > 
    > </td>
    > <td valign="top">
    > 
    >  *<Business user ID n\>* 
    > 
    > 
    > 
    > </td>
    > <td valign="top">
    > 
    >  *<Business role ID n\>* 
    > 
    > 
    > 
    > </td>
    > </tr>
    > </table>
    > 
    > In the app, you are provided with a `CSV` template that you can download and use for filling in the user role assignments. When uploading the `CSV` file, you can decide if you want to add the role assignments to a user, or if you want to overwrite them completely.
    > 
    > You can find the CSV template as follows: Click the *Upload* button, then click *Upload User Role Assignments* in the menu that appears. This opens a dialog box containing the *Download CSV Template* link that you can use to download the template.

    The user ID is optional. Only if the user name is not unique, the user ID has to be maintained.


**Downloading User Lists**

-   To download a list of all users with an email address as `CSV` files for upload to *SAP Cloud Identity Services - Identity Authentication*, proceed as follows:

    1.  To open the file, you have to set the list separator to comma by setting the format in the regional settings of your operating system to*English \(United States\)*.

    2.  Open the *Administration Console for SAP Cloud Identity Services – Identity Authentication*.

    3.  To upload the `CSV` file, go to *User Management* \> *Import Users*.

        > ### Note:  
        > Make sure that the `CSV` file is not opened with any program before the upload.



Changing the Default Settings for a Business User

To change the default settings for a business user, select it for editing and adjust the values as required.

If you create a new business user, the following fields in the *User Data* area and the *Regional Settings* area are automatically filled with default values. You can adjust them if necessary.

**Default Values**


<table>
<tr>
<th valign="top">

Field



</th>
<th valign="top">

Default Value



</th>
</tr>
<tr>
<td valign="top">

*Valid From*



</td>
<td valign="top">

01/01/1901



</td>
</tr>
<tr>
<td valign="top">

*Valid To*



</td>
<td valign="top">

12/31/9999



</td>
</tr>
<tr>
<td valign="top">

*Decimal Format*



</td>
<td valign="top" rowspan="5">

This default value is derived from the standard setting that is valid in the country of the workplace address. If the workplace address is not maintained, the value is derived from the business user’s private address.



</td>
</tr>
<tr>
<td valign="top">

*Date Format*



</td>
</tr>
<tr>
<td valign="top">

*Time Format*



</td>
</tr>
<tr>
<td valign="top">

*Time Zone*



</td>
</tr>
<tr>
<td valign="top">

*Language*



</td>
</tr>
</table>

-   
**Related Information**  


[Defaulting of User Attributes](https://launchpad.support.sap.com/#/notes/3089625)

