<!-- loio8eccd49452b041bf913cf77d10ad4d17 -->

# Using the XFF Header to Configure IP-Based Access to a Workload

Expose your workload and configure IP-based access using the X-Forwarded-For \(XFF\) header. This helps to enhance security by ensuring that only trusted IPs can interact with your application.



<a name="loio8eccd49452b041bf913cf77d10ad4d17__prereq_ndk_whb_tcc"/>

## Prerequisites

-   You have the Istio and API Gateway modules added. See [Add and Delete a Kyma Module](../50-administration-and-ops/add-and-delete-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).
-   You have a deployed workload.
-   You have access to Kyma dashboard. Alternatively, to use CLI instructions, you must install [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl) and [curl](https://curl.se/).
-   You have [set up your custom domain](https://kyma-project.io/#/api-gateway/user/tutorials/01-10-setup-custom-domain-for-workload). Alternatively, you can use the default domain of your Kyma cluster and the default Gateway `kyma-system/kyma-gateway`.

    > ### Note:  
    > Because the default Kyma domain is a wildcard domain, which uses a simple TLS Gateway, it is recommended that you set up your custom domain for use in a production environment.

    > ### Tip:  
    > To learn what the default domain of your Kyma cluster is, run `kubectl get gateway -n kyma-system kyma-gateway -o jsonpath='{.spec.servers[0].hosts}`




## Context

The XFF header is a standard HTTP header that conveys the client IP address and the chain of intermediary proxies that the request traverses to reach the Istio service mesh. This is particularly useful when an application must be provided with the client IP address of an originating request, for example, for access control.

However, there are some technical limitations when using the XFF header. The header might not include all IP addresses if an intermediary proxy does not support modifying the header. Due to [technical limitations of AWS Classic ELBs](https://docs.aws.amazon.com/elasticloadbalancing/latest/classic/enable-proxy-protocol.html#proxy-protocol), when using an IPv4 connection, the header does not include the public IP of the load balancer in front of Istio Ingress Gateway. Moreover, Istio Ingress Gateway’s Envoy does not append the private IP address of the load balancer to the XFF header, effectively removing this information from the request. For more information on XFF, see the [IETF’s RFC documentation](https://datatracker.ietf.org/doc/html/rfc7239) and [Envoy documentation](https://www.envoyproxy.io/docs/envoy/latest/configuration/http/http_conn_man/headers#x-forwarded-for).

To use the XFF header, you must configure the corresponding settings in the Istio custom resource \(CR\). Then, expose your workload using an VirtualService CR and create an AuthorizationPolicy resource with allowed IP addresses specified in the `remoteIpBlocks` field. To learn how to do this, follow the procedure.



<a name="loio8eccd49452b041bf913cf77d10ad4d17__steps-unordered_a34_zx5_tcc"/>

## Procedure

-   Use Kyma dashboard.

    1.  Go to *Cluster Details* and choose *Modify Modules*.

    2.  Select the Istio module and choose *Edit*.

    3.  In the *General* section, add the number of trusted proxies.

        Due to the variety of network topologies, the Istio CR must specify the number of trusted proxies deployed in front of the Istio Ingress Gateway proxy, so that the client address can be extracted correctly.

    4.  If you use a Google Cloud or Microsoft Azure cluster, navigate to the *Gateway* section and set the Gateway traffic policy to *Local*. If you use a different cloud service provider, skip this step.

        > ### Caution:  
        > For production Deployments, it is strongly recommended to deploy Istio Ingress Gateway Pod to multiple nodes if you enable `externalTrafficPolicy : Local`. For more information, see [Network Load Balancer](https://istio.io/latest/docs/tasks/security/authorization/authz-ingress/#network).
        > 
        > Default Istio installation profile configures `PodAntiAffinity` to ensure that Ingress Gateway Pods are evenly spread across all nodes. This guarantees that the above requirement is satisfied if your IngressGateway autoscaling configuration `minReplicas` is equal to or greater than the number of nodes. You can configure autoscaling options in the Istio CR using the field `spec.config.components.ingressGateway.k8s.hpaSpec.minReplicas`.

        > ### Tip:  
        > If you use a Google Cloud or Microsoft Azure cluster, you can find your load balancer's IP address in the field `status.loadBalancer.ingress` of the `ingress-gateway` Service.

    5.  Choose *Save*.

    6.  Go to *Istio \> VirtualServices* and choose *Create*.

    7.  Switch to the *YAML* section and paste the following configuration:

        ```
        apiVersion: networking.istio.io/v1alpha3
        kind: VirtualService
        metadata:
          name: {VIRTUALSERVICE_NAME}
          namespace: {VIRTUALSERVICE_NAMESPACE}
        spec:
          hosts:
          - "{SERVICE_NAME}.{DOMAIN_NAME}"
          gateways:
          - {GATEWAY_NAME}/{GATEWAY_NAMESPACE}
          http:
          - match:
            - uri:
                prefix: /
            route:                      
            - destination:
                port:
                  number: {SERVICE_PORT}
                host: {SERVICE_NAME}.{SERVICE_NAMESPACE}.svc.cluster.local
        ```

        When you go to `https:/{SUBDOMAIN}.{DOMAIN}/{PATH}`, the response contains the `X-Forwarded-For` and `X-Envoy-External-Address` headers with your public IP address. See an example response for the Client IP *165.1.187.197*:

        ```
        {
          "args": {
            "show_env": "true"
          },
          "headers": {
            ...
        
            "X-Envoy-Attempt-Count": "...",
            "X-Envoy-External-Address": "165.1.187.197",
            "X-Forwarded-Client-Cert": "...",
            "X-Forwarded-For": "165.1.187.197",
            "X-Forwarded-Proto": "...",
            "X-Request-Id": "..."
          },
          "origin": "165.1.187.197",
          "url": "..."
        }
        ```

        > ### Tip:  
        > You can check your public IP address at [https://api.ipify.org](https://api.ipify.org/).

    8.  Go to *Istio \> Authorizaiton Policies* and choose *Create*.

    9.  Add a selector to specify the workload for which access should be configured.

    10. Add a rule with a `From` field.

    11. In the `RemoteIpBlocks` field, specify the IP addresses that should be allowed access to the workload.

    12. Choose *Create*.


-   Use kubectl.

    1.  In the following command, replace the placeholder with the number of trusted proxies deployed in front of the Istio Ingress Gateway proxy. Run the command.

        ```
        kubectl patch istios/default -n kyma-system --type merge -p '{"spec":{"config":{"numTrustedProxies": NUM_OF_TRUSTED_PROXIES}}}'
        ```

        Due to the variety of network topologies, the Istio CR must specify the configuration property `numTrustedProxies`, so that the client IP address can be extracted correctly.

    2.  If you use a Google Cloud or Microsoft Azure cluster, run the following command to set the traffic policy to *Local*. If you use a different cloud service provider, skip this step.

        ```
        kubectl patch istios/default -n kyma-system --type merge -p '{"spec":{"config":{"gatewayExternalTrafficPolicy": "Local"}}}'
        ```

        > ### Caution:  
        > For production Deployments, it is strongly recommended to deploy Istio Ingress Gateway Pod to multiple nodes if you enable `externalTrafficPolicy : Local`. For more information, see [Network Load Balancer](https://istio.io/latest/docs/tasks/security/authorization/authz-ingress/#network).
        > 
        > Default Istio installation profile configures `PodAntiAffinity` to ensure that Ingress Gateway Pods are evenly spread across all nodes. This guarantees that the above requirement is satisfied if your IngressGateway autoscaling configuration `minReplicas` is equal to or greater than the number of nodes. You can configure autoscaling options in the Istio CR using the field `spec.config.components.ingressGateway.k8s.hpaSpec.minReplicas`.

        > ### Tip:  
        > If you use a Google Cloud or Microsoft Azure cluster, you can find your load balancer's IP address in the field `status.loadBalancer.ingress` of the `ingress-gateway` Service.

    3.  To expose your workload, apply the following VirtualService resource.

        You can adjust this sample configuration and use another access strategy, according to your needs.

        ```
        cat <<EOF | kubectl apply -f -
        apiVersion: networking.istio.io/v1alpha3
        kind: VirtualService
        metadata:
          name: {VIRTUALSERVICE_NAME}
          namespace: {VIRTUALSERVICE_NAMESPACE}
        spec:
          hosts:
          - "{SERVICE_NAME}.{DOMAIN_NAME}"
          gateways:
          - {GATEWAY_NAME}/{GATEWAY_NAMESPACE}
          http:
          - match:
            - uri:
                prefix: /
            route:
            - destination:
                port:
                  number: {SERVICE_PORT}
                host: {SERVICE_NAME}.{SERVICE_NAMESPACE}.svc.cluster.local
        EOF
        ```

        When you go to `https:/{SUBDOMAIN}.{DOMAIN}/{PATH}`, the response contains the `X-Forwarded-For` and `X-Envoy-External-Address` headers with your public IP address. See an example response for the Client IP *165.1.187.197*:

        ```
        {
          "args": {
            "show_env": "true"
          },
          "headers": {
            ...
        
            "X-Envoy-Attempt-Count": "...",
            "X-Envoy-External-Address": "165.1.187.197",
            "X-Forwarded-Client-Cert": "...",
            "X-Forwarded-For": "165.1.187.197",
            "X-Forwarded-Proto": "...",
            "X-Request-Id": "..."
          },
          "origin": "165.1.187.197",
          "url": "..."
        }
        ```

        > ### Tip:  
        > You can check your public IP address at [https://api.ipify.org](https://api.ipify.org/).

    4.  To configure IP-based access to the exposed workload, create an AuthorizationPolicy resource.

        The selector specifies the workload for which access should be configured, and the `RemoteIpBlocks` field specifies the IP addresses for which access should be allowed.

        ```
        cat <<EOF | kubectl apply -f -
        apiVersion: security.istio.io/v1beta1
        kind: AuthorizationPolicy
        metadata:
          name: {AUTHORIZATIONPOLICY_NAME}
          namespace: {AUTHORIZATIONPOLICY_NAMESPACE}
        spec:
          action: ALLOW
          rules:
            - from:
                - source:
                    ipBlocks: []
                    remoteIpBlocks:
                      - {ALLOWED_IP}
          selector:
            matchLabels:
              {KEY}: {VALUE}
        EOF
        ```





<a name="loio8eccd49452b041bf913cf77d10ad4d17__result_fp2_lqb_1dc"/>

## Results

You have configured the XFF header in the Istio CR and exposed your workload to the internet. Access to the workload is limited to the IP addresses that you have specified.

