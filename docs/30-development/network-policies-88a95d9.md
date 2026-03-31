<!-- loio88a95d9b190f42e68c6d05ba9d1352ce -->

# Network Policies

Learn about the network policies for the Application Connector module.

To increase security, the Application Connector module creates network policies that control traffic to and from its Pods. All the policies are enabled by default and cannot be disabled.

**Network Policies for the Application Connector Module**


<table>
<tr>
<th valign="top">

Policy Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`kyma-project.io--acm-module-to-api-server`

</td>
<td valign="top">

Allows egress from the Application Connector module Pods to any destination on TCP port 443, such as the Kubernetes API server

</td>
</tr>
<tr>
<td valign="top">

`kyma-project.io--acm-module-to-dns`

</td>
<td valign="top">

Allows egress from the Application Connector module Pods to DNS services on UDP/TCP ports 53 and 8053 for cluster and external DNS resolution

</td>
</tr>
<tr>
<td valign="top">

`kyma-project.io--acm-module-allow-to-sidecar`

</td>
<td valign="top">

Allows egress from the Application Connector module Pods to Istio's istiod on TCP port 15012 for sidecar configuration

</td>
</tr>
<tr>
<td valign="top">

`kyma-project.io--acm-module-allow-metrics`

</td>
<td valign="top">

Allows ingress to the Application Connector Manager Pods on TCP port 8080 from Pods in the `kyma-system` namespace labeled `networking.kyma-project.io/metrics-scraping: allowed` for metrics scraping

</td>
</tr>
<tr>
<td valign="top">

`kyma-project.io--acm-module-allow-to-external-system`

</td>
<td valign="top">

Allows egress from the Compass Runtime Agent and Central Application Gateway Pods to external systems at 0.0.0.0/0, excluding link-local addresses

</td>
</tr>
<tr>
<td valign="top">

`kyma-project.io--acm-gateway-allow-from-cluster-workload`

</td>
<td valign="top">

Allows ingress to the Central Application Gateway Pods on TCP ports 8080 and 8082 from any source within the cluster

</td>
</tr>
<tr>
<td valign="top">

`kyma-project.io--acm-gateway-allow-from-health-check`

</td>
<td valign="top">

Allows ingress to the Central Application Gateway Pods on TCP port 8081 for health checks

</td>
</tr>
<tr>
<td valign="top">

`kyma-project.io--acm-gateway-allow-to-external-system`

</td>
<td valign="top">

Allows egress from the Central Application Gateway Pods to external systems on TCP port 443

</td>
</tr>
<tr>
<td valign="top">

`kyma-project.io--acm-validator-allow-from-istio-ingressgateway`

</td>
<td valign="top">

Allows ingress to the Validator Pods on TCP port 8080 from Istio Ingress Gateway in the `istio-system` namespace

</td>
</tr>
<tr>
<td valign="top">

`kyma-project.io--acm-validator-allow-from-health-check`

</td>
<td valign="top">

Allows ingress to the Validator Pods on TCP port 8081 for health checks

</td>
</tr>
<tr>
<td valign="top">

`kyma-project.io--acm-validator-allow-to-eventing`

</td>
<td valign="top">

Allows egress from the Validator Pods to the Eventing Publisher Proxy on TCP port 8080

</td>
</tr>
<tr>
<td valign="top">

`kyma-project.io--acm-compass-allow-from-health-check`

</td>
<td valign="top">

Allows ingress to the Compass Runtime Agent Pods on TCP port 8090 for health checks

</td>
</tr>
</table>



## Verify Status

To check if the network policies are active, run the following command:

```
kubectl get networkpolicies -n kyma-system -l kyma-project.io/module=application-connector
```

