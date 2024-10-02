<!-- loiocf26911d1313420b89d84454d3ac120f -->

# My SAP SuccessFactors OData Destination Does Not Work

SAP SuccessFactors OData destination does not work.



<a name="loiocf26911d1313420b89d84454d3ac120f__section_txr_xtx_dcc"/>

## Issue/Symptom

You are extending SAP SuccessFactors on SAP BTP, Cloud Foundry environment using the SAP SuccessFactors Extensibility service. You are trying to configure the integration between SAP SuccessFactors and SAP Business Technology Platform \(SAP BTP\) and your SAP SuccessFactors OData destination does not work.



<a name="loiocf26911d1313420b89d84454d3ac120f__section_htp_45x_dcc"/>

## Solution

To fix your SAP SuccessFactors OData destination, you can try the following:

-   Make sure that the names of the destination properties, and their values match the names described in [Create an HTTP Destination in SAP BTP](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/55e837080eac424e8e107e18c3a8ac12.html#create-an-http-destination-for-consuming-the-sap-successfactors-hxm-suite-odata-apis).
-   Make sure that the values of the *Client Key* and *apiKey* properties match the *API Key* value specified in the SAP SuccessFactors OAuth client.
-   Make sure that the X509 certificate specified in the SAP SuccessFactors OAuth client is the same as the one you have in the Cloud Foundry environment. See [Configuring the Extension Application's Connectivity to SAP SuccessFactors](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/55e837080eac424e8e107e18c3a8ac12.html#).
-   Make sure that you have the *uaa.user* authorization scope defined in the *xs-security.json*file. See:
    -   [Update a Service Instance](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/7f926eb79a7746fd996363118cd2c2aa.html?q=xs-security.json)
    -   [UAA Scopes](https://docs.cloudfoundry.org/concepts/architecture/uaa.html#uaa-scopes)

-   Make sure that the *uaa.user* authorization scope is defined in the role template in the *xs-security.json*file. See [Accessing Business Service Data](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/783809d7e52f4e14a45945f3f2bad751.html).
-   Make sure you consume the destination correctly, as described in [Consumе the Destination](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/55e837080eac424e8e107e18c3a8ac12.html#loio528d9ae5e6e4495cbd65514294f3994a).
-   Make sure that you use the *user\_token* OAuth grant for retrieving the destination. See [OAuth User Token Exchange Authentication](https://help.sap.com/docs/CP_CONNECTIVITY/cca91383641e40ffbe03bdc78f00f681/e3c333f9de6245fca326993f2397c13a.html).
-   Make sure that the name of the destination that you use in your application matches the name of the one created in the SAP BTP cockpit.
-   Note that if you have a destination defined as an environment variable, it will overrule the one created in the cockpit.
-   Check the logs in Kibana. If you do not have the application logging service, you can add it. See [Access and Analyze Application Logs and Container Metrics](https://help.sap.com/viewer/ee8e8a203e024bbb8c8c2d03fce527dc/Cloud/en-US/30f9cfee0b5d46548ea2fca4ff75bb18.html).
-   Make sure that the name of the destination is the same as the name of the SAP SuccessFactors Extensibility service instance you have created. See [Access and Analyze Application Logs, Container Metrics and Custom Metrics](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/8b774e4ca8be46a4830a021f727667ed.html?version=Cloud).

