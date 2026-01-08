<!-- loio2b19ef591fa54e04b20a31b63b677ac9 -->

# Migrating APIRule `v1beta1` of Type `noop`, `allow`, or `no_auth` to Version `v2`

Learn how to migrate an APIRule created in version `v1beta1` using the `noop`, `allow`, or `no_auth` handlers to version `v2`. In APIRule `v2`, the `noAuth` handler replaces all of the above handlers from the `v1beta1` version.



<a name="loio2b19ef591fa54e04b20a31b63b677ac9__prereq_kwf_rvn_sfc"/>

## Prerequisites

-   You have read [Changes Introduced in APIRule v2](changes-introduced-in-apirule-v2-aa34a4a.md), which details the updates implemented in the new version of APIRule. If any of these changes affect your setup, you must consider them when migrating to APIRule `v2` and make the necessary adjustments.
-   You have the Istio and API Gateway modules added.
-   You have installed [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl) and [curl](https://curl.se/).
-   You have a deployed workload exposed by an APIRule in the deprecated `v1beta1` version. The APIRule uses the `noop`, `allow`, or `no_auth` handler.

    > ### Note:  
    > To expose a workload using APIRule in version `v2`, the workload must be a part of the Istio service mesh. See [Enabling Istio Sidecar Proxy Injection](enabling-istio-sidecar-proxy-injection-b3c6f1d.md).




<a name="loio2b19ef591fa54e04b20a31b63b677ac9__context_ylm_mt4_tfc"/>

## Context

APIRule in version `v1beta1` is deprecated and scheduled for removal. Once the APIRule custom resource definition \(CRD\) stops serving version `v1beta1`, the API server will no longer respond to requests for APIRules in this version. As a result, you will encounter errors when attempting to access the APIRule custom resource using the deprecated `v1beta1` version. Therefore, you must migrate to version `v2`.

This example demonstrates a migration from an APIRule `v1beta1` with `noop`, `allow`, and `no_auth` handlers to an APIRule `v2` with the `noAuth` handler. The example uses an HTTPBin service, exposing the `/anything`, `/headers`, and `/.*` endpoints. The HTTPBin service is deployed in its own namespace, with Istio enabled, ensuring the workload is part of the Istio service mesh.



## Procedure

1.  Retrieve a configuration of the APIRule in version `v1beta1` and save it for further modifications. For instructions, see [Retrieving the Complete spec of an APIRule in Version v1beta1](retrieving-the-complete-spec-of-an-apirule-in-version-v1beta1-fefeb7f.md).

    See a sample of the retrieved `spec` in the YAML format. The following configuration uses these handlers to expose the HTTPBin endpoints:

    -   The `noop` handler to expose `/anything`
    -   The `allow` handler to expose `/headers`
    -   The `no_auth` handler to expose `/.*`

    > ### Sample Code:  
    > ```
    > host: httpbin.local.kyma.dev
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

2.  Adjust the obtained configuration to match the `v2` APIRule specification by replacing the `noop`, `allow`, and `no_auth` handlers with the `noAuth` handler.

    To do this, you must modify the existing APIRule `spec` and ensure it is valid for the `v2` version of the `noAuth` type. See an example of the adjusted APIRule:

    > ### Sample Code:  
    > ```
    > apiVersion: gateway.kyma-project.io/v2
    > kind: APIRule
    > metadata:
    >   name: httpbin
    >   namespace: test
    > spec:
    >   hosts:
    >     - httpbin
    >   service:
    >     name: httpbin
    >     namespace: test
    >     port: 8000
    >   gateway: kyma-system/kyma-gateway
    >   rules:
    >     - path: /anything
    >       methods: ["POST"]
    >       noAuth: true
    >     - path: /headers
    >       methods: ["HEAD"]
    >       noAuth: true      
    >     - path: /{**}
    >       methods: ["GET"]
    >       noAuth: true
    > ```

    > ### Note:  
    > The `hosts` field accepts a short host name \(without a domain\). Additionally, the path `/.*` has been changed to `/{**}` because APIRule `v2` does not support regular expressions in the `spec.rules.path` field.
    > 
    > For more information, see [Changes Introduced in APIRule v2](changes-introduced-in-apirule-v2-aa34a4a.md).

3.  To update the APIRule to version `v2`, apply the adjusted configuration.

    To verify the version of the applied APIRule, check the value of the `gateway.kyma-project.io/original-version` annotation in the APIRule `spec`. If the APIRule has been successfully migrated, you see the value `v2`. Use the following command:

    ```
    kubectl get apirules.gateway.kyma-project.io -n $NAMESPACE $APIRULE_NAME -oyaml
    ```

    The following output indicates that the APIRule has been successfully migrated to version `v2`:

    > ### Sample Code:  
    > ```
    > apiVersion: gateway.kyma-project.io/v2
    > kind: APIRule
    > metadata:
    >   annotations:
    >     gateway.kyma-project.io/original-version: v2
    > ...
    > ```

    > ### Caution:  
    > Do not manually change the `gateway.kyma-project.io/original-version` annotation. This annotation is automatically updated when you apply your APIRule in version `v2`. Modifying the annotation's value manually causes your APIRule `v1beta1` to be handled and configured as version `v2`, potentially leading to reconciliation errors.

4.  To preserve the internal traffic policy from the APIRule `v1beta1`, you must apply the following AuthorizationPolicy.

    In APIRule `v2`, internal traffic is blocked by default. Without this AuthorizationPolicy, attempts to connect internally to the workload cause an `RBAC: access denied` error. Ensure that the selector label is updated to match the target workload.


    <table>
    <tr>
    <th valign="top">

    Option
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *\{NAMESPACE\}*
    
    </td>
    <td valign="top">
    
    The namespace to which the AuthorizationPolicy applies. This namespace must include the target workload for which you allow internal traffic. The selector matches workloads in the same namespace as the AuthorizationPolicy.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *\{LABEL\_KEY\}: \{LABEL\_VALUE\}*
    
    </td>
    <td valign="top">
    
    To further restrict the scope of the AuthorizationPolicy, specify label selectors that match the target workload. Replace these placeholders with the actual key and value of the label. The label indicates a specific set of Pods to which a policy should be applied. The scope of the label search is restricted to the configuration namespace in which the AuthorizationPolicy is present.

    For more information, see [Authorization Policy](https://istio.io/latest/docs/reference/config/security/authorization-policy/).
    
    </td>
    </tr>
    </table>
    
    ```
    apiVersion: security.istio.io/v1
    kind: AuthorizationPolicy
    metadata:
      name: allow-internal
      namespace: {NAMESPACE}
    spec:
      selector:
        matchLabels:
          {LABEL_KEY}: {LABEL_VALUE} 
      action: ALLOW
      rules:
      - from:
        - source:
            notPrincipals: ["cluster.local/ns/istio-system/sa/istio-ingressgateway-service-account"]
    ```

5.  To retain the CORS configuration from the APIRule `v1beta1`, update the APIRule in version `v2` to include the same CORS settings.

    For preflight requests to work correctly, you must explicitly add the `"OPTIONS"` method to the `rules.methods` field of your APIRule `v2`. For guidance, see the [sample APIRule CRs](https://kyma-project.io/#/api-gateway/user/custom-resources/apirule/04-10-apirule-custom-resource?id=sample-custom-resource).

    > ### Remember:  
    > If you migrated multiple APIRules that target the same workload, and you applied an additional AuthorizationPolicy to avoid traffic disruption during migration, delete it. For instructions, see the last point of the procedure [Migrate Multiple APIRules Targeting the Same Workload from v1beta1 to v2](migrate-multiple-apirules-targeting-the-same-workload-from-v1beta1-to-v2-b897dd3.md).




<a name="loio2b19ef591fa54e04b20a31b63b677ac9__result_zrb_2xn_sfc"/>

## Results

You have migrated your APIRule CR to version `v2`. Now, access your workload:

-   Send a `POST` request to the exposed workload:

    > ### Sample Code:  
    > ```
    > Send a POST request to the exposed workload:
    > ```

    If successful, the call returns the `200 OK` response code.

-   Send a `HEAD` request to the exposed workload:

    > ### Sample Code:  
    > ```
    > curl -ik -I https://{SUBDOMAIN}.{DOMAIN_NAME}/headers
    > ```

    If successful, the call returns the `200 OK` response code.

-   Send a `GET` request to the exposed workload:

    > ### Sample Code:  
    > ```
    > curl -ik -X GET https://{SUBDOMAIN}.{DOMAIN_NAME}/ip
    > ```

    If successful, the call returns the `200 OK` response code.


