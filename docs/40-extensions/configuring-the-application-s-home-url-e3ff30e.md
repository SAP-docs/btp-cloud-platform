<!-- loioe3ff30e5682d475bb38910f275876ab2 -->

# Configuring the Application's Home URL

You can configure the *Home URL* of an application in the administration console for Identity Authentication.



<a name="loioe3ff30e5682d475bb38910f275876ab2__context_rfp_q1x_k2b"/>

## Context

Home URL is the URL that the user is redirected to after being authenticated. Initially, the *Home URL* for an application is not configured in the administration console for Identity Authentication. Once the URL has been set, you can change it.

> ### Remember:  
> *Home URL* is necessary when you import new users in Identity Authentication. Identity Authentication needs to send activation e-mails to the new users and the home URL has to be mentioned in the e-mails. To access the application, the users have to activate their user accounts. For more information see [Importing or Updating SAP Cloud for Customer Users in Identity Authentication](importing-or-updating-sap-cloud-for-customer-users-in-identity-authentication-7c4ce35.md).

To configure the *Home URL*, proceed as follows:



<a name="loioe3ff30e5682d475bb38910f275876ab2__steps_ehc_fn2_sy"/>

## Procedure

1.  Access the tenant's administration console for Identity Authentication by using the console's URL.

    > ### Note:  
    > The URL has the `https://<tenant ID>.accounts.ondemand.com/admin` pattern.
    > 
    > *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation e-mail with a URL in it. This URL contains the *tenant ID*.

2.  Choose *Applications & Resources* \> *Applications* from the menu on the left.

    This operation opens a list of the applications.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you do not have a created application in your list, you can create one. For more information, see [Create a New Application](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/0d4b255051c74955a959146beee4bd8c.html).

4.  Select the *Home URL* anchor text.

    > ### Note:  
    > You get the Home URL from the SAP Cloud for Customer system:
    > 
    > -   Log on to your SAP Cloud for Customer system as an administrator.
    > 
    > -   Choose *ADMINISTRATOR* \> *Common Tasks* and then choose *Configure Single Sign-On*.
    > 
    > -   In the *Single Sign-On URL Handling* section, copy and save the URL from the *SSO URL* field. If this URL starts with uppercase *HTTPS* protocol, replace it with ***https***.

    -   If you are configuring the URL for the first time, type the address in the pop-up dialog that appears.

    -   If you are editing the URL, choose *Edit* from the list item, and type the new address in the pop-up dialog.

5.  Save your changes.

    Once the application has been updated, the system displays the message ***Application <name of application\> updated***.


