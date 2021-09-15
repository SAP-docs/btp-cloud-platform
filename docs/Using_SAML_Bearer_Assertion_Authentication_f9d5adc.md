<!-- loiof9d5adca9e414d9b8c42513a8890d782 -->

# Using SAML Bearer Assertion Authentication



<a name="loiof9d5adca9e414d9b8c42513a8890d782__prereq_kww_z2k_y3b"/>

## Prerequisites

You have configured single-sign on \(SSO\) with the Identity Authentication service. See [Configure Single Sign-On with the Identity Authentication Service](Configure_Single_Sign-On_with_the_Identity_Authentication_Service_8d3c376.md).



<a name="loiof9d5adca9e414d9b8c42513a8890d782__context_wm5_tss_scb"/>

## Context

To be able to use SAML Bearer Assertion authentication, you need to configure both SAP S/4HANA Cloud and SAP BTP sides.

**Related Information**  


[SAML Bearer Assertion Authentication](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e51e152ceaeb4b75affe5f15c65dfe6c.html)

 <a name="loiof9d5adca9e414d9b8c42513a8890d782 loio1c58ebce86514260a3b5be9fb9587745__loio1c58ebce86514260a3b5be9fb9587745"/>

<!-- loio1c58ebce86514260a3b5be9fb9587745 -->

# Upload Your Key-Pair Keystore in SAP BTP

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

 <a name="loiof9d5adca9e414d9b8c42513a8890d782 loio78d6b87a564c4f9d93d73e009aa2bd3f__loio78d6b87a564c4f9d93d73e009aa2bd3f"/>

<!-- loio78d6b87a564c4f9d93d73e009aa2bd3f -->

# Set Up SAP S/4HANA Cloud Side



<a name="loio78d6b87a564c4f9d93d73e009aa2bd3f__context_atn_wrs_scb"/>

## Context

From the SAP S/4HANA Cloud side you need to maintain the communication settings to configure the connectivity between SAP S/4HANA Cloud and SAP BTP.

> ### Note:  
> Make sure you have assigned the appropriate business catalogs to the propagated business users in the SAP S/4HANA Cloud tenant.



<a name="loio78d6b87a564c4f9d93d73e009aa2bd3f__steps_ovc_3pt_scb"/>

## Procedure

