<!-- loioce322f8e99ba4c389d3e1871dd1c3231 -->

# Manage Network Policies

Network policy support in the API Gateway module is disabled by default. Learn about the network policies for the API Gateway module and how to manage them.

When enabled, the API Gateway module creates the `kyma-project.io--api-gateway-allow` network policy. This policy allows only the following connections:

-   Egress to the `kube-dns` and `local-dns` workloads for in-cluster name resolution.
-   Egress to the Kubernetes API server on port `443`.
-   Ingress to the webhook port `9443`.
-   Ingress to the metrics port `8080` from external workloads labeled with `networking.kyma-project.io/metrics-scraping=allowed` or from other Kyma modules.

> ### Caution:  
> Since Oathkeeper support is deprecated, network policies don't cover Ory Oathkeeper connectivity. It's not recommended to use network policies when Ory Oathkeeper support is enabled. If you still use Ory Oathkeeper and wish to enable network policies, expose your workloads with `APIRule` resources in version *v2*.



<a name="loioce322f8e99ba4c389d3e1871dd1c3231__section_enable_network_policies"/>

## Enable Network Policies

To enable network policies, set the `networkPoliciesEnabled` field to *true* in the `APIGateway` custom resource:

```
kubectl patch apigateways.operator.kyma-project.io default --type=merge --patch='{"spec": {"networkPoliciesEnabled": true}}'
```



<a name="loioce322f8e99ba4c389d3e1871dd1c3231__section_disable_network_policies"/>

## Disable Network Policies

To disable network policies, set the `networkPoliciesEnabled` field to *false* in the `APIGateway` custom resource:

```
kubectl patch apigateways.operator.kyma-project.io default --type=merge --patch='{"spec": {"networkPoliciesEnabled": false}}'
```

> ### Caution:  
> If you disable network policies in supported clusters, the traffic to the API server or other critical workloads may be disrupted. Always consult your cluster configuration to choose the best solution.



<a name="loioce322f8e99ba4c389d3e1871dd1c3231__section_verify_status"/>

## Verify Status

To check if the network policies are active, run:

```
kubectl get networkpolicies -n kyma-system -l api-gateway.kyma-project.io/managed-by
```

