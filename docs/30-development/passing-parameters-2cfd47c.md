<!-- loio2cfd47cf52b440e8bad3f0c495db824b -->

# Passing Parameters

You can set input parameters for your resources.



<a name="loio2cfd47cf52b440e8bad3f0c495db824b__section_cf5_bmx_wcc"/>

## Procedure

To set input parameters, go to the `spec` of the `ServiceInstance` or `ServiceBinding` resource, and use one or all of the following fields:

-   `parameters`: Specifies a set of properties sent to the service broker. The specified data is passed to the service broker without any modifications aside from converting it to JSON for transmission to the broker if the `spec` field is specified as YAML. All valid YAML or JSON constructs are supported.

-   `parametersFrom`: Specifies which Secret, together with the key in it, to include in the set of parameters sent to the service broker. The key contains a `string` that represents a JSON file. The `parametersFrom` field is a list that supports multiple sources referenced per `spec`. The ServiceInstance resource can specify multiple related Secrets.

-   `watchParametersFromChanges`: Use this field together with `parametersFrom`. Set it to `true` to trigger an automatic update of the ServiceInstance resource with the changes to the Secret values listed in `parametersFrom`. By default, the field is set to `false`.


If you specify multiple sources in the `parameters` and `parametersFrom` fields, the final payload merges all of them at the top level.

To avoid errors, do not use the same top-level parameter name in multiple sources in the `parameters` and `parametersFrom` fields. Otherwise, the specification is invalid, and further processing of the `ServiceInstance` or `ServiceBinding` resources stops with the status ***Error***.



<a name="loio2cfd47cf52b440e8bad3f0c495db824b__section_uxh_dnx_wcc"/>

## Examples

See the following examples:

-   The `spec` format in YAML:

    ```
    spec:
      ...
      parameters:
        name: value
      parametersFrom:
        - secretKeyRef:
            name: {SECRET_NAME}
            key: secret-parameter
      watchParametersFromChanges: true      
    ```

-   The `spec` format in JSON:

    ```
    {
      "spec": {
        "parameters": {
          "name": "value"
        },
        "parametersFrom": {
          "secretKeyRef": {
            "name": "{SECRET_NAME}",
            "key": "secret-parameter"
          }
        }
        "watchParametersFromChanges": true
      } 
    }
    ```

-   A Secret with the key named `secret-parameter`:

    ```
    apiVersion: v1
    kind: Secret
    metadata:
      name: {SECRET_NAME}
    type: Opaque
    stringData:
      secret-parameter:
        '{
          "password": "password"
        }'
    ```

-   The final JSON payload sent to the service broker:

    ```
    {
      "name": "value",
      "password": "password"
    }
    ```

-   Multiple parameters in the Secret with key-value pairs separated with commas:

    ```
    secret-parameter:
      '{
        "password": "password",
        "key2": "value2",
        "key3": "value3"
      }'
    ```


