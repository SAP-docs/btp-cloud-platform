<!-- loioef4b7caf3e95443a8f5bfb23c637f01a -->

# Configuring the Extension Application's Connectivity to SAP S/4HANA Cloud

Use this procedure to set up the connectivity between the extension application on SAP BTP and the SAP S/4HANA Cloud system.

To set up the connectivity from a subaccount in SAP BTP to an SAP S/4HANA Cloud tenant, you need to create HTTP destinations in the SAP BTP cockpit. These destinations provide data communication via HTTP protocol.

When creating an HTTP destination, you can use different authentication types for access control:



<a name="loioef4b7caf3e95443a8f5bfb23c637f01a__section_cqs_5tn_4cb"/>

## Basic Authentication

Using authentication method you need to provide username and password. When configuring the HTTP destination in the cockpit, the username and password must correspond to the communication user in the SAP S/4HANA Cloud tenant.

See [Using Basic Authentication](Using_Basic_Authentication_c573baf.md#loioc573bafd1f2c4282b26966647e46f309).



<a name="loioef4b7caf3e95443a8f5bfb23c637f01a__section_ny4_5tn_4cb"/>

## Client Certificate Authentication

> ### Note:  
> Available only for the manual configuration.

To configure a client certificate authentication, you need a client certificate signed by a trusted certificate authority \(CA\). You upload the public key when creating a communication user in the SAP S/4HANA Cloud tenant, and then, you add the corresponding keystore to the HTTP destination in the SAP BTP cockpit.

See [Using Client Certificate Authentication](Using_Client_Certificate_Authentication_54d36ff.md#loio54d36ff122d64c59a10b803463d82f0b).



<a name="loioef4b7caf3e95443a8f5bfb23c637f01a__section_nsq_stn_4cb"/>

## SAML Bearer Assertion Authentication

You can use the SAML Bearer assertion flow for consuming OAuth-protected resources. Users are authenticated by using SAML against the configured trusted identity providers. The SAML assertion is then used to request an access token from an OAuth authorization server. This access token must be added as an Authorization header with value *Bearer <access token\>* in all HTTP requests to the OAuth-protected resources.

See [Using SAML Bearer Assertion Authentication](Using_SAML_Bearer_Assertion_Authentication_f9d5adc.md#loiof9d5adca9e414d9b8c42513a8890d782).

-   **[Using Basic Authentication](Using_Basic_Authentication_c573baf.md#loioc573bafd1f2c4282b26966647e46f309 "")**  

-   **[Using Client Certificate Authentication](Using_Client_Certificate_Authentication_54d36ff.md#loio54d36ff122d64c59a10b803463d82f0b "")**  

-   **[Using SAML Bearer Assertion Authentication](Using_SAML_Bearer_Assertion_Authentication_f9d5adc.md#loiof9d5adca9e414d9b8c42513a8890d782 "")**  


**Related Information**  


[Authentication for Java Resource Servers](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/5af489d4cfd54b0790a02e9f1425d57d.html)

[Consuming the Destination Service \(Cloud Foundry Environment\)](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/7e306250e08340f89d6c103e28840f30.html)

