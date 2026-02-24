<!-- loio4d6a98cf1239433ba612bbb386e2f4cb -->

# Ingress and Egress IP Addresses

Learn how to check ingress and egress IP addresses for your Kyma runtime cluster. These addresses are needed to integrate with partner systems, enforce IP-based access controls, connect to external databases, and more.



## Egress IP Address



### How to Check the Egress IP

You can see the IP addresses for NAT Gateway that handles the egress traffic as values of the `cloud.natGatewayIps` parameter in the `kyma-info` ConfigMap in your Kyma instance.

To check the NAT IPs, use either Kyma dashboard or kubectl:

-   In Kyma dashboard, go to the *Cluster Overview* section.
-   With kubectl, run:

    ```
    kubectl --namespace kyma-system get configmap kyma-info -o json | jq -r '.data["cloud.natGatewayIps"]'
    ```




### Egress IP Stability

The NAT Gateway IP address is assigned when you create the Kyma runtime, and remains unchanged throughout the cluster's lifecycle.



## Ingress IP Address



### How to Check the Ingress IP

You can see the IP addresses for Istio Ingress Gateway that, by default, handles the ingress traffic. To get the LoadBalancer IP for `istio-ingressgateway`, run:

```
LOAD_BALANCER_ADDRESS=$(kubectl get services --namespace istio-system istio-ingressgateway --output jsonpath='{.status.loadBalancer.ingress[0].ip}')
if [[ -z $LOAD_BALANCER_ADDRESS ]]; then
    LOAD_BALANCER_ADDRESS=$(kubectl get services --namespace istio-system istio-ingressgateway --output jsonpath='{.status.loadBalancer.ingress[0].hostname}')
fi
echo "The load balancer address is ${LOAD_BALANCER_ADDRESS}"
```



### When the Ingress IP Is Assigned

When you create a Kyma runtime cluster and add the Istio module, the module deploys the `istio-ingressgateway` Service of type LoadBalancer. Then, Gardener creates a cloud LoadBalancer. When it is ready, its IP address appears in the `istio-ingressgateway` Service.

When you also enable the API Gateway module, it creates a default Gateway custom resource named `kyma-gateway`. This Gateway configures the `istio-ingressgateway` as the cluster’s ingress traffic entry point.

If the Istio module isn't enabled, the cluster doesn’t have the `istio-ingressgateway` Service, so there’s no ingress LoadBalancer IP. If the Istio module is enabled but the API Gateway module isn't, the `istio-ingressgateway` exists, but there's no default Gateway resource that routes external traffic through it. In that case, you must manually configure your own Gateway and related routing resources.



### Ingress IP Stability

The external ingress IP of the `istio-ingressgateway` LoadBalancer Service changes in these cases:

-   You delete the `istio-ingressgateway` LoadBalancer Service and recreate it.
-   You migrate from Elastic LoadBalancer to Network LoadBalancer.
-   You remove the Istio module \(which deletes the `istio-ingressgateway` Service\) and then add it again, which creates a new LoadBalancer.

In other cases, the ingress IP remains the same.

