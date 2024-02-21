<!-- loio54d36ff122d64c59a10b803463d82f0b -->

# Using Client Certificate Authentication



## Context

To be able to use client certificate authentication, you need to configure both SAP S/4HANA Cloud and SAP BTP sides.

<a name="loio311edbe5befa4e06b434c2130bc493b2"/>

<!-- loio311edbe5befa4e06b434c2130bc493b2 -->

## Set Up SAP BTP Side



<a name="loio311edbe5befa4e06b434c2130bc493b2__prereq_yhj_m5w_3bb"/>

## Prerequisites

You have logged into the SAP BTP cockpit from the SAP BTP landing page for your subaccount.



<a name="loio311edbe5befa4e06b434c2130bc493b2__steps_vhq_fww_3bb"/>

## Procedure

1.  In the SAP BTP cockpit, navigate to your extension subaccount in the Cloud Foundry environment.

2.  Choose *Connectivity* \> *Destinations*.

3.  Choose *Certificates* and then choose *Generate Certificate* to generate the certificate for this subaccount.

4.  In the *Generate new certificate* wizard:

    -   In the *Certificate File Name* field, enter a name for the certificate.

    -   In the *File Name Extension* dropdown menu, select the type of keystore you want to use, for example *PEM* or *p12*.

        > ### Note:  
        > If you use SAP Cloud SDK to develop a JavaScript application, check the supported keystore types at [SAP Cloud SDK: Keystore Configuration](https://sap.github.io/cloud-sdk/docs/js/guides/trust-and-keystores#keystore-configuration).

    -   \(Optional\) In the *Certificate Validity Time Unit* dropdown menu, select whether you want to set a validity for the certificate in days, months, or years.

    -   \(Optional\) In the *Certificate Validity Value* specify the validity of the certificate.

    -   \(Optional\) Select the *Enable automatic renewal* checkbox.

    -   Choose *Generate Certificate* and then choose *Cancel* to close the wizard.


5.  Choose *Connectivity* \> *Destinations* in the navigation panel.

6.  Choose *New Destination* and fill in the following properties:


    <table>
    <tr>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Value
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `Name`
    
    </td>
    <td valign="top">
    
    Enter a meaningful name.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Type`
    
    </td>
    <td valign="top">
    
    `HTTP`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Description`
    
    </td>
    <td valign="top">
    
    \(Optional\) Enter a meaningful description.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `URL`
    
    </td>
    <td valign="top">
    
    The service URL from the communication arrangement.

    Make sure you use the HTTPS protocol, otherwise the *ClientCertificateAuthentication* option would not appear in the *Authentication* doropdown list.

    For example, *https://yourSAPS4HANACloudTenant-api.s4hana.ondemand.com*.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Proxy Type`
    
    </td>
    <td valign="top">
    
    `Internet` 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Authentication`
    
    </td>
    <td valign="top">
    
    `ClientCertificateAuthentication`

    > ### Note:  
    > Once you have selected this option, the system displays the *Upload and Delete Certificate* link.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Key Store Location`
    
    </td>
    <td valign="top">
    
    Select the certificate you have generated in step 4 for the destinations in your subaccount in SAP BTP.
    
    </td>
    </tr>
    </table>
    
7.  Save the destination.

8.  \(Optional\) If you are using SAP Business Application Studio to develop your application, you have to specify another set of additional properties. See [What is SAP Business Application Studio](https://help.sap.com/products/SAP%20Business%20Application%20Studio/9d1db9835307451daa8c930fbd9ab264/8f46c6e6f86641cc900871c903761fd4.html?version=Cloud).

    In the *Additional Properties*, choose *New Property* to define the following properties related to the SAP Business Application Studio:


    <table>
    <tr>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Value
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `WebIDEUsage`
    
    </td>
    <td valign="top">
    
    Specify this property with value `odata_gen` to consume an OData service in your application.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `WebIDEEnabled`
    
    </td>
    <td valign="top">
    
    If your application does not run on Cloud Foundry, you have to establish a connection to an external system by setting this property to `true`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `HTML5.DynamicDestination`
    
    </td>
    <td valign="top">
    
    If your application does not run on Cloud Foundry, you have to establish a connection to an external system by setting this property to `true`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `product.name`
    
    </td>
    <td valign="top">
    
    `SAP S/4HANA Cloud`

    The type of the SAP System for which you create this HTTP destination.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `communicationScenarioID`
    
    </td>
    <td valign="top">
    
    The ID of the communication scenario.
    
    </td>
    </tr>
    </table>
    
9.  Choose *Export* to download the certificate you have generated and assigned to this destination.

10. Open the keystore file in an editor of your choice and extract the certificate chain from the keystore. For example:

    -   If you are using the *PEM* keystore type:
        1.  Decode the *.pem* file from Base64 format and create a new decoded *cert.pem* file.

        2.  Open the *cert.pem* file and delete the section between the lines *\-----BEGIN PRIVATE KEY-----* and *\-----END PRIVATE KEY-----* including these lines. Save the file.


    -   If you are using the *p12* keystore type:
        1.  Decode the *.p12* file from Base64 format and create a new decoded *keystore.p12* file. For example, for Unix operating systems, use the command: `cat <your-file>.p12 | base64 --decode > keystore.p12`.

        2.  Extract the certificate chain from the *keystore.p12* file and copy the result in a new *cert.pem* file. For example, for Unix operating systems, use the command: `openssl pkcs12 -info -in keystore.p12 -nokeys -out cert.pem`.

        3.  Open the *cert.pem* file and clean *bag* attributes.




**Related Information**  


[Managing Destinations](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/84e45e071c7646c88027fffc6a7bb787.html)

<a name="loiod8e98a9d49b844479049208bf00593a1"/>

<!-- loiod8e98a9d49b844479049208bf00593a1 -->

## Set Up SAP S/4HANA Cloud Side



<a name="loiod8e98a9d49b844479049208bf00593a1__context_qrv_ljr_b2b"/>

## Context

To use client certificate authentication, you proceed with creating and configuring the communication settings in the SAP S/4HANA Cloud tenant. To do that, you have to:



<a name="loiod8e98a9d49b844479049208bf00593a1__steps_rrv_ljr_b2b"/>

## Procedure

1.  Use the client certificate signed by a trusted certificate authority \(CA\) in *.pem* format you have generated in the [Set Up SAP BTP Side](using-client-certificate-authentication-54d36ff.md#loio311edbe5befa4e06b434c2130bc493b2) page.

2.  Create a communication user and upload the public key. See [Maintain Communication Users](https://help.sap.com/docs/SAP_S4HANA_CLOUD/55a7cb346519450cb9e6d21c1ecd6ec1/eef80dda3867461c92ac1273689ed36f.html).

3.  Create a communication system and add the communication user as *User for Inbound Communication* with an authentication method SSL Client Certificate.

    1.  Log in the SAP Fiori launchpad in the SAP S/4HANA Cloud system.

    2.  Select the *Communication Systems* tile.

    3.  Choose *New* to create a new system.

    4.  Enter a system ID and a system name.

    5.  Choose *Create*.

    6.  Enter information about SAP BTP in the *Technical Data* section.

    7.  Choose *\+* \(Add\) under *User for Inbound Communication*.

    8.  In the dialog box that appears, select *SSL Client Certificate* from the *Authentication Method* drop-down list.

        The username corresponds to the communication user.

    9.  Choose *OK* to confirm.

    10. Choose *Save*.


4.  Create a communication arrangement using an existing or create a new scenario that supports client certificate authentication. See [Maintain Communication Arrangements](https://help.sap.com/docs/SAP_S4HANA_CLOUD/55a7cb346519450cb9e6d21c1ecd6ec1/fab3fd449cf74c6384622b98831e989e.html).

    You can use the already created communication system. The settings in the *Inbound Communication* section are filled in automatically. Save the value from the *URL* field, you will need it when creating a destination in the subaccount in SAP BTP.

5.  Copy the URL of the newly created communication arrangement, and get back to the SAP BTP cockpit. Navigate to your extension subaccount in the Cloud Foundry environment. Choose *Connectivity* \> *Destinations* and find the destination you have created in the *Set Up SAP BTP Side* section. Make sure the URL you have set up in the destination is the same as the URL you have for the communication arrangement.


