<!-- loiob279adf3ec134b2a8611a42bff1ee9d9 -->

# Rotate Signing Keys of Access Tokens

Components of the Cloud Foundry environment use the digital signature of the access tokens to verify the validity of access tokens. To rotate the signing keys of access token, use the Security Setting API of the SAP Authorization and Trust Management service.



<a name="loiob279adf3ec134b2a8611a42bff1ee9d9__prereq_g3h_l5y_tjb"/>

## Prerequisites

-   You've enabled API access to the SAP Authorization and Trust Management service.

    For more information, see [Access UAA Admin APIs](access-uaa-admin-apis-ebc9113.md)

-   You've checked that you have space for an additional signing key.

    You can store two signing keys per service instance. Get the settings of your subaccount to see how many keys you’ve stored there. Delete an inactive key if you already have two.




<a name="loiob279adf3ec134b2a8611a42bff1ee9d9__context_prh_mmz_tjb"/>

## Context

Access tokens are JSON web tokens \(JWT\). The system uses the signing key of the access token to digitally sign the JWT.

A service instance of the SAP Authorization and Trust Management service has an initial signing key for its access token.

> ### Caution:  
> When you enable the first signing key after the initial signing key, the initial signing key is immediately invalid. Clients with access tokens issued within the last 12 hours, the default lifetime of an access token, can't use their access tokens anymore. Affected clients must reauthenticate to get a new token.
> 
> We recommend that you plan for possible service interruption when you add your first signing key.



## Procedure

1.  Add a new signing key for the access token to the service instance.

    Call the *PATCH* method of the Security Settings API at the following endpoint:

    `https://api.authentication.*<region\>*.hana.ondemand.com/sap/rest/authorization/v2/securitySettings`

    Specify the tenant Id of the tenant that you want to work on with the parameter `tenantid`.

    In the body, include a key ID and set `changeMode` to ***ADD*** in the token policy settings.

    For more information, check the security settings API on the [API Business Hub](https://api.sap.com/package/authtrustmgmnt?section=Artifacts).

    > ### Sample Code:  
    > ```
    > {
    >     "tokenPolicySettings": {
    >         "keyId": "my-new-key",
    >         "changeMode":"ADD"
    >     }
    > }
    > ```

    The service generates a new signing key.

2.  Enable the new signing key.

    Call the *PATCH* method of the same endpoint, but set `changeMode` to ***UPDATE***.

    ```
    {
        "tokenPolicySettings": {
            "keyId": "my-new-key",
            "changeMode":"UPDATE"
        }
    }
    ```

    The service instance now signs new access tokens with the new signing key.

3.  Wait for access tokens signed by the old key to expire.

    As long as the old signing key exists, the system still accepts digital signatures signed by that key. Once you’ve waited out the lifetime of any access tokens signed by the old key, you can delete the old key.

    > ### Note:  
    > Exception: The initial signing key is invalid as soon as you enable your first signing key.

4.  Delete the old signing key for the access token.

    Call the *PATCH* method of the same endpoint, but set `keyID` to the old key ID and `changeMode` to ***DELETE***.

    > ### Sample Code:  
    > ```
    > {
    >     "tokenPolicySettings": {
    >         "keyId": "my-old-key",
    >         "changeMode":"DELETE"
    >     }
    > }
    > ```

    > ### Note:  
    > You can't delete the default signing key. The default signing key is invalid as soon as you add your first signing key.


**Related Information**  


[Managing Secrets of the SAP Authorization and Trust Management Service](managing-secrets-of-the-sap-authorization-and-trust-management-service-22f4a5c.md "The SAP Authorization and Trust Management service maintains a number of secrets to ensure secure operation of the service. Your organization can have policies that require you change secrets or you may need to respond to the loss of a secret.")

