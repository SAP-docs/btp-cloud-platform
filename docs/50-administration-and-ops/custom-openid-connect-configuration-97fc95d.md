<!-- loio97fc95da803c438d9a0dbc0d82a05b84 -->

# Custom OpenID Connect Configuration

During SAP BTP, Kyma runtime provisioning or update, you can provide your custom Open ID Connect \(OIDC\) configuration as a list of `oidc` objects or as a single `oidc` object. You can also have no OIDC configuration.

<a name="concept_i2s_3j5_xfc"/>

<!-- concept\_i2s\_3j5\_xfc -->

## Configuring the OIDC Property as a List of `oidc` Objects

Configure the `oidc` property as a list of `oidc` objects. In this way, you can define zero, one, or multiple OIDC configurations. When using the list of `oidc` objects, you must provide values for each element except for `requiredClaims`. By configuring the OIDC details yourself, you gain full visibility of your settings within the SAP BTP cockpit. For your convenience, in the SAP BTP cockpit, one `oidc` object has the predefined values filled in, but you can change them. For each additional `oidc` object, you must provide your own settings.



<a name="concept_i2s_3j5_xfc__section_ynr_pj5_xfc"/>

## Provisioning Kyma Runtime with the `oidc` List

When configuring your OIDC setup, you have the following options:

-   If you use an `oidc` list, you must explicitly define values for all its elements, because they do not inherit default values.
-   If you provide an empty `oidc` list with zero elements, no OIDC configuration is applied to the instance.



### Example

-   Configuring the `oidc` list.

    You can define one or multiple OIDC configurations, depending on the number of lists of `oidc` objects you add to your provisioning request. See an example of a request with one `oidc` object in the list:

    ```
    {
      "service_id" : "47c9dcbf-ff30-448e-ab36-d3bad66ba281",
      "plan_id" : "4deee563-e5ec-4731-b9b1-53b42d855f0c",
      "context" : {
        "globalaccount_id" : {GLOBAL_ACCOUNT_ID}
      },
      "parameters" : {
        "region": {REGION},
        "name" : {CLUSTER_NAME},
        "oidc" : {
          "list": [
            {
              "clientID" : "custom-client-id",
              "issuerURL" : "https://custom.issuer.com",
              "groupsClaim" : "groups",
              "groupsPrefix" : "-",
              "signingAlgs" : ["RS256"],
              "usernamePrefix" : "-",
              "usernameClaim" : "sub",
              "requiredClaims" : ["first-claim=value", "second-claim=value"],
              "encodedJwksArray": ""
            }
          ]
        }
      }
    }
    ```

    You see a configuration similar to this one:

    ```
    {
      ...
      "oidc" : {
        "list": [
          {
            "clientID" : "custom-client-id",
            "issuerURL" : "https://custom.issuer.com",
            "groupsClaim" : "groups",
            "groupsPrefix" : "-",
            "signingAlgs" : ["RS256"],
            "usernamePrefix" : "-",
            "usernameClaim" : "sub",
            "requiredClaims" : ["first-claim=value", "second-claim=value"],
            "encodedJwksArray": ""
          }
        ]
      }
      ...
    }
    ```




<a name="concept_i2s_3j5_xfc__section_lnr_tj5_xfc"/>

## Updating Kyma Runtime with the `oidc` List

You can update the OIDC configuration from a single `oidc` object to an `oidc` list, but updating from an `oidc` list to a single `oidc` object is not supported.

When updating your OIDC configuration, you have the following options:

-   If you are updating your `oidc` list, you must explicitly define values for all its elements, because they do not inherit default values.
-   The update operation overwrites the OIDC configuration values provided in JSON for the `oidc` list, so if you provide OIDC parameters with empty values, they are considered valid and replace the existing settings.
-   If you provide an empty `oidc` list, it clears the OIDC configuration for the instance.



### Example

