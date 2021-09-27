<!-- loioebc8341367a64fe3a5b187a4e2440608 -->

# Register the Assertion Consumer Service for Every Extension Application in SAP SuccessFactors



<a name="loioebc8341367a64fe3a5b187a4e2440608__prereq_zfz_3jn_npb"/>

## Prerequisites

> ### Note:  
> This procedure is required only if you use SAP BTP, Cloud Foundry environment.

1.  [Establish Trust Between SAP SuccessFactors and SAP BTP](Establish_Trust_Between_SAP_SuccessFactors_and_SAP_BTP_80a3fd1.md)

2.  [Register the Assertion Consumer Service of the Subaccount in SAP BTP in SAP SuccessFactors](Register_the_Assertion_Consumer_Service_of_the_Subaccount_in_SAP_BTP_in_SAP_SuccessFactors_de3a1b3.md)




<a name="loioebc8341367a64fe3a5b187a4e2440608__steps_qml_hpf_gdb"/>

## Procedure

1.  In Provisioning of SAP SuccessFactors, go to your company and choose *Authorized SP Assertion Consumer Service Settings* under the *Service Provider Settings* section.

2.  Choose *Add another Service Provider ACS* and fill in the following fields:

    > ### Note:  
    > If you are using more than one application router for your extension applications in your subaccount, repeat this step for every application router.


    <table>
    <tr>
    <th>

    Field


    
    </th>
    <th>

    Value


    
    </th>
    </tr>
    <tr>
    <td>

    ***Assertion Consumer Service***


    
    </td>
    <td>

    The assertion consumer service URL

    This is the absolute URL that corresponds to the URL of the application router. See [Application Router](../30-development/Application_Router_01c5f9b.md).


    
    </td>
    </tr>
    <tr>
    <td>

    ***Logout URL***


    
    </td>
    <td>

    The logout URL

    This is the absolute URL that corresponds to the URL of the application router with the appended value of the `logoutEndpoint` property. See [logout](../30-development/logout_2296b4d.md).

    > ### Note:  
    > The `SameSite` attribute of the `Set-Cookie` HTTP response header needs to be set to `None` so that the cookies are sent in all responses to both first-party and cross-origin requests. You also need to set the cookie `Secure` attribute, because it requires a secure context/HTTPS.


    
    </td>
    </tr>
    <tr>
    <td>

    ***SHA-256 Certificate***


    
    </td>
    <td>

    Select the checkbox, if you are using:

    -   SAP SuccessFactors, First Half 2021 Release or later

    -   The SHA-256 certificate for the identity provider `http://<sap_successfactors_system>/idp/samlmetadata?company=<company_id>&cert=sha2` as it has been set up when establishing the trust between SAP SuccessFactors and SAP BTP. See [Establish Trust Between SAP SuccessFactors and SAP BTP](Establish_Trust_Between_SAP_SuccessFactors_and_SAP_BTP_80a3fd1.md).


    
    </td>
    </tr>
    </table>
    
3.  Choose *Save*.


