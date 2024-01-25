<!-- loioc2234acd55774ebcbedb66744199273e -->

# How to Create Communication Systems



<a name="loioc2234acd55774ebcbedb66744199273e__HowToCreateCommSystems_context"/>

## Context

To create a communication system perform the following steps:



<a name="loioc2234acd55774ebcbedb66744199273e__HowToCreateCommSystems_steps"/>

## Procedure

1.  On the initial screen of the *Communication Systems* app, select *New*.

2.  In the *New Communication System* dialog define an ID and a name of the new system.

3.  Fill in the required fields under:

    -   *General Data*

        Enter system ID and system name.

        *Contact Information*

        Enter name, email or phone number of a contact person.

    -   *Technical Data* 

        *General*

        If you want your communication system to be used for a communication arrangement based on a communication scenario that only contains inbound services, we recommend that you select the *Inbound Only* checkbox. If this checkbox is selected, the input fields that are only required for outbound communication disappear.

        If your communication system is intended for outbound communication, host, port, user and authentication method are used as specified in the destination service.

    -   *Destination Service* \(Only for Outbound Communication\)

        Because SAP BTP for the ABAP environment uses destination services of SAP BTP for outbound communication, you need to enter the name of the required destination service. For more information, see [Set Up the Destination Service](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/3fa7934f5a714bf88d8490958211382f.html). You also need to select the instance the destination service is based on. For more information, see [Creating the Service Instance for the ABAP Environment](https://help.sap.com/viewer/a96b1df8525f41f79484717368e30626/Cloud/en-US/50b32f144e184154987a06e4b55ce447.html).

        > ### Note:  
        > A predefined instance is selected by default. If you want to add your own instance, deselect this instance.

    -   *Cloud Connector* switch

        Indicates that SAP Cloud Platform Cloud Connector is used for communication with this system.

        *SSC Location ID*: Enter the SAP Cloud Platform Cloud Connector ID

        If your scenario is uses RFC modules, and SAP Cloud Platform Cloud Connector is not activated, the system uses WebSocket RFC. Therefore the remote system needs to support WebSocket RFC and you need to specify the client in the *RFC Settings* section.

    -   *RFC Settings*

        Define additional settings needed for RFC communication.

    -   *OAuth 2.0 Settings*

        Define additional settings if oAuth 2.0 is used for outbound communication.

        > ### Note:  
        > The propagation of technical users from the cloud application towards on-premise systems can be enabled in the *Communication Systems* app. To propagate the technical user, you have to select the *Cloud Conn. Technical User Propagation* checkbox in the *OAuth 2.0 Settings* area \(the checkbox is only active if the *Cloud Connector*switch is on\). This is similar to principal propagation, but in this case, a technical user is propagated instead of a business user.

    -   *OAuth 2.0 Identity Provider* switch

        Before you can authenticate and get an access token to access resources using an OAuth 2.0 client, you have to configure a trusted relationship to the required *SAML Identity Provider* \(token issuer\).

        Upload the signing certificate of the trusted provider and define the provider name.

        Define the *User ID Mapping Mode* if you don't use e-mail addresses, but either logon name or global user ID.

        The *User ID Mapping Mode* is required when the *SAML Identity Provider* is creating SAML assertions with the *NameIdentifierFormat* `unspecified`.

        This setting is ignored when then SAML assertion is using the *NameIdentifierFormat* `eMailAddress`.

        Please note that the required authorization for calling the service is granted to the business user and not to the technical user. When you set up a communication arrangement using oAuth, you can click *OAuth 2.0 Details*, select the scope and click *Granted by Business Catalogs* to find the necessary details. This way you can retrieve the business catalogs that are required for calling the service.

    -   *SAML Bearer Assertion Provider*

        Before you can authenticate using SAML2 Bearer assertions transmitted via the authorization header, you have to configure a trusted relationship to the required *SAML Identity Provider* \(token issuer\).

        Upload the signing certificate of the trusted provider and define the provider name.

        Define the required *User ID Mapping Mode* if it is unspecified and you don't use e-mail addresses, but either logon name or global user ID.

        The *User ID Mapping Mode* is required when the *SAML Identity Provider* is creating SAML assertions with the *NameIdentifierFormat* `unspecified` .

        This setting is ignored when then SAML assertion is using the *NameIdentifierFormat*`eMailAddress`.

    -   *OpenID Connect* switch

        Before you can authenticate using OpenID Connect, you have to configure a trusted *OpenID Connect Provider*.

        Define the required *User ID Mapping Mode*, the *OIDC Token Issuer* and *Client ID*. Click *Import Metadata*. This is necessary to ensure that the configuration is validated and complete.

        If the automatic configuration fails, you can configure the OpenID Connect settings manually. For more information, see *Manual Configuration - OpenID Connect \(OIDC\) Provider* in the *Related Information* section.

        > ### Note:  
        > You can select the *User Mapping Claim* to define the authorization attributes that are used by the identity provider. The default selection is *sub*.


4.  Add technical users for inbound communication. You can either select a user from the list or create a new user. If you decide to create a new user, you will be redirected to the *Maintain Communication User* app.

    > ### Note:  
    > Inbound users are communication users provided by your system and are used by the communication system to call the inbound services.

5.  Save the changes.

    You can now establish a communication arrangement with the created system. Use the *Communication Arrangements* app for this purpose.


**Related Information**  


[Communication Systems](communication-systems-15663c1.md "You can use this app to create communication systems. Communication systems are created to enable the communication among different systems.")

 <?sap-ot O2O class="- topic/link " href="fab3fd449cf74c6384622b98831e989e.xml" text="" desc="" xtrc="link:2" xtrf="file:/home/builder/src/dita-all/jjq1673438782153/loio2080d0faf9d84ce6aa14caa4caa32935_en-US/src/content/localization/en-us/c2234acd55774ebcbedb66744199273e.xml" output-class="" current-file="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 

[How to Create Communication Users](how-to-create-communication-users-0377ade.md "")

[Manual Configuration - OpenID Connect \(OIDC\) Provider](manual-configuration-openid-connect-oidc-provider-fa5e4a6.md "")

