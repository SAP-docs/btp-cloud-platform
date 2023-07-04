<!-- loio54d36ff122d64c59a10b803463d82f0b -->

# Using Client Certificate Authentication



## Context

To be able to use client certificate authentication, you need to configure both SAP S/4HANA Cloud and SAP BTP sides.

 <a name="loiod8e98a9d49b844479049208bf00593a1"/>

<!-- loiod8e98a9d49b844479049208bf00593a1 -->

## Set Up SAP S/4HANA Cloud Side



<a name="loiod8e98a9d49b844479049208bf00593a1__context_qrv_ljr_b2b"/>

## Context

To use client certificate authentication, you first start with creating and configuring the communication settings in the SAP S/4HANA Cloud tenant. To do that, you have to:



<a name="loiod8e98a9d49b844479049208bf00593a1__steps_rrv_ljr_b2b"/>

## Procedure

1.  Obtain a client certificate signed by a trusted certificate authority \(CA\) in *.pem* format.

    You can find a list of the trusted CA in the SAP S/4HANA Cloud tenant using the **Maintain Certificate Trust List** application. See [Maintain Certificate Trust List](https://help.sap.com/docs/SAP_S4HANA_CLOUD/55a7cb346519450cb9e6d21c1ecd6ec1/2b3c3f1e4007472883abe5226e84f05f.html).

2.  Create a communication user and upload the public key. See [Maintain Communication Users](https://help.sap.com/docs/SAP_S4HANA_CLOUD/55a7cb346519450cb9e6d21c1ecd6ec1/eef80dda3867461c92ac1273689ed36f.html).

3.  Create a communication system and add the communication user as *User for Inbound Communication* with an authentication method SSL Client Certificate.

    1.  Log into the SAP Fiori launchpad in the SAP S/4HANA Cloud system.

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


 <a name="loio311edbe5befa4e06b434c2130bc493b2"/>

<!-- loio311edbe5befa4e06b434c2130bc493b2 -->

## Set Up SAP BTP Side



<a name="loio311edbe5befa4e06b434c2130bc493b2__prereq_yhj_m5w_3bb"/>

## Prerequisites

You have logged into the SAP BTP cockpit from the SAP BTP landing page for your subaccount.



<a name="loio311edbe5befa4e06b434c2130bc493b2__steps_vhq_fww_3bb"/>

## Procedure

1.  In the cockpit, navigate to your subaccount.

2.  Choose *Connectivity* \> *Destinations* in the navigation panel.

3.  Choose *New Destination* and fill in the following properties:


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
    </table>
    
4.  \(Optional\) If you are using SAP Business Application Studio to develop your application, you have to specify another set of additional properties. See [What is SAP Business Application Studio](https://help.sap.com/products/SAP%20Business%20Application%20Studio/9d1db9835307451daa8c930fbd9ab264/8f46c6e6f86641cc900871c903761fd4.html?version=Cloud).

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
    
5.  Choose *Upload and Delete Certificate* link to upload your keystore. The keystore format .jks. When you finish uploading, choose *Close*.

    The keystore contains the key/pair signed by the trusted certificate authority \(CA\) in [Set Up SAP S/4HANA Cloud Side](using-client-certificate-authentication-54d36ff.md#loiod8e98a9d49b844479049208bf00593a1), **step 1**.

    1.  From the *Key Store Location* drop-down menu, select your keystore.

    2.  In the *Key Store Password*, enter the keystore password.


6.  Select the *Use default JDK truststore* checkbox.

7.  Save your entries.


**Related Information**  


[Managing Destinations](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/84e45e071c7646c88027fffc6a7bb787.html)

