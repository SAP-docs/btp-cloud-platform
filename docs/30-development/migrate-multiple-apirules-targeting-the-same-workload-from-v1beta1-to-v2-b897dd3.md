<!-- loiob897dd34bf4449d5a9fff6943191e1ab -->

# Migrate Multiple APIRules Targeting the Same Workload from v1beta1 to v2

Learn how to migrate multiple APIRules `v1beta1` that expose the same workload using different host names. To keep all endpoints available during migration, you must create an additional, temporary AuthorizationPolicy. This ensures that service requests to APIRules `v1beta1` are handled as intended, while another APIRule targeting the same workload has already been migrated to `v2`.



## Context

When you have multiple APIRules `v1beta1` that expose the same workload but use different host values, and you migrate only one of those APIRules to version `v2`, you may get `HTTP/2 403 RBAC: Access Denied` errors when making requests to the endpoints of the remaining `v1beta1` APIRules. However, requests to the endpoint of the migrated `v2` APIRule are successful, returning `HTTP/2 200 OK` responses.

`HTTP/2 403 RBAC: Access Denied` errors are caused by Istio subresources created by the migrated APIRule `v2`. Because the other APIRules exposing the same workload remain in version `v1beta1` and do not use Istio subresources, requests from these APIRules `v1beta1` to the workload are no longer allowed. In such cases, access to the target workload is permitted only for requests that match the rules specified in the APIRule `v2`.

For example, suppose a scenario where you have applied the following two `v1beta1` APIRules configured to expose the same HTTPBin Service, each with a different host value, and you want to maintain uninterrupted access to service endpoints during migration.

```
apiVersion: gateway.kyma-project.io/v1beta1
kind: APIRule
metadata:
  name: example1
  namespace: test
spec:
  host: example1
  service:
    name: httpbin
    namespace: default
    port: 8000
  gateway: kyma-gateway.kyma-system
  rules:
    - path: /post
      methods: ["POST"]
      accessStrategies:
        - handler: no_auth
    - path: /.*
      methods: ["GET"]
      mutators: []
      accessStrategies:
        - handler: jwt
          config:
            trusted_issuers:
              - https://${IAS_TENANT}.accounts.ondemand.com
            jwks_urls:
              - https://${IAS_TENANT}.accounts.ondemand.com/oauth2/certs
---
apiVersion: gateway.kyma-project.io/v1beta1
kind: APIRule
metadata:
  name: example2
  namespace: test
spec:
  host: example2
  service:
    name: httpbin
    namespace: default
    port: 8000
  gateway: kyma-gateway.kyma-system
  rules:
    - path: /post
      methods: ["POST"]
      accessStrategies:
        - handler: no_auth
    - path: /.*
      methods: ["GET"]
      mutators: []
      accessStrategies:
        - handler: jwt
          config:
            trusted_issuers:
              - https://${IAS_TENANT}.accounts.ondemand.com
            jwks_urls:
              - https://${IAS_TENANT}.accounts.ondemand.com/oauth2/certs
```

To ensure a seamless migration to `v2` without any downtime, you must create an additional, temporary AuthorizationPolicy before applying the first migrated APIRule `v2`. To learn how to do this, follow the procedure.

> ### Note:  
> Using both versions of APIRules for one target workload is not recommended. Instead, migrate all APIRules targeting the same workload at once to version `v2`. Creating a temporary AuthorizationPolicy blocks internal traffic to the workload, which migration to APIRule `v2` causes anyway. Get acquainted with every step of the migration guides. Note that any ALLOW-type AuthorizationPolicy automatically blocks traffic that doesn't meet the requirements of policies specified there.
> 
> We recommend the following course of action:
> 
> 1.  Apply the temporary AuthorizationPolicy that blocks in-cluster communication and unblocks `v1beta1` exposure to external traffic during the migration.
> 2.  Migrate APIRules to `v2`. For instructions, follow the [APIRule Migration](apirule-migration-f8df238.md).
> 3.  Delete the temporary AuthorizationPolicy.



## Procedure

1.  For each of your APIRules `v1beta1` targeting the same workload, list hosts that contain at least one `allow` or `no_auth` handler. Specify those hosts in the FQDN format.

    > ### Note:  
    > If your APIRules `v1beta1` don't use the `allow` or `no_auth` handlers, skip this step. Specifying these hosts is only necessary for APIRules with `allow` or `no_auth` access strategies to allow traffic from Istio ingress gateway to the target workload during migration. Other handlers, such as `jwt`, `oauth2_introspection`, and `noop`, use the Ory Oathkeeper service, and the traffic doesn't come directly from the ingress gateway to the target workload.

    > ### Example:  
    > In the example, two APIRules `v1beta1` with `no_auth` handler expose the same `httpbin` Service on different hosts: `example1` and `example2`.
    > 
    > To obtain the FQDN format of the hosts, get the domain of the referenced Gateway. For this, you use the following command:
    > 
    > ```
    > kubectl get gateway ${GATEWAY_NAME} -n ${GATEWAY_NAMESPACE} -o jsonpath='{.spec.servers[0].hosts}'
    > ```
    > 
    > In the example scenario, the APIRules reference the `kyma-gateway` Gateway in the namespace `kyma-system`, so the command looks like this:
    > 
    > ```
    > kubectl get gateway -n kyma-system kyma-gateway -o jsonpath='{.spec.servers[0].hosts}'
    > ["*.local.kyma.dev"]%
    > ```
    > 
    > Assuming the default domain is `local.kyma.dev`, the FQDN format of the hosts is:
    > 
    > -   `example1.local.kyma.dev`
    > -   `example2.local.kyma.dev`

