<!-- loiof9d5adca9e414d9b8c42513a8890d782 -->

# Using SAML Bearer Assertion Authentication



<a name="loiof9d5adca9e414d9b8c42513a8890d782__prereq_kww_z2k_y3b"/>

## Prerequisites

You have configured single-sign on \(SSO\) with the Identity Authentication service. See [Configure Single Sign-On with the Identity Authentication Service](configure-single-sign-on-with-the-identity-authentication-service-8d3c376.md).



<a name="loiof9d5adca9e414d9b8c42513a8890d782__context_wm5_tss_scb"/>

## Context

To be able to use SAML Bearer Assertion authentication, you need to configure both SAP S/4HANA Cloud and SAP BTP sides.

**Related Information**  


[SAML Bearer Assertion Authentication](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e51e152ceaeb4b75affe5f15c65dfe6c.html)

<a name="loio1c58ebce86514260a3b5be9fb9587745"/>

<!-- loio1c58ebce86514260a3b5be9fb9587745 -->

## Upload Your Key-Pair Keystore in SAP BTP

To use SAML Bearer Assertion authentication for the communication between your extension application and the SAP S/4HANA Cloud system, you first need to upload your key-pair keystore in SAP BTP on subaccount level.



<a name="loio1c58ebce86514260a3b5be9fb9587745__steps_cqs_bxb_b2b"/>

## Procedure

1.  In the SAP BTP cockpit, navigate to your extension subaccount in the Cloud Foundry environment.

2.  Choose *Connectivity* \> *Destinations*.

3.  Choose *Certificates* \> *Upload Certificate*.

4.  Browse to the keystore file.

    > ### Note:  
    > You can only use JKS, PFX and P12 files. The keystore file must contain exactly one key pair entry.

    The keystore file containing your key pair entry is added.


**Related Information**  


[Use Destination Certificates](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/df1bb55a526942b9bee78fea2ebb3162.html)

<a name="loio78d6b87a564c4f9d93d73e009aa2bd3f"/>

<!-- loio78d6b87a564c4f9d93d73e009aa2bd3f -->

## Set Up SAP S/4HANA Cloud Side



<a name="loio78d6b87a564c4f9d93d73e009aa2bd3f__context_atn_wrs_scb"/>

## Context

From the SAP S/4HANA Cloud side you need to maintain the communication settings to configure the connectivity between SAP S/4HANA Cloud and SAP BTP.

> ### Note:  
> Make sure you have assigned the appropriate business catalogs to the propagated business users in the SAP S/4HANA Cloud tenant.



<a name="loio78d6b87a564c4f9d93d73e009aa2bd3f__steps_ovc_3pt_scb"/>

## Procedure

