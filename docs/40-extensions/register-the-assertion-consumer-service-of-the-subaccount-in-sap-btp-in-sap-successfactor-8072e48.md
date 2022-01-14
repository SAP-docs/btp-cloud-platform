<!-- copy8072e4805398436ca7d957313bb2869c -->

# Register the Assertion Consumer Service of the Subaccount in SAP BTP in SAP SuccessFactors

You need to register the assertion consumer service of the subaccount in SAP BTP as an authorized assertion consumer service in Provisioning of SAP SuccessFactors.



<a name="copy8072e4805398436ca7d957313bb2869c__prereq_zfz_3jn_npb"/>

## Prerequisites

[Establish Trust Between SAP SuccessFactors and SAP BTP](establish-trust-between-sap-successfactors-and-sap-btp-80a3fd1.md)



<a name="copy8072e4805398436ca7d957313bb2869c__steps_qml_hpf_gdb"/>

## Procedure

1.  Download the service provider SAML metadata file from the SAP BTP cockpit.

    1.  Go to your subaccount and choose *Security* \> *Trust Configuration*.

    2.  Choose *SAML Metadata* to download an XML file that contains the SAML 2.0 metadata describing SAP BTP as a service provider.

    3.  Open the XML file in a text editor and copy the following values:

        -   The value of the `Location` attribute of the `AssertionConsumerService` element with the `HTTP-POST` binding of the XML file: this is the value of the Assertion Consumer Service.

        -   The value of the `Location` attribute of the `SingleLogoutService` element with the `HTTP-POST` binding of the XML file: this is the value of the logout URL.

        -   The value of the `EntityID` attribute of `EntityDescriptor` element of the XML file: this is the value of the Audience URL.



2.  In Provisioning of SAP SuccessFactors, go to your company and choose *Authorized SP Assertion Consumer Service Settings* under the *Service Provider Settings* section.

3.  Choose *Add another Service Provider ACS* and fill in the following fields:


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

    The assertion consumer service URL

    This is the value of the `Location` attribute of the `AssertionConsumerService` element with the `HTTP-POST` binding you copied in **step 1**.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *Logout URL*


    
    </td>
    <td valign="top">

    The logout URL

    This is the value of the `Location` attribute of the `SingleLogoutService` element with the `HTTP-POST` binding you copied in **step 1**.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *Audience Url*


    
    </td>
    <td valign="top">

    The audience URL

    This is the value of the `EntityID` attribute of `EntityDescriptor` element you copied in **step 1**


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *Application Name*


    
    </td>
    <td valign="top">

    Select the application name SAP Business Technology Platform from the drop-down list.

    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *SHA-256 Certificate*


    
    </td>
    <td valign="top">

    Select the checkbox, if you are using:

    -   SAP SuccessFactors, First Half 2021 Release or later

    -   The SHA-256 certificate for the identity provider `http://<sap_successfactors_system>/idp/samlmetadata?company=<company_id>&cert=sha2` as it has been set up when establishing the trust between SAP SuccessFactors and SAP BTP. See [Establish Trust Between SAP SuccessFactors and SAP BTP](establish-trust-between-sap-successfactors-and-sap-btp-80a3fd1.md).



    
    </td>
    </tr>
    </table>
    
4.  Choose *Save*.


