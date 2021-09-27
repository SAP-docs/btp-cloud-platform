<!-- loio5e773f8cb2694eccac0026d89c0b997f -->

# Configuring the Extension Application Connectivity to SAP Cloud for Customer APIs

To set up the connectivity from a subaccount in SAP BTP to an SAP Cloud for Customer system, you need to create HTTP destinations in the SAP BTP cockpit. These destinations provide data communication via HTTP protocol.

You can use the SAML Bearer assertion flow for consuming OAuth-protected resources. Users are authenticated by using SAML against the configured trusted identity providers. The SAML assertion is then used to request an access token from an OAuth authorization server. This access token must be added as an Authorization header with value *Bearer <access token\>* in all HTTP requests to the OAuth-protected resources.

These are the steps you need to follow:

1.  [Configure OAuth Identity Provider in SAP Cloud for Customer](Configure_OAuth_Identity_Provider_in_SAP_Cloud_for_Customer_40d20a2.md)

2.  [Configure the OAuth Client for OData Access](Configure_the_OAuth_Client_for_OData_Access_2c9c02d.md)

3.  [Create and Configure the HTTP Destination](Create_and_Configure_the_HTTP_Destination_21e50d8.md)


-   **[Configure OAuth Identity Provider in SAP Cloud for Customer](Configure_OAuth_Identity_Provider_in_SAP_Cloud_for_Customer_40d20a2.md "You need to add the SAP BTP service provider
		as a trusted OAuth identity provider.")**  
You need to add the SAP BTP service provider as a trusted OAuth identity provider.
-   **[Configure the OAuth Client for OData Access](Configure_the_OAuth_Client_for_OData_Access_2c9c02d.md "In SAP Cloud for Customer, use this procedure to configure the OAuth
		client for OData access to SAP Cloud for
                            Customer OData
		APIs.")**  
In SAP Cloud for Customer, use this procedure to configure the OAuth client for OData access to SAP Cloud for Customer OData APIs.
-   **[Create and Configure the HTTP Destination](Create_and_Configure_the_HTTP_Destination_21e50d8.md "")**  


**Related Information**  


[Authentication for Java Resource Servers](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/5af489d4cfd54b0790a02e9f1425d57d.html)

[Consuming the Destination Service \(Cloud Foundry Environment\)](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/7e306250e08340f89d6c103e28840f30.html)