2.  To identify the label key and value for the target workload, check the selector from the Service that the APIRules expose.

    ```
    kubectl get service ${SERVICE_NAME} -n ${NAMESPACE} -o jsonpath='{.spec.selector}'
    ```

    > ### Example:  
    > In the example, the selector for the `httpbin` Service in the `default` namespace is `app: httpbin`:
    > 
    > ```
    > kubectl get service httpbin -n default -o jsonpath='{.spec.selector}'
    > {"app":"httpbin"}%
    > ```

3.  Create a temporary AuthorizationPolicy using the gathered information in the previous steps.


    <table>
    <tr>
    <th valign="top">

     
    
    </th>
    <th valign="top">

     
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `${NAMESPACE}`
    
    </td>
    <td valign="top">
    
    The namespace to which the AuthorizationPolicy applies. This namespace must include the target workload for which you allow traffic. The selector matches workloads in the same namespace as the AuthorizationPolicy.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `${HOSTNAME}`
    
    </td>
    <td valign="top">
    
    List all host names that are exposed by the `v1beta1` APIRules being migrated which contain handler `no_auth` or `allow`. These hostnames represent the external endpoints through which clients access the workload. List all relevant hostnames in FQDN format to ensure the AuthorizationPolicy allows traffic for each endpoint during migration.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `${LABEL_KEY}: ${LABEL_VALUE}`
    
    </td>
    <td valign="top">
    
    To further restrict the scope of the AuthorizationPolicy, specify label selectors that match the target workload. Replace these placeholders with the actual key and value of the label. The label indicates a specific set of Pods to which a policy should be applied. The scope of the label search is restricted to the configuration namespace in which the AuthorizationPolicy is present.

    For more information, see [Authorization Policy](https://istio.io/latest/docs/reference/config/security/authorization-policy/).
    
    </td>
    </tr>
    </table>
    
    This AuthorizationPolicy allows traffic from the Ory Oathkeeper service and the Istio ingress gateway to the target workload only for the specified hosts. Applying this AuthorizationPolicy before starting the migration process ensures uninterrupted access to service endpoints during the migration

    ```
    apiVersion: security.istio.io/v1
    kind: AuthorizationPolicy
    metadata:
      name: allow-migration
      namespace: ${NAMESPACE}
    spec:
      action: ALLOW
      rules:
        - from:
            - source:
                principals:
                  - "cluster.local/ns/kyma-system/sa/oathkeeper-maester-account"
        - from:
            - source:
                principals:
                  - "cluster.local/ns/istio-system/sa/istio-ingressgateway-service-account"
          to:
            - operation:
                hosts:
                  - ${HOSTNAME1}
                  - ${HOSTNAME2}
      selector:
        matchLabels:
          ${LABEL_KEY}: ${LABEL_VALUE}
    ```

    If you don't migrate any APIRules `v1beta1` with `allow` or `allow` handlers, remove the second rule from the AuthorizationPolicy. The AuthorizationPolicy then allows all traffic from the Ory Oathkeeper service to the target workload.

    ```
    apiVersion: security.istio.io/v1
    kind: AuthorizationPolicy
    metadata:
      name: allow-migration
      namespace: ${NAMESPACE}
    spec:
      action: ALLOW
      rules:
        - from:
            - source:
                principals:
                  - "cluster.local/ns/kyma-system/sa/oathkeeper-maester-account"
      selector:
        matchLabels:
          ${LABEL_KEY}: ${LABEL_VALUE}
    ```

    If you migrate APIRules `v1beta1` that specify only the `allow` or `no_auth` handlers, remove the first rule from the AuthorizationPolicy. The policy then allows all traffic from the ingress gateway to the target workload for the specified hosts.

    ```
    apiVersion: security.istio.io/v1
    kind: AuthorizationPolicy
    metadata:
      name: allow-migration
      namespace: ${NAMESPACE}
    spec:
      action: ALLOW
      rules:
        - from:
            - source:
                principals:
                  - "cluster.local/ns/istio-system/sa/istio-ingressgateway-service-account"
          to:
            - operation:
                hosts:
                  - ${HOSTNAME1}
                  - ${HOSTNAME2}
      selector:
        matchLabels:
          ${LABEL_KEY}: ${LABEL_VALUE}
    ```

    > ### Example:  
    > In the example scenario, APIRules `v1beta1` specify both `no_auth` and `jwt` handlers. Therefore, the temporarily applied AuthorizationPolicy looks like this:
    > 
    > ```
    > apiVersion: security.istio.io/v1
    > kind: AuthorizationPolicy
    > metadata:
    >   name: allow-migration
    >   namespace: default
    > spec:
    >   action: ALLOW
    >   rules:
    >     - from:
    >         - source:
    >             principals:
    >               - "cluster.local/ns/kyma-system/sa/oathkeeper-maester-account"
    >     - from:
    >         - source:
    >             principals:
    >               - "cluster.local/ns/istio-system/sa/istio-ingressgateway-service-account"
    >       to:
    >         - operation:
    >             hosts:
    >               - example1.local.kyma.dev
    >               - example2.local.kyma.dev
    >   selector:
    >     matchLabels:
    >       app: httpbin
    > ```

4.  To migrate APIRules `v1beta1` to `v2`, follow the steps in [APIRule Migration](apirule-migration-f8df238.md). During this process, the temporary AuthorizationPolicy ensures that requests from both `v1beta1` APIRules to the target workload are allowed.

5.  After all APIRules targeting the same workload are migrated to `v2`, delete the temporary AuthorizationPolicy.

    ```
    kubectl delete authorizationpolicy ${AUTHORIZATION_POLICY_NAME} -n ${NAMESPACE}
    ```

    > ### Example:  
    > See an example:
    > 
    > ```
    > kubectl delete authorizationpolicy allow-migration -n default
    > ```


