<!-- loio2c9c02d7d19748eea0d2482093f04278 -->

# Configure the OAuth Client for OData Access

In SAP Cloud for Customer, use this procedure to configure the OAuth client for OData access to SAP Cloud for Customer OData APIs.



<a name="loio2c9c02d7d19748eea0d2482093f04278__steps_e5f_ysd_l2b"/>

## Procedure

1.  Log on to your SAP Cloud for Customer system as an administrator. Go to *ADMINISTRATOR* \> *OAUTH2.0 CLIENT REGISTRATION*.

2.  Choose *New*.

3.  Specify a client secret, description, and token lifetime \(in seconds\). For example, 3600 seconds.

4.  In the *Issuer Name* field, use the dropdown list to specify the identity provider that you created in the document [Configure OAuth Identity Provider in SAP Cloud for Customer](Configure_OAuth_Identity_Provider_in_SAP_Cloud_for_Customer_40d20a2.md).

5.  Copy the entry in the *Client ID* field. You will need it later when creating the HTTP destination with OAuth authentication required for the connectivity to the SAP Cloud for Customer OData APIs.

6.  In the *Scope* list, select the *UIWC:CC\_HOME* scope.

7.  Choose *Save and Close*.




<a name="loio2c9c02d7d19748eea0d2482093f04278__postreq_f5f_ysd_l2b"/>

## Next Steps

On the SAP BTP side configure the HTTP destination required to create an HTTP client for the OData API, and thus ensure the connectivity to SAP Cloud for Customer. For more information, see [Create and Configure the HTTP Destination](Create_and_Configure_the_HTTP_Destination_21e50d8.md).

**Related Information**  


[Configuring OAuth 2.0](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/7e658b3e4cea4a79b035d0f1d2798c1f.html)

