<!-- loiob9f4b0dc967040c99c7c8268ce335cce -->

# Establishing Trust of Type OpenID Connect

If you want to use a custom identity provider, you must set up trust between the subaccount and the SAP Cloud Identity Services - Identity Authentication service.



## Context

> ### Note:  
> If you have run the booster *Prepare an Account for ABAP Development*, you can skip this step.

If you have custom identity provider, you can use a function in SAP BTP cockpit to set up trust between your subaccount and the Identity Authentication service for SAP BTP automatically. The trust configuration is of type *OpenID Connect*.

For more information, see [Establish Trust and Federation Between SAP Authorization and Trust Management Service and Identity Authentication](https://help.sap.com/docs/btp/sap-business-technology-platform/establish-trust-and-federation-between-uaa-and-identity-authentication?version=Cloud).



## Procedure

1.  In the SAP BTP cockpit, go to the subaccount for your ABAP system.

2.  From the navigation area, choose *Security* \> *Trust Configuration*.

3.  Choose *Establish Trust*.

4.  In the following popup, select a identity provider from the dropdown list.

    Only identity providers that are associated with your customer ID are shown.

5.  Choose *Establish Trust*.

    Trust of type *OpenID Connect* between your subaccount and the identity provider is generated.

6.  Log on to the Identity Authentication service.

7.  From the navigation area, choose *Applications & Resources* \> *Applications*.

8.  Search for the application that has been created as part of the trust setup.

    The name of the application has the format *SAP BTP subaccount *<Subaccount Name\>**, but you can change it if needed.

    > ### Note:  
    > Older application names have the format *XSUAA\_*<Subaccount Name\>*.*

9.  Verify that the subject name identifier matches the login\_attribute chosen during ABAP system provisioning.


    <table>
    <tr>
    <th valign="top">

    ABAP login\_attribute
    
    </th>
    <th valign="top">

    SAP Cloud Identity Services Subject Name Identifier
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    **email**
    
    </td>
    <td valign="top">
    
    email
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **user\_name**
    
    </td>
    <td valign="top">
    
    login name
    
    </td>
    </tr>
    </table>
    

