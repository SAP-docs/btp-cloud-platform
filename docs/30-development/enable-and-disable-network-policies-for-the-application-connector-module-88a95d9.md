<!-- loio88a95d9b190f42e68c6d05ba9d1352ce -->

# Enable and Disable Network Policies for the Application Connector Module

Learn about the network policies for the Application Connector module and how to enable and disable them.



## Context

To increase security, the Application Connector module creates network policies that control traffic to and from its Pods. All the policies are disabled by default. You can enable these policies using Kyma dashboard or kubectl.

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

Allows egress from the Application Connector module Pods to any destination on TCP port 443, such as the Kubernetes API server.

</td>
</tr>
<tr>
<td valign="top">

`kyma-project.io--acm-module-to-dns`

</td>
<td valign="top">

Allows egress from the Application Connector module Pods to DNS services on UDP/TCP ports 53 and 8053 for cluster and external DNS resolution.

</td>
</tr>
<tr>
<td valign="top">

`kyma-project.io--acm-module-allow-to-sidecar`

</td>
<td valign="top">

Allows egress from the Application Connector module Pods to Istio's istiod on TCP port 15012 for sidecar configuration.

</td>
</tr>
<tr>
<td valign="top">

`kyma-project.io--acm-module-allow-metrics`

</td>
<td valign="top">

Allows ingress to the Application Connector Manager Pods on TCP port 8080 from Pods in the `kyma-system` namespace labeled `networking.kyma-project.io/metrics-scraping: allowed` for metrics scraping.

</td>
</tr>
<tr>
<td valign="top">

`kyma-project.io--acm-module-allow-to-external-system`

</td>
<td valign="top">

Allows egress from the Compass Runtime Agent and Central Application Gateway Pods to external systems at 0.0.0.0/0, excluding link-local addresses.

</td>
</tr>
<tr>
<td valign="top">

`kyma-project.io--acm-gateway-allow-from-cluster-workload`

</td>
<td valign="top">

Allows ingress to the Central Application Gateway Pods on TCP ports 8080 and 8082 from any source within the cluster.

</td>
</tr>
<tr>
<td valign="top">

`kyma-project.io--acm-gateway-allow-from-health-check`

</td>
<td valign="top">

Allows ingress to the Central Application Gateway Pods on TCP port 8081 for health checks.

</td>
</tr>
<tr>
<td valign="top">

`kyma-project.io--acm-gateway-allow-to-external-system`

</td>
<td valign="top">

Allows egress from the Central Application Gateway Pods to external systems on TCP port 443.

</td>
</tr>
<tr>
<td valign="top">

`kyma-project.io--acm-validator-allow-from-istio-ingressgateway`

</td>
<td valign="top">

Allows ingress to the Validator Pods on TCP port 8080 from Istio Ingress Gateway in the `istio-system` namespace.

</td>
</tr>
<tr>
<td valign="top">

`kyma-project.io--acm-validator-allow-from-health-check`

</td>
<td valign="top">

Allows ingress to the Validator Pods on TCP port 8081 for health checks.

</td>
</tr>
<tr>
<td valign="top">

`kyma-project.io--acm-validator-allow-to-eventing`

</td>
<td valign="top">

Allows egress from the Validator Pods to the Eventing Publisher Proxy on TCP port 8080.

</td>
</tr>
<tr>
<td valign="top">

`kyma-project.io--acm-compass-allow-from-health-check`

</td>
<td valign="top">

Allows ingress to the Compass Runtime Agent Pods on TCP port 8090 for health checks.

</td>
</tr>
</table>



## Procedure

-   Use Kyma dashboard

    1.  Go to Kyma dashboard. The URL is in the *Overview* section of your subaccount.

    2.  Go to *Configuration* \> *Modules*.

    3.  Choose the *application-connector* module from the list, and switch to the *Edit* tab.

    4.  In the ApplicationConnector custom resource specification, find the `networkPoliciesEnabled` parameter. To enable all the network policies, change the parameter value to `true`. If the value is `false`, the network policies are disabled.


-   Use kubectl

    1.  To enable all the network policies for the Application Connector module, run the following command:

        ```
        kubectl patch applicationconnector applicationconnector-sample -n kyma-system \
          --type=merge \
          -p '{"spec":{"networkPoliciesEnabled": true}}'
        ```

    2.  To disable the network policies, run the following command:

        ```
        kubectl patch applicationconnector applicationconnector-sample -n kyma-system \
          --type=merge \
          -p '{"spec":{"networkPoliciesEnabled": false}}'
        ```

    3.  To check if the network policies are active, run the following command:

        ```
        kubectl get networkpolicies -n kyma-system -l kyma-project.io/module=application-connector
        ```