1.  Create a communication user. See [Maintain Communication Users](https://help.sap.com/viewer/f544846954f24b9183eddadcc41bdc3b/1808.500/en-US/eef80dda3867461c92ac1273689ed36f.html).

    For the SAML Bearer Assertion authentication, you need to provide a password when defining the required credentials.

2.  Create a communication system. See [Maintain Communication Systems](https://help.sap.com/viewer/f544846954f24b9183eddadcc41bdc3b/1808.500/en-US/15663c157670410ca366623dff329396.html).

    1.  Log into the SAP Fiori launchpad in the SAP S/4HANA Cloud system.

    2.  Select the *Communication Systems* tile.

    3.  Choose *New* to create a new system.

    4.  Enter a system ID and a system name.

    5.  Choose *Create*.

    6.  In the *Technical Data* section, in the *Host Name* field, enter the URL of the Cloud Foundry application or service required by your scenario or consult your scenario configuration guide.

        For example, the URL for an application deployed in SAP BTP in the Cloud Foundry environment is `https://*<application\_route\>*.cfapps.*<location\>*.hana.ondemand.com.` Where:

        -   The domain depends on your location, in the European region for example, the domain is *cfapps.eu10.hana.ondemand.com*
        -   The application route is the single point of entry of an application. To view the application route, you can use the `cf apps` or `cf routes` cf CLI command.
    7.  Enable the OAuth Identity Provider by checking the box under *OAuth 2.0 Identity Provider*.

    8.  Upload the public key contained in the keystore file you have have uploaded in your subaccount in SAP BTP. See [Upload Your Key-Pair Keystore in SAP BTP](Using_SAML_Bearer_Assertion_Authentication_f9d5adc.md#loio1c58ebce86514260a3b5be9fb9587745).

    9.  In the *Provider Name* field, enter a unique provider name. For example, you can enter the value of the CN field of your public key.

    10. Choose *+* \(Add\) under *User for Inbound Communication*.

    11. In the dialog box that appears, select *User Name and Password* from the *Authentication Method* drop-down list.

        The username corresponds to the communication user.

    12. Choose *OK* to confirm.

    13. Choose *Save*.

3.  Create a communication arrangement and select a communication scenario. See [Maintain Communication Arrangements](https://help.sap.com/viewer/f544846954f24b9183eddadcc41bdc3b/1808.500/en-US/fab3fd449cf74c6384622b98831e989e.html).

    > ### Note:  
    > When you have the communication arrangement created, choose *OAuth 2.0 Details.*. Copy and save locally the fields and their values. You will need them when setting up the destination in the SAP BTP cockpit.


 <a name="loiof9d5adca9e414d9b8c42513a8890d782 loiob5cd7da31eff4e6f82febecd5431ac48__loiob5cd7da31eff4e6f82febecd5431ac48"/>

<!-- loiob5cd7da31eff4e6f82febecd5431ac48 -->

# Set Up SAP BTP Side



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
        <th>

        Parameter


        
        </th>
        <th>

        Value


        
        </th>
        </tr>
        <tr>
        <td>

        `Name`


        
        </td>
        <td>

        Enter a meaningful name.


        
        </td>
        </tr>
        <tr>
        <td>

        `Type`


        
        </td>
        <td>

        ***HTTP***


        
        </td>
        </tr>
        <tr>
        <td>

        `Description`


        
        </td>
        <td>

        \(Optional\) Enter a meaningful description.


        
        </td>
        </tr>
        <tr>
        <td>

        `URL`


        
        </td>
        <td>

        The service URL from the communication arrangement.

        > ### Note:  
        > Make sure you use the HTTPS protocol.


        
        </td>
        </tr>
        <tr>
        <td>

        `Proxy Type`


        
        </td>
        <td>

        ***Internet***


        
        </td>
        </tr>
        <tr>
        <td>

        `Authentication`


        
        </td>
        <td>

        ***OAuth2SAMLBearerAssertion***


        
        </td>
        </tr>
        <tr>
        <td>

        `Key Store Location`


        
        </td>
        <td>

        In the dropdown list, select the key-pair keystore file you have uploaded in [Upload Your Key-Pair Keystore in SAP BTP](Using_SAML_Bearer_Assertion_Authentication_f9d5adc.md#loio1c58ebce86514260a3b5be9fb9587745).


        
        </td>
        </tr>
        <tr>
        <td>

        `Key Store Password`


        
        </td>
        <td>

        The password for the keystore.

        > ### Note:  
        > The pasword for the keystore must be the same as the one for the key pair entry in the keystore file.


        
        </td>
        </tr>
        <tr>
        <td>

        `Audience`


        
        </td>
        <td>

        The URL of your SAP S/4HANA Cloud account. To get it, log on to your SAP S/4HANA Cloud account. Select the profile picture and then choose *Settings* and copy the value from the *Server* field.

        > ### Note:  
        > Make sure you use the HTTPS protocol.


        
        </td>
        </tr>
        <tr>
        <td>

        `Client Key`


        
        </td>
        <td>

        The name of the communication user you have in the SAP S/4HANA Cloud tenant.


        
        </td>
        </tr>
        <tr>
        <td>

        `Token Service URL`


        
        </td>
        <td>

        This is the *Token Service URL* from the *OAuth 2.0 Details* in the communication arrangement. See [Set Up SAP S/4HANA Cloud Side](Using_SAML_Bearer_Assertion_Authentication_f9d5adc.md#loio78d6b87a564c4f9d93d73e009aa2bd3f), **step 3**.


        
        </td>
        </tr>
        <tr>
        <td>

        `Token Service User`


        
        </td>
        <td>

        The name of the communication user you have in the SAP S/4HANA Cloud tenant.


        
        </td>
        </tr>
        <tr>
        <td>

        `Token Service Password`


        
        </td>
        <td>

        The password for the communication user.


        
        </td>
        </tr>
        <tr>
        <td>

        `System User`


        
        </td>
        <td>

        This parameter is not used, leave the field empty.


        
        </td>
        </tr>
        </table>
        
    2.  Configure the required additional property. To do so, in the *Additional Properties* panel, choose *New Property*, and enter the following property:


        <table>
        <tr>
        <th>

        Parameter


        
        </th>
        <th>

        Value


        
        </th>
        </tr>
        <tr>
        <td>

        `authnContextClassRef`


        
        </td>
        <td>

         ***urn:oasis:names:tc:SAML:2.0:ac:classes:X509*** 


        
        </td>
        </tr>
        <tr>
        <td>

        `assertionIssuer`


        
        </td>
        <td>

        Issuer of the SAML assertion.

        Enter the provider name you have specified when creating the communication system in SAP S/4HANA Cloud. See [Set Up SAP S/4HANA Cloud Side](Using_SAML_Bearer_Assertion_Authentication_f9d5adc.md#loio78d6b87a564c4f9d93d73e009aa2bd3f).


        
        </td>
        </tr>
        </table>
        
    3.  Select the *Use default JDK truststore* checkbox.
4.  Save your entries.


**Related Information**  


[Consuming the Destination Service \(Cloud Foundry Environment\)](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/7e306250e08340f89d6c103e28840f30.html?q=destination%20service)

