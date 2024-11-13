<!-- loio2415e555b3bb484c9effebf88a9dcd66 -->

# Network Connectivity - Basic Diagnostics

If you're having trouble with network connectivity and don't know where to begin troubleshooting, follow these steps. The issues may not be directly related to Istio, but could be due to misconfigured Istio resources or other cluster resources.

-   Verify the state of the Istio custom resource. If it is in the ***Warning*** state, check the warning message and conditions.
-   Verify that no `NetworkPolicy` resources affect the connectivity by blocking traffic between Pods in the service mesh. To get all `NetworkPolicy` resources, run the command `kubectl get networkpolicies -A`.
-   The configuration of the following kinds of resources might affect the connectivity in the service mesh. Verify that these resources are configured as intended:
    -   [DestinationRule](https://istio.io/latest/docs/reference/config/networking/destination-rule/)
    -   [PeerAuthentication](https://istio.io/latest/docs/reference/config/security/peer_authentication/)
    -   [Gateway](https://istio.io/latest/docs/reference/config/networking/gateway/)
    -   [AuthorizationPolicy](https://istio.io/latest/docs/reference/config/security/authorization-policy/)
    -   [RequestAuthentication](https://istio.io/latest/docs/reference/config/security/request_authentication/)

-   To check for potential issues in the Istio configuration and see suggestions on how to fix them, run the command `istioctl analyze -A`.
-   To enable the access logs of the Envoy proxy, follow the guide [Envoy Access Logs](https://istio.io/latest/docs/tasks/observability/logs/access-log/). In the access logs, you can find the field `response_flags`. The response flags DC \(Downstream client terminated connection\) and UC \(Upstream terminated connection\) are not within the scope of the Istio module, as they relate to the behavior of the client \(DC\) or the workload application \(UC\).