1.  Create a communication user. See [Maintain Communication Users](https://help.sap.com/docs/SAP_S4HANA_CLOUD/55a7cb346519450cb9e6d21c1ecd6ec1/eef80dda3867461c92ac1273689ed36f.html).

    For the SAML Bearer Assertion authentication, you need to provide a password when defining the required credentials.

2.  Create a communication system. See [Maintain Communication Systems](https://help.sap.com/docs/SAP_S4HANA_CLOUD/55a7cb346519450cb9e6d21c1ecd6ec1/15663c157670410ca366623dff329396.html).

    1.  Log into the SAP Fiori launchpad in the SAP S/4HANA Cloud system.

    2.  Select the *Communication Systems* tile.

    3.  Choose *New* to create a new system.

    4.  Enter a system ID and a system name.

    5.  Choose *Create*.

    6.  In the *Technical Data* section, in the *Host Name* field, enter the URL of the Cloud Foundry application or service required by your scenario or consult your scenario configuration guide.

        For example, the URL for an application deployed in SAP BTP in the Cloud Foundry environment is <code>https://<i class="varname">&lt;application_route&gt;</i>.cfapps.<i class="varname">&lt;location&gt;</i>.hana.ondemand.com.</code> Where:

        -   The domain depends on your location, in the European region for example, the domain is *cfapps.eu10.hana.ondemand.com*
        -   The application route is the single point of entry of an application. To view the application route, you can use the `cf apps` or `cf routes` cf CLI command.

    7.  Enable the OAuth Identity Provider by checking the box under *OAuth 2.0 Identity Provider*.

    8.  Upload the public key contained in the keystore file you have have uploaded in your subaccount in SAP BTP. See [Upload Your Key-Pair Keystore in SAP BTP](using-saml-bearer-assertion-authentication-f9d5adc.md#loio1c58ebce86514260a3b5be9fb9587745).

    9.  In the *Provider Name* field, enter a unique provider name. For example, you can enter the value of the CN field of your public key.

    10. Choose *\+* \(Add\) under *User for Inbound Communication*.

    11. In the dialog box that appears, select *User Name and Password* from the *Authentication Method* drop-down list.

        The username corresponds to the communication user.

    12. Choose *OK* to confirm.

    13. Choose *Save*.


3.  Create a communication arrangement and select a communication scenario. See [Maintain Communication Arrangements](https://help.sap.com/docs/SAP_S4HANA_CLOUD/55a7cb346519450cb9e6d21c1ecd6ec1/fab3fd449cf74c6384622b98831e989e.html).

    > ### Note:  
    > When you have the communication arrangement created, choose *OAuth 2.0 Details.*. Copy and save locally the fields and their values. You will need them when setting up the destination in the SAP BTP cockpit.


<a name="loiob5cd7da31eff4e6f82febecd5431ac48"/>

<!-- loiob5cd7da31eff4e6f82febecd5431ac48 -->

## Set Up SAP BTP Side



<a name="loiob5cd7da31eff4e6f82febecd5431ac48__prereq_yhj_m5w_3bb"/>

## Prerequisites

You have logged into the SAP BTP cockpit from the SAP BTP landing page for your subaccount.



<a name="loiob5cd7da31eff4e6f82febecd5431ac48__steps_vhq_fww_3bb"/>

## Procedure

1.  In the cockpit, navigate to your subaccount.

2.  Choose *Connectivity* \> *Destinations* in the navigation panel.

3.  Create an HTTP destination.

    To enable principal propagation, create an *OAuth2SAMLBearerAssertion* HTTP destination and configure its settings as follows:

    1.  Configure the basic settings:


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

        > ### Note:  
        > Make sure you use the HTTPS protocol.


        
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
        
        `OAuth2SAMLBearerAssertion`
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `Key Store Location`
        
        </td>
        <td valign="top">
        
        In the dropdown list, select the key-pair keystore file you have uploaded in [Upload Your Key-Pair Keystore in SAP BTP](using-saml-bearer-assertion-authentication-f9d5adc.md#loio1c58ebce86514260a3b5be9fb9587745).
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `Key Store Password`
        
        </td>
        <td valign="top">
        
        The password for the keystore.

        > ### Note:  
        > The pasword for the keystore must be the same as the one for the key pair entry in the keystore file.


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `Audience`
        
        </td>
        <td valign="top">
        
        The URL of your SAP S/4HANA Cloud account. To get it, log on to your SAP S/4HANA Cloud account. Select the profile picture and then choose *Settings* and copy the value from the *Server* field.

        > ### Note:  
        > Make sure you use the HTTPS protocol.


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `Client Key`
        
        </td>
        <td valign="top">
        
        The name of the communication user you have in the SAP S/4HANA Cloud tenant.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `Token Service URL`
        
        </td>
        <td valign="top">
        
        This is the *Token Service URL* from the *OAuth 2.0 Details* in the communication arrangement. See [Set Up SAP S/4HANA Cloud Side](using-saml-bearer-assertion-authentication-f9d5adc.md#loio78d6b87a564c4f9d93d73e009aa2bd3f), **step 3**.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `Token Service User`
        
        </td>
        <td valign="top">
        
        The name of the communication user you have in the SAP S/4HANA Cloud tenant.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `Token Service Password`
        
        </td>
        <td valign="top">
        
        The password for the communication user.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `System User`
        
        </td>
        <td valign="top">
        
        This parameter is not used, leave the field empty.
        
        </td>
        </tr>
        </table>
        
    2.  Configure the required additional property. To do so, in the *Additional Properties* panel, choose *New Property*, and enter the following property:


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
        
        `authnContextClassRef`
        
        </td>
        <td valign="top">
        
        `urn:oasis:names:tc:SAML:2.0:ac:classes:X509` 
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `assertionIssuer`
        
        </td>
        <td valign="top">
        
        Issuer of the SAML assertion.

        Enter the provider name you have specified when creating the communication system in SAP S/4HANA Cloud. See [Set Up SAP S/4HANA Cloud Side](using-saml-bearer-assertion-authentication-f9d5adc.md#loio78d6b87a564c4f9d93d73e009aa2bd3f).
        
        </td>
        </tr>
        </table>
        
    3.  \(Optional\) If you are using SAP Business Application Studio to develop your application, you have to specify another set of additional properties. See [What is SAP Business Application Studio](https://help.sap.com/products/SAP%20Business%20Application%20Studio/9d1db9835307451daa8c930fbd9ab264/8f46c6e6f86641cc900871c903761fd4.html?version=Cloud).

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
        

    1.  Select the *Use default JDK truststore* checkbox.

4.  Save your entries.


**Related Information**  


[Consuming the Destination Service \(Cloud Foundry Environment\)](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/7e306250e08340f89d6c103e28840f30.html?q=destination%20service)

