<!-- loio2415e555b3bb484c9effebf88a9dcd66 -->

# Network Connectivity Diagnostics

If you're having trouble with network connectivity and don't know where to begin troubleshooting, follow these steps. The issues may not be directly related to Istio, but could be due to misconfigured Istio resources or other cluster resources.

Before starting the detailed analysis, perform these initial checks:

-   Verify the state of the `Istio` CR. If it is in the ***Warning*** state, check the warning message and conditions. It might help you begin the investigation.
-   Verify that no [NetworkPolicies](https://kubernetes.io/docs/concepts/services-networking/network-policies/) are affecting the connectivity by blocking traffic between Pods in the service mesh. To find all `NetworkPolicy` resources, run the command `kubectl get networkpolicies -A`.
-   The configuration of the following kinds of resources can affect the connectivity in the service mesh. Verify that those resources are configured as intended:
    -   [`DestinationRule`](https://istio.io/latest/docs/reference/config/networking/destination-rule/)
    -   [`PeerAuthentication`](https://istio.io/latest/docs/reference/config/security/peer_authentication/)
    -   [`Gateway`](https://istio.io/latest/docs/reference/config/networking/gateway/)
    -   [`AuthorizationPolicy`](https://istio.io/latest/docs/reference/config/security/authorization-policy/)
    -   [`RequestAuthentication`](https://istio.io/latest/docs/reference/config/security/request_authentication/)




<a name="loio2415e555b3bb484c9effebf88a9dcd66__section_global_analysis"/>

## 1. Global Analysis

As a starting point, run `istioctl analyze` to check the state of your mesh and point out common errors and misconfigurations.

Analyze a specific namespace:

```
istioctl analyze -n <your-namespace>
```

Analyze the entire cluster:

```
istioctl analyze --all-namespaces
```

What to look for:

-   **Errors and Warnings:** Review all output carefully, especially warnings like ***IST0133***, which indicate an `AuthorizationPolicy` might be blocking more traffic than intended. The analysis often includes the name and namespace of the problematic resource.



<a name="loio2415e555b3bb484c9effebf88a9dcd66__section_authorization_policies"/>

## 2. AuthorizationPolicies

Misconfigured `AuthorizationPolicy` resources are a common cause of access issues, such as ***403*** errors or unexpected connection timeouts.

List all `AuthorizationPolicy` resources in a namespace:

```
kubectl get authorizationpolicies -n <your-namespace>
```

List all `AuthorizationPolicy` resources cluster-wide:

```
kubectl get authorizationpolicies --all-namespaces
```

Describe a specific `AuthorizationPolicy` to see its details:

```
kubectl describe authorizationpolicy <policy-name> -n <namespace>
```

What to look for:

-   **Errors and Warnings**: Deny policies may block more traffic than intended. A deny rule without the `ports` field on an HTTP-based `hosts` rule can block all TCP traffic, not just HTTP.
-   **Allow policies**: If even a single allow policy matches a workload, all traffic that does not match any allow rule is denied. Make sure that all intended traffic is covered by allow rules.
-   **Scope**: Check the `selector` to see which workloads the policy applies to. An empty selector applies the policy to all workloads in the namespace.
-   **Rules**: Look at the `to`, `from`, and `when` clauses to understand what traffic is being allowed or denied.



<a name="loio2415e555b3bb484c9effebf88a9dcd66__section_request_authentications"/>

## 3. RequestAuthentications

`RequestAuthentication` defines how JSON Web Tokens \(JWTs\) are validated. Misconfigurations often lead to ***401 Unauthorized*** responses.

List all request authentications in a namespace:

```
kubectl get requestauthentications -n <your-namespace>
```

Describe a specific `RequestAuthentication` to see its configuration:

```
kubectl describe requestauthentication <ra-name> -n <namespace>
```

What to look for:

-   `jwksUri`: Ensure the JSON Web Key Set \(JWKS\) endpoint is correct and reachable from Istiod.
-   `issuer`: The `iss` claim in the JWT must match this value.
-   `audiences`: In case those are set, the `aud` claim in the JWT must match one of the values here.



<a name="loio2415e555b3bb484c9effebf88a9dcd66__section_envoy_filters"/>

## 4. EnvoyFilters

`EnvoyFilter` resources modify the Envoy configuration and can easily cause problems if misconfigured. They are often used for complex use cases.

List all `EnvoyFilter` resources cluster-wide:

```
kubectl get envoyfilters --all-namespaces
```

Examine a specific filter:

```
kubectl get envoyfilter <filter-name> -n <namespace> -o yaml
```

What to look for:

-   **Workload selector**: Check which Pods the filter applies to.
-   **Filters**: Look at the filter configuration. These are often complex Lua scripts or WASM filters. A bug in the script can break traffic.



<a name="loio2415e555b3bb484c9effebf88a9dcd66__section_envoy_configuration"/>

## 5. Envoy Configuration

If the previous steps don't reveal the issue, inspect the live Envoy configuration for a specific Pod. This shows exactly which rules Envoy applies.

Get the proxy config for a specific Pod:

```
istioctl proxy-config <all|listeners|clusters|routes|endpoints|bootstrap> <pod-name> -n <namespace>
```

For example, check the routes for a Pod:

```
istioctl proxy-config routes <pod-name>.<namespace> -o json
```

