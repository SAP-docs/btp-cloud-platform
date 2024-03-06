<!-- loiofda1027a5bb04c35acdf5a68aab07f83 -->

# Get Access to the APIs

To enable programmatic access to the SAP Authorization and Trust Management service \(XSUAA\) in your global account, directory, or multi-environment subaccount, you need API credentials.



## Context

To get access to the APIs of the SAP Authorization and Trust Management service, use the SAP BTP command-line interface \(btp CLI\) to create API credentials. You can get API credentials that apply for the global account, directory, or subaccount.

For more information, see [Managing API Credentials for Calling REST APIs of SAP Authorization and Trust Management Service](managing-api-credentials-for-calling-rest-apis-of-sap-authorization-and-trust-managemen-ce43eb5.md).



## Procedure

1.  Log on to the SAP BTP CLI.

2.  Enter the following command in the relevant global account, subaccount, or directory:

    `btp create security/api-credential --name my-credential`

    You get API credentials, which enable you to access the [REST APIs of the SAP Authorization and Trust Management service on Business Accelerator Hub](https://api.sap.com/package/authtrustmgmnt).

    The btp CLI shows the API credential as follows:

    > ### Output Code:  
    > ```
    > Name: my-credential
    > Credential Type: binding-secret
    > Read-only: false
    > Client Secret: <secret>
    > Certificate: <null>
    > Client ID: sb-full-access!a76125
    > ```

    With the client ID and client secret, or certificate, you can request an access token for the APIs in the targeted global account, directory, or subaccount.


