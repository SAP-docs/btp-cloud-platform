<!-- loiob279adf3ec134b2a8611a42bff1ee9d9 -->

# Rotate Signing Keys of Access Tokens

Components of the Cloud Foundry environment use the digital signature of the access tokens to verify the validity of access tokens. To rotate the signing keys of access tokens, use the Security Setting API of the SAP Authorization and Trust Management service.



<a name="loiob279adf3ec134b2a8611a42bff1ee9d9__prereq_g3h_l5y_tjb"/>

## Prerequisites

-   You've enabled API access to the service.

    For more information, see [Access SAP Authorization and Trust Management Service APIs](access-sap-authorization-and-trust-management-service-apis-ebc9113.md)

-   Plan for waiting time in hours between the steps of this procedure.

    After activating a new key, wait for access tokens signed by the old key to expire before deleting the old key. The default lifetime of access tokens is 12 hours.

    To support this delay in rotation, the service enforces a minimum 1-hour delay between rotation and the activation \(`UPDATE`\) or deletion \(`DELETE`\) of signing keys.

    > ### Note:  
    > In emergency cases or in automated test setups, you can bypass the delay in activation and deletion by using the `FORCE_UPDATE` and `FORCE_DELETE` change modes. Forcing changes can also cause service interruption for access tokens that haven't expired yet.




## Procedure

1.  Check that there's space for a new signing key.

    You can store two signing keys per subaccount. Get the settings of your subaccount to see how many keys are stored there.

    Call the *GET* method of the Security Settings API at the following endpoint:

    <code>https://api.authentication.<i class="varname">&lt;region&gt;</i>.hana.ondemand.com/sap/rest/authorization/v2/securitySettings</code>

    For more information, check the security settings API on the [SAP Business Accelerator Hub](https://api.sap.com/package/authtrustmgmnt?section=Artifacts).

    The API returns a JSON with the security settings. Examine the key IDs in the token policy settings.

    ```
    {
        …
        "tokenPolicySettings": {
            …
            "activeKeyId": "jwt-sig-2022-12-01",
            "keyIds": [
                "jwt-sig-2022-09-10",
                "jwt-sig-2022-12-01"
            ]
        },
    …
    }
    ```

    Delete the inactive key if you already have two. In the previous example, delete `jwt-sig-2022-09-10`. For more information on how to delete keys, see step 5.

    > ### Caution:  
    > If the `keyID` is ***key-id-0*** or ***key-id-1***, these keys are legacy signing keys. When you enable the first signing key after a legacy signing key, the legacy signing key is immediately invalid. Clients with access tokens issued within the lifetime of an access token, can't use their access tokens anymore. Affected clients must reauthenticate to get a new token.
    > 
    > Plan for possible service interruption when you add your first signing key.

2.  Add a new signing key for the access token.

    Call the *PATCH* method of the same endpoint.

    In the body, include a key ID and set `changeMode` to `ADD` in the token policy settings.

    > ### Sample Code:  
    > ```
    > {
    >     "tokenPolicySettings": {
    >         "keyId": "jwt-sig-2023-01-30",
    >         "changeMode":"ADD"
    >     }
    > }
    > ```

    A new signing key is generated.

3.  Enable the new signing key.

    Call the *PATCH* method of the same endpoint, but set `changeMode` to `UPDATE`.

    ```
    {
        "tokenPolicySettings": {
            "keyId": "jwt-sig-2023-01-30",
            "changeMode":"UPDATE"
        }
    }
    ```

    New access tokens are now signed with the new signing key.

4.  Wait for access tokens signed by the old key to expire.

    As long as the old signing key exists, the system still accepts digital signatures signed by that key. Once you’ve waited out the lifetime of any access tokens signed by the old key, you can delete the old key.

5.  Delete the old signing key for the access token.

    Call the *PATCH* method of the same endpoint, but set `keyID` to the old key ID and `changeMode` to `DELETE`.

    > ### Sample Code:  
    > ```
    > {
    >     "tokenPolicySettings": {
    >         "keyId": "jwt-sig-2022-12-01",
    >         "changeMode":"DELETE"
    >     }
    > }
    > ```


**Related Information**  


[Managing Secrets of the SAP Authorization and Trust Management Service](managing-secrets-of-the-sap-authorization-and-trust-management-service-22f4a5c.md "The SAP Authorization and Trust Management service maintains a number of secrets to ensure secure operation of the service. Your organization can have policies that require you change secrets or you may need to respond to the loss of a secret.")

