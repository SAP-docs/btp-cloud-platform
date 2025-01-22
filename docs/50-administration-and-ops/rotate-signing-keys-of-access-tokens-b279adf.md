<!-- loiob279adf3ec134b2a8611a42bff1ee9d9 -->

# Rotate Signing Keys of Access Tokens

Components of SAP BTP use the digital signature of the access tokens to verify the validity of access tokens. Periodically rotate the signing keys of access tokens \(see [Security Recommendations for SAP Authorization and Trust Management Service](../60-security/security-recommendations-for-sap-authorization-and-trust-management-service-0578b80.md)\).

**Related Information**  


[Manually Rotate Signing Keys of Access Tokens with the SAP BTP CLI](rotate-signing-keys-of-access-tokens-b279adf.md#loio8e15b59efbd846de990a9207b45ac71d "The SAP BTP CLI enables you to manually rotate the signing keys of access tokens.")

[Manually Rotate Signing Keys of Access Tokens with the Security Setting API](rotate-signing-keys-of-access-tokens-b279adf.md#loiodb9daade18d04bfbb4b03fca11dbd349 "You can use the Security Setting API of the SAP Authorization and Trust Management service to manually rotate the signing keys of access tokens.")

<a name="loio8e15b59efbd846de990a9207b45ac71d"/>

<!-- loio8e15b59efbd846de990a9207b45ac71d -->

## Manually Rotate Signing Keys of Access Tokens with the SAP BTP CLI

The SAP BTP CLI enables you to manually rotate the signing keys of access tokens.



<a name="loio8e15b59efbd846de990a9207b45ac71d__prereq_hqc_jyk_31c"/>

## Prerequisites

Plan for waiting time in hours between the steps of this procedure.

After activating a new key, wait for access tokens signed by the old key to expire before deleting the old key. The default lifetime of access tokens is 12 hours.

To support this delay in rotation, the service enforces a minimum 12-hour delay between rotation and the activation.

> ### Note:  
> In emergency cases or in automated test setups, you can bypass the delay in activation and deletion by using the `--force` option. Forcing changes can also cause service interruption for access tokens that haven't expired yet.



<a name="loio8e15b59efbd846de990a9207b45ac71d__context_hry_lxk_31c"/>

## Context

To rotate the signing key of access tokens, use the SAP BTP command-line interface \(btp CLI\). You can rotate signing keys for the global account, directory, or subaccount.

For more information, see [Managing Signing Keys for Access Tokens](managing-signing-keys-for-access-tokens-dfca1d3.md).



## Procedure

1.  Log on to the SAP BTP CLI.

    For more information, see [Log in](log-in-e241b30.md).

2.  Check that there's space for a new signing key.

    You can store two signing keys per subaccount.

    Use the following command:

    ```
    btp list security/token-key
    ```

    The service lists any keys.

    ```
    Key ID                     Enabled   Created                      Fips Compliant 
    default-jwt-key-491aae9c42           Fri Feb 02 14:48:51 UTC 2024 yes
    default-jwt-key-ca81ebbb43 yes       Mon Feb 05 14:42:26 UTC 2024 yes
    
    2 entries
    
    OK
    ```

    Delete the inactive key if you already have two. In the previous example, delete `default-jwt-key-491aae9c42`. For more information on how to delete keys, see step 6.

    > ### Caution:  
    > If the `keyID` is ***key-id-0*** or ***key-id-1***, these keys are legacy signing keys. When you enable the first signing key after a legacy signing key, the legacy signing key is immediately invalid. Clients with access tokens issued within the lifetime of an access token can't use their access tokens anymore. Affected clients must reauthenticate to get a new token.
    > 
    > In addition, the issuer of the key changes as well. Update the configuration of systems depending on these keys, such as SAP HANA systems and cloud connector connections. For more information, see:
    > 
    > -   [Managed Certificate Collections](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-security-guide/managed-certificate-collections) in the *SAP HANA Cloud, SAP HANA Database Security Guide*
    > 
    > -   [Configure a CA Certificate](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/configure-ca-certificate-for-principal-propagation?version=Cloud) in the *SAP BTP Connectivity* documentation
    > 
    > 
    > Plan for possible service interruption when you add your first signing key.

3.  Add a new signing key for the access token.

    Use the following command:

    ```
    btp create security/token-key
    Created default signing key
    ```

    A new signing key is generated.

4.  Enable the new signing key.

    Use the following command:

    <code>btp enable security/token-key --key <i class="varname">&lt;Key_ID&gt;</i></code>

    For example:

    ```
    btp enable security/token-key --key default-jwt-key-ca81ebbb43
    Enabled signing key 'default-jwt-key-ca81ebbb43'
    ```

    New access tokens are now signed with the new signing key.

5.  Wait for access tokens signed by the old key to expire.

    As long as the old signing key exists, the system still accepts digital signatures signed by that key. Once you’ve waited out the lifetime of any access tokens signed by the old key, you can delete the old key.

6.  Delete the old signing key for the access token.

    Use the following command:

    <code>btp delete security/token-key --key <i class="varname">&lt;Key_ID&gt;</i></code>

    For example:

    ```
    btp delete security/token-key --key default-jwt-key-491aae9c42
    Do you really want to delete signing key 'default-jwt-key-491aae9c42'? [no]> Yes
    Deleted signing key 'default-jwt-key-491aae9c42'
    ```


<a name="loiodb9daade18d04bfbb4b03fca11dbd349"/>

<!-- loiodb9daade18d04bfbb4b03fca11dbd349 -->

## Manually Rotate Signing Keys of Access Tokens with the Security Setting API

You can use the Security Setting API of the SAP Authorization and Trust Management service to manually rotate the signing keys of access tokens.



<a name="loiodb9daade18d04bfbb4b03fca11dbd349__prereq_g3h_l5y_tjb"/>

## Prerequisites

-   You've enabled API access to the service.

    For more information, see [Get Access to the APIs](get-access-to-the-apis-fda1027.md).

-   Plan for waiting time in hours between the steps of this procedure.

    After activating a new key, wait for access tokens signed by the old key to expire before deleting the old key. The default lifetime of access tokens is 12 hours.

    To support this delay in rotation, the service enforces a minimum 12-hour delay between rotation and the activation \(`UPDATE`\) or deletion \(`DELETE`\) of signing keys.

    > ### Note:  
    > In emergency cases or in automated test setups, you can bypass the delay in activation and deletion by using the `FORCE_UPDATE` and `FORCE_DELETE` change modes. Forcing changes can also cause service interruption for access tokens that haven't expired yet.




## Context



<a name="loiodb9daade18d04bfbb4b03fca11dbd349__steps_qyt_hzk_31c"/>

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
    > In addition, the issuer of the key changes as well. Update the configuration of systems depending on these keys, such as SAP HANA systems and cloud connector connections. For more information, see:
    > 
    > -   [Managed Certificate Collections](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-security-guide/managed-certificate-collections) in the *SAP HANA Cloud, SAP HANA Database Security Guide*
    > 
    > -   [Configure a CA Certificate](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/configure-ca-certificate-for-principal-propagation?version=Cloud) in the *SAP BTP Connectivity* documentation
    > 
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