-   Updating an instance with a list of `oidc` objects.

    Suppose your current OIDC configuration is the following:

    ```
    [
      {
       "clientID": "first-custom-client-id",
       "issuerURL": "https://first.custom.issuer.com",
       "groupsClaim": "groups",
       "groupsPrefix": "-",
       "usernameClaim": "sub",
       "usernamePrefix": "-",
       "signingAlgs": ["RS256"],
       "requiredClaims": ["first-claim=value", "second-claim=value"],
       "encodedJwksArray": ""
      },
      {
       "clientID": "second-custom-client-id",
       "issuerURL": "https://second.custom.issuer.com",
       "groupsClaim": "groups",
       "groupsPrefix": "-",
       "usernameClaim": "sub",
       "usernamePrefix": "acme-",
       "signingAlgs": ["RS256"],
       "requiredClaims": ["example-claim=value"],
       "encodedJwksArray": ""
      }
    ]
    ```

    To update this configuration, send an HTTP PATCH request with the following payload:

    ```
    {
      "service_id": "47c9dcbf-ff30-448e-ab36-d3bad66ba281",
      "plan_id": "4deee563-e5ec-4731-b9b1-53b42d855f0c",
      "context": {
       "globalaccount_id": "{GLOBAL_ACCOUNT_ID}"
      },
      "parameters": {
       "name": "{CLUSTER_NAME}",
       "oidc": {
        "list": [
          {
           "clientID": "new-client-id",
           "issuerURL": "https://new.issuer.com",
           "groupsClaim": "groups",
           "groupsPrefix": "-",
           "signingAlgs": ["RS256"],
           "usernameClaim": "sub",
           "usernamePrefix": "-",
           "requiredClaims": [],
           "encodedJwksArray": ""
          },
          {
           "clientID": "updated-client-id",
           "issuerURL": "https://updated.issuer.com",
           "groupsClaim": "groups",
           "groupsPrefix": "-",
           "usernameClaim": "sub",
           "usernamePrefix": "acme-",
           "signingAlgs": ["RS256"],
           "encodedJwksArray": ""
          }
        ]
       }
      }
    }
    ```

    You see the configuration with the values provided in the request:

    ```
    [
      {
       "clientID": "new-client-id",
       "issuerURL": "https://new.issuer.com",
       "groupsClaim": "groups",
       "groupsPrefix": "-",
       "usernameClaim": "sub",
       "usernamePrefix": "-",
       "signingAlgs": ["RS256"],
       "requiredClaims": [],
       "encodedJwksArray": ""
      },
      {
       "clientID": "updated-client-id",
       "issuerURL": "https://updated.issuer.com",
       "groupsClaim": "groups",
       "groupsPrefix": "-",
       "usernameClaim": "sub",
       "usernamePrefix": "acme-",
       "signingAlgs": ["RS256"],
       "requiredClaims": [],
       "encodedJwksArray": ""
      }
    ]
    ```


<a name="concept_ifg_mj5_xfc"/>

<!-- concept\_ifg\_mj5\_xfc -->

## Configuring the OIDC Property as a Single `oidc` Object

This solution is not recommended, and is only supported for maintaining backward compatibility with existing automations. With this approach you cannot have multiple OIDC configurations for your Kyma runtime.

In the SAP BTP cockpit, you can only see the parameters that you configure yourself. Since you must provide values only for `clientID` and `issuerURL` in a single `oidc` object, the visibility of your complete OIDC configuration may be limited.



<a name="concept_ifg_mj5_xfc__section_hmq_1k5_xfc"/>

## Provisioning Kyma Runtime with a Single `oidc` Object

When configuring your OIDC setup, you have the following options:

-   If you do not include an `oidc` object in the provisioning request at all, the default OIDC configuration is applied.
-   If you leave the parameters of a single `oidc` object empty, it defaults to the predefined values.



### Example

-   See a request with an `oidc` object with empty keys:

    ```
    {
      "service_id" : "47c9dcbf-ff30-448e-ab36-d3bad66ba281",
      "plan_id" : "4deee563-e5ec-4731-b9b1-53b42d855f0c",
      "context" : {
        "globalaccount_id" : {GLOBAL_ACCOUNT_ID}
      },
      "parameters" : {
        "region": {REGION},
        "name" : {CLUSTER_NAME},
        "oidc" : {
          "clientID" : "",
          "issuerURL" : "",
          "groupsClaim" : "",
          "groupsPrefix" : "",
          "signingAlgs" : [],
          "usernamePrefix" : "",
          "usernameClaim" : "",
          "requiredClaims" : ["-"],
          "encodedJwksArray": "-"
        }
      }
    }
    ```

    The result is the default OIDC configuration:

    ```
    {
      ...
      "oidc" : {
        "clientID" : "12b13a26-d993-4d0c-aa08-5f5852bbdff6",
        "issuerURL" : "https://kyma.accounts.ondemand.com",
        "groupsClaim" : "groups",
        "groupsPrefix" : "-",
        "signingAlgs" : ["RS256"],
        "usernamePrefix" : "-",
        "usernameClaim" : "sub",
        "requiredClaims" : ["-"],
        "encodedJwksArray": "-"
      }
      ...
    }
    ```




