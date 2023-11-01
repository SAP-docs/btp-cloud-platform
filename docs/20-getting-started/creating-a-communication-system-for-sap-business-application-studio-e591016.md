<!-- loioe591016bdb3e49ae9a3df236b6a8f904 -->

# Creating a Communication System for SAP Business Application Studio

Create a communication system to set up communication between your ABAP environment system and SAP Business Application Studio.



<a name="loioe591016bdb3e49ae9a3df236b6a8f904__steps_bbp_vvc_x4b"/>

## Procedure

1.  In the SAP BTP cockpit, download your subaccount-specific trust certificate by navigating to *Connectivity* \> *Destinations* \> *Download Trust*.

2.  In the SAP Fiori launchpad of your ABAP environment system, create a communication system by using the *Communication Systems* app. See [How to Create Communication Systems](https://help.sap.com/docs/btp/sap-business-technology-platform/how-to-create-communication-systems?version=Cloud).

3.  Navigate to section *General* \> *SAML Bearer Assertion Provider* and switch the toggle button to *ON*.

4.  Upload the *Signing Certificate* first and then enter the following data:

    > ### Note:  
    > The signing certificate is the trust certificate that you have downloaded from your destination.


    <table>
    <tr>
    <th valign="top">

    Field
    
    </th>
    <th valign="top">

    User Input
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    **User ID Mapping Mode**
    
    </td>
    <td valign="top">
    
    User Name
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **SAML Bearer Issuer**
    
    </td>
    <td valign="top">
    
    From the *Signing Certificate Subject*, copy the common name \(the string after *CN=*\) and paste it in the *SAML Bearer Issuer* field.
    
    </td>
    </tr>
    </table>
    

