<!-- loiofefeb7fa13634c67ad2aebdaada5262c -->

# Retrieve the Complete `spec` of an `APIRule` in Version *v1beta1*

Retrieve the complete `spec` of an `APIRule` originally applied in version *v1beta1* when the displayed `spec` does not contain the `rules` field.



## Prerequisites

-   You have the Istio and API Gateway modules added.
-   You have a deployed workload exposed by an `APIRule` in the deprecated *v1beta1* version.
-   You must have [`kubectl`](https://kubernetes.io/docs/tasks/tools/#kubectl) and [`yq`](https://mikefarah.gitbook.io/yq).



<a name="loiofefeb7fa13634c67ad2aebdaada5262c__context_retrieve_v1beta1"/>

## Context

`APIRule` in version *v1beta1* is removed, and the API server no longer responds to requests for `APIRule`s in this version.

This creates a migration challenge: If your `APIRule` was originally created using *v1beta1* and you have not yet migrated to *v2*, the `spec` is missing the `rules` field when viewed via the `kubectl get` command. Kyma dashboard does not display `APIRule`s in version *v1beta1*.

For example, suppose you have applied the following `APIRule` in version *v1beta1*:

```
apiVersion: gateway.kyma-project.io/v1beta1
kind: APIRule
metadata:
  name: httpbin
  namespace: test
spec:
  gateway: kyma-gateway.kyma-system
  host: httpbin
  rules:
  - accessStrategies:
    - handler: noop
    methods:
    - POST
    path: /anything
  - accessStrategies:
    - handler: allow
    methods:
    - HEAD
    path: /headers
  - accessStrategies:
    - handler: no_auth
    methods:
    - GET
    path: /.*
  service:
    name: httpbin
    namespace: test
    port: 8000
```

When retrieving this `APIRule`, the resulting `spec` does not include the `rules` field, as these rules cannot be converted to *v2*:

```
kubectl get apirules.gateway.kyma-project.io -n $NAMESPACE $APIRULE_NAME -oyaml
```

```
...
spec:
  gateway: kyma-system/kyma-gateway
  hosts:
    - httpbin
  service:
    name: httpbin
    namespace: test
    port: 8000
...
```

In this case, you must access the original `APIRule` *v1beta1* configuration through an annotation. To learn how to do this, follow the procedure.



## Procedure

1.  To get the full original `spec` of the `APIRule` created in version *v1beta1*, use the annotation that stores the original configuration. Run:

    ```
    kubectl get apirules.gateway.kyma-project.io -n $NAMESPACE $APIRULE_NAME -ojsonpath='{.metadata.annotations.gateway\.kyma-project\.io/v1beta1-spec}'
    ```

    See a sample output in the JSON format:

    ```
    {"host":"httpbin","service":{"name":"httpbin","namespace":"test","port":8000},"gateway":"kyma-gateway.kyma-system","rules":[{"path":"/anything","methods":["POST"],"accessStrategies":[{"handler":"noop"}]},{"path":"/headers","methods":["HEAD"],"accessStrategies":[{"handler":"allow"}]},{"path":"/.*","methods":["GET"],"accessStrategies":[{"handler":"no_auth"}]}]}
    ```

2.  To format the output as YAML for better readability, use the `yq` command.

    ```
    kubectl get apirules.gateway.kyma-project.io -n $NAMESPACE $APIRULE_NAME -ojsonpath='{.metadata.annotations.gateway\.kyma-project\.io/v1beta1-spec}' | yq -P
    ```

    See a sample output in the YAML format:

    ```
    host: httpbin
    service:
      name: httpbin
      namespace: test
      port: 8000
    gateway: kyma-gateway.kyma-system
    rules:
      - path: /anything
        methods:
          - POST
        accessStrategies:
          - handler: noop
      - path: /headers
        methods:
          - HEAD
        accessStrategies:
          - handler: allow
      - path: /.*
        methods:
          - GET
        accessStrategies:
          - handler: no_auth
    ```




## Next Steps

Adjust the obtained configuration of the `APIRule` to migrate it to version *v2*. To learn how to do this, follow the relevant tutorial:

-   [Migrate APIRule v1beta1 of Type jwt to Version v2](migrate-apirule-v1beta1-of-type-jwt-to-version-v2-bcaec91.md)
-   [Migrate APIRule v1beta1 of Type noop, allow, or no\_auth to Version v2](migrate-apirule-v1beta1-of-type-noop-allow-or-no-auth-to-version-v2-2b19ef5.md)
-   [Migrate APIRule v1beta1 of Type oauth2\_introspection to Version v2](migrate-apirule-v1beta1-of-type-oauth2-introspection-to-version-v2-394d18a.md)