<a name="concept_ifg_mj5_xfc__section_imq_1k5_xfc"/>

## Updating Kyma Runtime with a Single `oidc` Object

You can update the OIDC configuration from a single `oidc` object to an `oidc` list, but updating from an `oidc` list to a single `oidc` object is not supported.

When updating your OIDC configuration, you have the following options:

-   If you provide no `oidc` object in the update request, the existing OIDC configuration remains unchanged.
-   If you update using a single `oidc` object, empty keys do not change the configuration, and only the provided values are updated.



### Example

-   Updating an instance with a single `oidc` object.

    Suppose your current OIDC configuration is the following:

    ```
    {
      "clientID": "some-client-id",
      "issuerURL": "https://some.issuer.com",
      "groupsClaim": "groups",
      "groupsPrefix": "-",
      "usernameClaim": "sub",
      "usernamePrefix": "-",
      "signingAlgs": ["RS256"],
      "requiredClaims": ["-"],
      "encodedJwksArray": "-"
    }
    ```

    To update this configuration, send an HTTP PATCH request with the following payload:

    ```
    {
      "service_id": "47c9dcbf-ff30-448e-ab36-d3bad66ba281",
      "plan_id": "4deee563-e5ec-4731-b9b1-53b42d855f0c",
      "context": {
       "globalaccount_id": "{GLOBAL_ACCOUNT_ID}"
      },
      "parameters": {
       "name": "{CLUSTER_NAME}",
       "oidc": {
        "clientID": "new-client-id",
        "issuerURL": "https://new.issuer.com",
        "groupsClaim": "",
        "groupsPrefix": "",
        "signingAlgs": [],
        "usernamePrefix": "",
        "usernameClaim": "",
        "requiredClaims": ["-"],
        "encodedJwksArray": "-"
       }
      }
    }
    ```

    You see the configuration with the values provided in the request, similar to this one:

    ```
    {
      "clientID": "new-client-id",
      "issuerURL": "https://new.issuer.com",
      "groupsClaim": "groups",
      "groupsPrefix": "-",
      "usernameClaim": "sub",
      "usernamePrefix": "-",
      "signingAlgs": ["RS256"],
      "requiredClaims": ["-"],
      "encodedJwksArray": "-"
    }
    ```


<a name="concept_qlz_g3w_xfc"/>

<!-- concept\_qlz\_g3w\_xfc -->

## Configuration with no OIDC Property

You can provision or update your Kyma runtime without providing the OIDC property at all.



<a name="concept_qlz_g3w_xfc__section_ylz_3sw_xfc"/>

## Provisioning Kyma Runtime with No OIDC Property

If you do not include an `oidc` parameter in the provisioning request at all, the default OIDC configuration is applied.



### Example

-   See an example of a provisioning request without specifying any `oidc` configuration:

    ```
    {
      "service_id" : "47c9dcbf-ff30-448e-ab36-d3bad66ba281",
      "plan_id" : "4deee563-e5ec-4731-b9b1-53b42d855f0c",
      "context" : {
        "globalaccount_id" : {GLOBAL_ACCOUNT_ID}
      },
      "parameters" : {
        "region": {REGION},
        "name" : {CLUSTER_NAME}
      }
    }
    ```

    The resulting configuration has default values like in the following example. You can only view this configuration in your cluster.

    ```
    {
      ...
      "oidc" : {
        "clientID" : "12b13a26-d993-4d0c-aa08-5f5852bbdff6",
        "issuerURL" : "https://kyma.accounts.ondemand.com",
        "groupsClaim" : "groups",
        "groupsPrefix" : "-",
        "signingAlgs" : ["RS256"],
        "usernamePrefix" : "-",
        "usernameClaim" : "sub",
        "requiredClaims" : ["-"],
        "encodedJwksArray": "-"
      }
      ...
    }
    ```




<a name="concept_qlz_g3w_xfc__section_cg5_3tw_xfc"/>

## Updating Kyma Runtime with No OIDC Property

If you provide no `oidc` property in the update request, the existing OIDC configuration remains unchanged.

**Related Information**  


[OpenID Connect \(OIDC\)](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_OIDC)

[Configuring a Custom Identity Provider for Kyma](../60-security/configuring-a-custom-identity-provider-for-kyma-67bcc6e.md "Enable the Kyma environment with a custom identity provider (IdP).")

