<!-- loiof8df238618eb4858905c2b42fa4ec815 -->

# APIRule Migration

Learn how to obtain the full `spec` of an APIRule in version `v1beta1` and migrate it to version `v2`.

The APIRule CustomResourceDefinition \(CRD\) in version `v1beta1` has been deprecated. Therefore, you must migrate all your APIRule custom resources \(CRs\) to version `v2`.

To identify which APIRules must be migrated, run the following command:

```
kubectl get apirules.gateway.kyma-project.io -A-o json | jq '.items[] | select(.metadata.annotations["gateway.kyma-project.io/original-version"] == "v1beta1") | {namespace: .metadata.namespace, name: .metadata.name}'
```

To retrieve the complete `spec` with the `rules` field of an APIRule in version `v1beta1`, see [Retrieving the Complete spec of an APIRule in Version v1beta1](retrieving-the-complete-spec-of-an-apirule-in-version-v1beta1-fefeb7f.md).

To migrate an APIRule from version `v1beta1` to version `v2`, follow the relevant guide:

-   [Migrating APIRule v1beta1 of Type jwt to Version v2](migrating-apirule-v1beta1-of-type-jwt-to-version-v2-bcaec91.md)
-   [Migrating APIRule v1beta1 of Type noop, allow, or no\_auth to Version v2](migrating-apirule-v1beta1-of-type-noop-allow-or-no-auth-to-version-v2-2b19ef5.md)
-   [Migrating APIRule v1beta1 of type oauth2\_introspection to version v2](migrating-apirule-v1beta1-of-type-oauth2-introspection-to-version-v2-394d18a.md)

For more information about APIRule `v2`, see also [APIRule `v2` Custom Resource](https://kyma-project.io/#/api-gateway/user/custom-resources/apirule/04-10-apirule-custom-resource) and [Changes Introduced in APIRule v2](changes-introduced-in-apirule-v2-aa34a4a.md).

