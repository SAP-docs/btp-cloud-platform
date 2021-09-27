<!-- loio052e9b4b54ce4c268422b1f2c736e47e -->

# Rotate Signing Keys of SAML Token

The SAP Authorization and Trust Management service uses an X.509 certificate to sign SAML 2.0 protocol messages between itself, a SAML service provider, and an SAML identity provider. To rotate the signing keys for SAML tokens, use the Security Settings API of the SAP Authorization and Trust Management service and then establish trust by exchanging metadata between the service provider and identity provider.



<a name="loio052e9b4b54ce4c268422b1f2c736e47e__prereq_g3h_l5y_tjb"/>

## Prerequisites

-   You've enabled API access to the SAP Authorization and Trust Management service.

    For more information, see [Access UAA Admin APIs](Access_UAA_Admin_APIs_ebc9113.md)

-   Optionally, to use your own signing key for SAML tokens, you've obtained an X.509 certificate for the SAP Authorization and Trust Management service.

-   You've checked that you have space for an additional signing key.

    You can store two signing keys per service instance. Get the settings of your subaccount to see how many signing keys you’ve stored there. Delete an inactive signing key if you already have two.




<a name="loio052e9b4b54ce4c268422b1f2c736e47e__context_w3m_mjz_tjb"/>

## Context

The signed SAML tokens are used to validate and authenticate the protocol messages between the SAP Authorization and Trust Management service instance and the identity provider.



<a name="loio052e9b4b54ce4c268422b1f2c736e47e__steps_txf_23s_tjb"/>

## Procedure

1.  Add a new signing key for SAML tokens to the service instance.

    Call the *PATCH* method of the Security Settings API at the following endpoint:

    `https://api.authentication.*<region\>*.hana.ondemand.com/sap/rest/authorization/v2/securitySettings`

    In the body, include a key ID and set `changeMode` to ***ADD*** in the SAML configuration settings.

    > ### Sample Code:  
    > ```
    > {
    >     "samlConfigSettings": {
    >         "keyId": "my-new-key",
    >         "changeMode":"ADD"
    >     }
    > }
    > ```

    The service generates a new signing key.

    Optionally, provide your own signing key with the `key` parameter. The signing key is your private key of the certificate key pair. Provide the certificate.

    > ### Recommendation:  
    > We recommend providing an empty passphrase. We believe that there's no reason to view the private key.

    > ### Note:  

    > ### Sample Code:  
    > ```
    > {
    >     "samlConfigSettings": {
    >         "keyId": "my-new-key",
    >         "changeMode":"ADD",
    >         "key": "*<key\_data\>*",
    >         "passphrase": "",
    >         "certificate": "*<certificate\_data\>*"
    >     }
    > }
    > ```

2.  Enable the new signing key.

    Call the *PATCH* method of the same endpoint, but set `changeMode` to ***UPDATE***.

    ```
    {
        "samlConfigSettings": {
            "keyId": "my-new-key",
            "changeMode":"UPDATE"
                }
            }
        }
    }
    ```

    The service instance now signs new SAML tokens with the new signing key.

3.  Establish trust with the identity providers you consume.

    Upload the new metadata information to your identity providers.

    For more information, see the related documentation:

    -   [Manually Establish Trust and Federation Between UAA and Identity Authentication](Manually_Establish_Trust_and_Federation_Between_UAA_and_Identity_Authentication_7c6aa87.md#loio7c6aa87459764b179aeccadccd4f91f3)

    -   [Establish Trust and Federation with UAA Using Any SAML Identity Provider](Establish_Trust_and_Federation_with_UAA_Using_Any_SAML_Identity_Provider_2ce3938.md#loio2ce3938c66d94479848bff3090999027)

    > ### Caution:  
    > Until you upload the metadata to your identity provider, the identity provider rejects SAML tokens signed by the service instance.

4.  Delete the old signing key for SAML tokens.

    Call the *PATCH* method of the same endpoint, but set `keyID` to the old key ID and `changeMode` to ***DELETE***.

    > ### Sample Code:  
    > ```
    > {
    >     "samlConfigSettings": {
    >         "keyId": "my-old-key",
    >         "changeMode":"DELETE"
    >             }
    >         }
    >     }
    > }
    > ```


**Related Information**  


[Access UAA Admin APIs](Access_UAA_Admin_APIs_ebc9113.md "To enable programmatic access to the XS user authentication and authorization (UAA) service in your subaccount of the Cloud Foundry environment, create an XSUAA service instance under the apiaccess plan.")

[Managing Secrets of the SAP Authorization and Trust Management Service](Managing_Secrets_of_the_SAP_Authorization_and_Trust_Management_Service_22f4a5c.md "The SAP Authorization and Trust Management service maintains a number of secrets to ensure secure operation of the service. Your organization can have policies that require you change secrets or you may need to respond to the loss of a secret.")

