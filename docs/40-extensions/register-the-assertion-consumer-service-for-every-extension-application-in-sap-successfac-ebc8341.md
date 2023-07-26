<!-- loioebc8341367a64fe3a5b187a4e2440608 -->

# Register the Assertion Consumer Service for Every Extension Application in SAP SuccessFactors



<a name="loioebc8341367a64fe3a5b187a4e2440608__prereq_zfz_3jn_npb"/>

## Prerequisites

> ### Note:  
> This procedure is required only if you use SAP BTP, Cloud Foundry environment.

1.  [Configure SAP SuccessFactors as a Trusted Identity Provider in SAP BTP](configure-sap-successfactors-as-a-trusted-identity-provider-in-sap-btp-80a3fd1.md)

2.  [Register the Assertion Consumer Service of the Subaccount in SAP BTP in SAP SuccessFactors](register-the-assertion-consumer-service-of-the-subaccount-in-sap-btp-in-sap-successfactor-de3a1b3.md)




<a name="loioebc8341367a64fe3a5b187a4e2440608__steps_qml_hpf_gdb"/>

## Procedure

1.  Log in to SAP SuccessFactors Provisioning for your SAP SuccessFactors system using the following link:

    `https://<sap_successfactors_system>/provisioning_login`

    where `<sap_successfactors_system>` is the hostname of your SAP SuccessFactors system.

2.  Go to your company and choose *Authorized SP Assertion Consumer Service Settings* under the *Service Provider Settings* section.

3.  Choose *Add another Service Provider ACS* and fill in the following fields:

    > ### Note:  
    > If you are using more than one application router for your extension applications in your subaccount, repeat this step for every application router.


    <table>
    <tr>
    <th valign="top">

    Field


    
    </th>
    <th valign="top">

    Value


    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *Assertion Consumer Service*


    
    </td>
    <td valign="top">
    
    This is the absolute URL that corresponds to the URL of the application router. See [Application Router](../30-development/application-router-01c5f9b.md).


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Logout URL*


    
    </td>
    <td valign="top">
    
    This is the absolute URL that corresponds to the URL of the application router with the appended value of the `logoutEndpoint` property. See [logout](../30-development/logout-2296b4d.md).

    > ### Note:  
    > Make sure that the value of the `logoutMethod` property is set to `GET` in the *xs-app.json* file.

    > ### Note:  
    > The `SameSite` attribute of the `Set-Cookie` HTTP response header needs to be set to `None` so that the cookies are sent in all responses to both first-party and cross-origin requests. You also need to set the cookie `Secure` attribute, because it requires a secure context/HTTPS. See [Environment Variables](../30-development/environment-variables-ba52705.md).


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Application Name*


    
    </td>
    <td valign="top">
    
    Select *SAP Business Technology Platform* from the drop-down list.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *SHA-256 Certificate*


    
    </td>
    <td valign="top">
    
    Select the checkbox if it is not automatically selected when specifying the *Application Name* value.


    
    </td>
    </tr>
    </table>
    
4.  Choose *Save*.


