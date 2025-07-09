<!-- loiofefeb7fa13634c67ad2aebdaada5262c -->

# Retrieving the Complete spec of an APIRule in Version v1beta1

Learn how to retrieve the complete `spec` of an APIRule originally applied in version `v1beta1` when the displayed `spec` does not contain the `rules` field. To do this, you can either use Kyma dashboard or the `kubectl get` command.



<a name="loiofefeb7fa13634c67ad2aebdaada5262c__prereq_n2k_hrn_sfc"/>

## Prerequisites

-   You have the Istio and API Gateway modules added.
-   You have a deployed workload exposed by an APIRule in the deprecated v1beta1 version.
-   To use CLI instructions, you must have [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl) and [yq](https://mikefarah.gitbook.io/yq). Alternatively, you can use Kyma dashboard.



## Context

APIRule in version `v1beta1` is deprecated and scheduled for removal. Once the APIRule custom resource definition \(CRD\) stops serving version `v1beta1`, the API server will no longer respond to requests for APIRules in this version. Consequently, you will encounter errors attempting to access the APIRule custom resource at the deprecated `v1beta1` version.

This creates a migration challenge: If your APIRule was originally created using `v1beta1` and you have not yet migrated to `v2`, you may notice that the `spec` is missing the `rules` field when viewed in Kyma dashboard or via the `kubectl get` command.

For example, suppose you have applied the following APIRule in version `v1beta1`:

> ### Sample Code:  
> ```
> apiVersion: gateway.kyma-project.io/v1beta1
> kind: APIRule
> metadata:
>   name: httpbin
>   namespace: test
> spec:
>   gateway: kyma-system/kyma-gateway
>   host: httpbin
>   rules:
>   - accessStrategies:
>     - handler: noop
>     methods:
>     - POST
>     path: /anything
>   - accessStrategies:
>     - handler: allow
>     methods:
>     - HEAD
>     path: /headers
>   - accessStrategies:
>     - handler: no_auth
>     methods:
>     - GET
>     path: /.*
>   service:
>     name: httpbin
>     namespace: test
>     port: 8000
> ```

When retrieving this APIRule, the resulting `spec` does not include the `rules` field, as these rules cannot be converted to `v2`:

```
kubectl get apirules.gateway.kyma-project.io -n $NAMESPACE $APIRULE_NAME -oyaml 
```

> ### Sample Code:  
> ```
> ...
> spec:
>   gateway: kyma-system/kyma-gateway
>   hosts:
>     - httpbin
>   service:
>     name: httpbin
>     namespace: test
>     port: 8000
> ...
> ```

In this case, you must access the original APIRule `v1beta1` configuration through an annotation. To learn how to do this, follow the procedure.



## Procedure

-   Use Kyma dashboard.

    1.  Go to *Discovery and Network \> API Rules* and select specific APIRule CR in version `v1beta1`.

    2.  Go to the *Edit* tab.

    3.  Copy the value of `metadata.annotations.gateway.kyma-project.io/v1beta1-spec` as it stores the full original configuration of the APIRule created in version `v1beta1`.


-   Use kubectl.

    1.  To get the full original **spec** of the APIRule created in version `v1beta1`, use the annotation that stores the original configuration. Run:

        ```
        kubectl get apirules.gateway.kyma-project.io -n $NAMESPACE $APIRULE_NAME -ojsonpath='{.metadata.annotations.gateway\.kyma-project\.io/v1beta1-spec}' 
        ```

        See a sample output in the JSON format:

        > ### Sample Code:  
        > ```
        > {"host":"httpbin","service":{"name":"httpbin","namespace":"test","port":8000},"gateway":"kyma-system/kyma-gateway","rules":[{"path":"/anything","methods":["POST"],"accessStrategies":[{"handler":"noop"}]},{"path":"/headers","methods":["HEAD"],"accessStrategies":[{"handler":"allow"}]},{"path":"/.*","methods":["GET"],"accessStrategies":[{"handler":"no_auth"}]}]}
        > ```

    2.  To format the output as YAML for better readability, use the yq command.

        ```
        kubectl get apirules.gateway.kyma-project.io -n $NAMESPACE $APIRULE_NAME -ojsonpath='{.metadata.annotations.gateway\.kyma-project\.io/v1beta1-spec}' | yq -P
        ```

        See a sample output in the YAML format:

        > ### Sample Code:  
        > ```
        > host: httpbin
        > service:
        >   name: httpbin
        >   namespace: test
        >   port: 8000
        > gateway: kyma-system/kyma-gateway
        > rules:
        >   - path: /anything
        >     methods:
        >       - POST
        >     accessStrategies:
        >       - handler: noop
        >   - path: /headers
        >     methods:
        >       - HEAD
        >     accessStrategies:
        >       - handler: allow
        >   - path: /.*
        >     methods:
        >       - GET
        >     accessStrategies:
        >       - handler: no_auth
        > ```





<a name="loiofefeb7fa13634c67ad2aebdaada5262c__postreq_bg1_msn_sfc"/>

## Next Steps

Next, adjust the obtained configuration of the APIRule to migrate it to version `v2`. To learn how to do this, follow the relevant tutorial:

-   [Migrating APIRule v1beta1 of Type jwt to Version v2](migrating-apirule-v1beta1-of-type-jwt-to-version-v2-bcaec91.md)
-   [Migrating APIRule v1beta1 of Type noop, allow, or no\_auth to Version v2](migrating-apirule-v1beta1-of-type-noop-allow-or-no-auth-to-version-v2-2b19ef5.md)
-   [Migrating APIRule v1beta1 of type oauth2\_introspection to version v2](migrating-apirule-v1beta1-of-type-oauth2-introspection-to-version-v2-394d18a.md)

