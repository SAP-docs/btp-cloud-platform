<!-- loiof8df238618eb4858905c2b42fa4ec815 -->

# Migrate `APIRule` from Version *v1beta1* to Version *v2*

`APIRule` custom resource \(CR\) *v1beta1* is deleted. You must migrate all your `APIRule` CRs to version *v2*. Learn how to perform the migration.



<a name="loiof8df238618eb4858905c2b42fa4ec815__context_migration_intro"/>

## Context

> ### Caution:  
> `APIRule` CRD *v2* is the latest stable version.
> 
> -   You can no longer create, edit, or delete `APIRule`s using *v1beta1* API. Existing configurations continue to function as expected, but to make any changes, migrate to version *v2*.
> -   `APIRule`s *v1beta1* are no longer visible in Kyma dashboard. You can still view them with `kubectl`, but they display in the converted *v2* format.
> -   Reconciliation of `APIRules` *v1beta1* is disabled, and the API Gateway module no longer manages them. Migrating to version *v2* may temporarily disrupt workload availability and access.
> 
> For the `APIRule` deletion timeline for SAP BTP, Kyma runtime, see [API Gateway What's New notes](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?locale=en-US&version=Cloud&q=api+gateway+module).



## Procedure

-   To migrate to version `v2`, follow these steps:

    1.  To identify which `APIRule`s must be migrated, run the following command:

        ```
        kubectl get apirules.gateway.kyma-project.io -A -o json | jq '.items[] | select(.metadata.annotations["gateway.kyma-project.io/original-version"] == "v1beta1") | {namespace: .metadata.namespace, name: .metadata.name}'
        ```

    2.  If two or more of your `APIRule`s target the same workload, apply an additional `AuthorizationPolicy` to avoid traffic disruption during migration. See [Migrate Multiple APIRules Targeting the Same Workload from v1beta1 to v2](migrate-multiple-apirules-targeting-the-same-workload-from-v1beta1-to-v2-b897dd3.md).

    3.  To retrieve the complete `spec` with the `rules` field of an `APIRule` in version *v1beta1*, see [Retrieve the Complete spec of an APIRule in Version v1beta1](retrieve-the-complete-spec-of-an-apirule-in-version-v1beta1-fefeb7f.md).

    4.  To migrate an `APIRule` from version *v1beta1* to version *v2*, follow the relevant guide:


    -   [Migrate APIRule v1beta1 of Type jwt to Version v2](migrate-apirule-v1beta1-of-type-jwt-to-version-v2-bcaec91.md)

    -   [Migrate APIRule v1beta1 of Type noop, allow, or no\_auth to Version v2](migrate-apirule-v1beta1-of-type-noop-allow-or-no-auth-to-version-v2-2b19ef5.md)

    -   [Migrate APIRule v1beta1 of Type oauth2\_introspection to Version v2](migrate-apirule-v1beta1-of-type-oauth2-introspection-to-version-v2-394d18a.md)


-   To delete `APIRule`s *v1beta1*, use *v2* API:

    ```
    kubectl delete apirules.v2.gateway.kyma-project.io -n $NAMESPACE $APIRULE_NAME -oyaml
    ```


**Related Information**  


[Changes Introduced in APIRule v2](changes-introduced-in-apirule-v2-aa34a4a.md "Learn about the changes that APIRule v2 introduces and the actions you must take to adjust your v1beta1 resources.")

