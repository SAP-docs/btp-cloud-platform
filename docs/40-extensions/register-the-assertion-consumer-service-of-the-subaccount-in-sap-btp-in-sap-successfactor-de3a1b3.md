<!-- loiode3a1b3d12fb449e9ff0a528db6ae4b4 -->

# Register the Assertion Consumer Service of the Subaccount in SAP BTP in SAP SuccessFactors

You need to register the assertion consumer service of the subaccount as an authorized assertion consumer service in Provisioning of SAP SuccessFactors.



<a name="loiode3a1b3d12fb449e9ff0a528db6ae4b4__prereq_zfz_3jn_npb"/>

## Prerequisites

[Configure SAP SuccessFactors as a Trusted Identity Provider in SAP BTP](configure-sap-successfactors-as-a-trusted-identity-provider-in-sap-btp-80a3fd1.md)



<a name="loiode3a1b3d12fb449e9ff0a528db6ae4b4__steps_qml_hpf_gdb"/>

## Procedure

1.  Download the service provider SAML metadata file from the SAP BTP cockpit.

    1.  Go to your subaccount and choose *Security* \> *Trust Configuration*.

    2.  Choose *SAML Metadata* to download an XML file that contains the SAML 2.0 metadata describing SAP BTP as a service provider.

    3.  Open the XML file in a text editor and copy the following values:

        -   The value of the `Location` attribute of the `AssertionConsumerService` element with the `HTTP-POST` binding of the XML file: this is the value of the Assertion Consumer Service.

        -   The value of the `Location` attribute of the `SingleLogoutService` element with the `HTTP-POST` binding of the XML file: this is the value of the logout URL.

        -   The value of the `EntityID` attribute of `EntityDescriptor` element of the XML file: this is the value of the Audience URL.



2.  Log in to SAP SuccessFactors Provisioning for your SAP SuccessFactors system using the following link:

    `https://<sap_successfactors_system>/provisioning_login`

    where `<sap_successfactors_system>` is the hostname of your SAP SuccessFactors system.

3.  Go to your company and choose *Authorized SP Assertion Consumer Service Settings* under the *Service Provider Settings* section.

4.  Choose *Add another Service Provider ACS* and fill in the following fields:


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
    
        This is the value of the `Location` attribute of the `AssertionConsumerService` element with the `HTTP-POST` binding you copied in **step 1**.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        *Logout URL*


    
    </td>
    <td valign="top">
    
        This is the value of the `Location` attribute of the `SingleLogoutService` element with the `HTTP-POST` binding you copied in **step 1**.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        *Audience Url*


    
    </td>
    <td valign="top">
    
        This is the value of the `EntityID` attribute of `EntityDescriptor` element you copied in **step 1** 


    
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
    
5.  Choose *Save*.


