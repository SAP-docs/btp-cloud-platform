<!-- loio1711365955074e409a3748e919e5347e -->

# Identity Provider Could Not Process Authentication Request



## Symptom

After sending a request to a web application in the SAP BTP, Cloud Foundry environment, the system responds as follows:

`Error - Identity provider could not process the authentication request received. Delete your browser cache and stored cookies, and restart your browser. If you continue to experience issues, send an e-mail to sso@sap.com.`



## Reason and Prerequisites

The Cloud Foundry environment uses the Identity Authentication service as its SAML 2.0 identity provider. The SAP Authorization and Trust Management service \(XSUAA\) forwards unauthenticated requests to the configured identity provider. This error occurs because the trust relationship between the SAP Authorization and Trust Management service and the identity provider hasn't been fully configured. The subaccount has not been registered in the SAML 2.0 identity provider.



## Solution

Configure the missing part of the trust relationship in your identity provider by doing one of the following:

-   Use the [simplified trust configuration](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/161f8f0cfac64c4fa2d973bc5f08a894.html).
-   Download the SAML metadata file from the SAP Authorization and Trust Management service, upload it to your SAML 2.0 identity provider, and complete the configuration by registering your subaccount. The following link provides instructions for configuring the Identity Authentication service as a trusted SAML 2.0 identity provider: [Register SAP BTP Subaccount in the SAML 2.0 Identity Provider](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/7c6aa87459764b179aeccadccd4f91f3.html#loio347cc6991eda439ea7d87ef1311913bf).

