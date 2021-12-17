<!-- loio974f741bb4884bc1bbc1ecb5737a733e -->

# Configuring Backup

You can back up and restore the destination and the trust configuration settings for the integration between the SAP S/4HANA Cloud and the global account in SAP BTP.

You can back up and restore the following configuration settings:

-   The HTTP destination configured during the creation of the SAP S/4HANA Cloud Extensibility service instance. For more, see [Export Destinations](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/707b49e752df4741bf678bc27523af7a.html).

-   Your subaccount X.509 certificates. For more information, see [Set up Trust Between Systems](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/82dbecae3454493782d16a79e30f1a6d.html) 

-   Your subaccount-specific IdP metadata.

    To download your SAP SuccessFactors IdP SAML 2.0 metadata, in the SAP BTP cockpit, navigate to *Connectivity* \> *Destinations* \> *Download IdP Metadata*.

-   Your identity provider configurations.

    You can back up identity provider configurations with the Identity Provider Management API. For more information see: [Identity Provider Management](https://api.sap.com/api/TrustConfigurationAPI/overview) API.


