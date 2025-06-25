<!-- loio4dea5d550b3d4b85b879d4def33f0a9c -->

# Exposing and Securing Workloads with extAuth

Expose and secure your workload using the `extAuth` access strategy.



<a name="loio4dea5d550b3d4b85b879d4def33f0a9c__prereq_adk_mv3_x2c"/>

## Prerequisites

-   You have the Istio and API Gateway modules added. See [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).
-   You have installed [curl](https://curl.se/) and [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl). You have configured kubectl to communicate with your Kyma runtime instance. See [Access a Kyma Instance Using kubectl](access-a-kyma-instance-using-kubectl-3e25944.md).
-   You have a deployed workload.

    > ### Note:  
    > To expose a workload using APIRule in version `v2`, the workload must be a part of the Istio service mesh. See [Enabling Istio Sidecar Proxy Injection](enabling-istio-sidecar-proxy-injection-b3c6f1d.md).

-   You have [set up your custom domain](https://kyma-project.io/#/api-gateway/user/tutorials/01-10-setup-custom-domain-for-workload). Alternatively, you can use the default domain of your Kyma cluster and the default Gateway `kyma-system/kyma-gateway`.

    > ### Note:  
    > Because the default Kyma domain is a wildcard domain, which uses a simple TLS Gateway, it is recommended that you set up your custom domain for use in a production environment.

    > ### Tip:  
    > To learn what the default domain of your Kyma cluster is, run the following command:
    > 
    > ```
    > kubectl get gateway -n kyma-system kyma-gateway -o jsonpath='{.spec.servers[0].hosts}'
    > ```

-   You have a JSON Web Token \(JWT\). See [Get a JWT](https://kyma-project.io/#/api-gateway/user/tutorials/01-50-expose-and-secure-a-workload/01-51-get-jwt).



## Context

Learn how to expose and secure services using APIGateway Controller and OAuth2.0 Client Credentials flow. For this purpose, this task uses [`oauth2-proxy`](https://oauth2-proxy.github.io/oauth2-proxy/) with an OAuth2.0 complaint authorization server supporting OIDC discovery. APIGateway Controller reacts to an instance of the APIRule custom resource \(CR\) and creates an Istio [VirtualService](https://istio.io/latest/docs/reference/config/networking/virtual-service/) and [AuthorizationPolicy](https://istio.io/latest/docs/reference/config/security/authorization-policy/) with action type `CUSTOM`.



## Procedure

1.  Replace the placeholders and define the `oauth2-proxy` configuration for your authorization server.

    > ### Tip:  
    > To generate `COOKIE_SECRET` and `CLIENT_SECRET`, you can use the command `openssl rand -base64 32 | head -c 32 | base64`.

    > ### Tip:  
    > You can adapt this configuration to better suit your needs. See the [additional configuration parameters](https://oauth2-proxy.github.io/oauth2-proxy/configuration/overview/#config-options).

    ```
    cat <<EOF > values.yaml
    config:
      clientID: {CLIENT_ID}
      clientSecret: {CLIENT_SECRET}
      cookieName: ""
      cookieSecret: {COOKIE_SECRET}
    
    extraArgs: 
      auth-logging: true
      cookie-domain: "{DOMAIN_TO_EXPOSE_WORKLOADS}"
      cookie-samesite: lax
      cookie-secure: false
      force-json-errors: true
      login-url: static://401
      oidc-issuer-url: {OIDC_ISSUER_URL}
      pass-access-token: true
      pass-authorization-header: true
      pass-host-header: true 
      pass-user-headers: true
      provider: oidc
      request-logging: true
      reverse-proxy: true
      scope: "{TOKEN_SCOPES}"
      set-authorization-header: true
      set-xauthrequest: true
      skip-jwt-bearer-tokens: true
      skip-oidc-discovery: false
      skip-provider-button: true
      standard-logging: true
      upstream: static://200
      whitelist-domain: "*.{DOMAIN_TO_EXPOSE_WORKLOADS}:*"
    EOF
    ```

2.  To install `oauth2-proxy` with your configuration, use [oauth2-proxy helm chart](https://github.com/oauth2-proxy/manifests):

    ```
    kubectl create namespace oauth2-proxy
    helm repo add oauth2-proxy https://oauth2-proxy.github.io/manifests
    helm upgrade --install oauth2-proxy oauth2-proxy/oauth2-proxy -f values.yaml -n oauth2-proxy
    ```

3.  Register `oauth2-proxy` as an authoriation provider in the Istio module.

    ```
    kubectl patch istio -n kyma-system default --type merge --patch '{"spec":{"config":{"authorizers":[{"name":"oauth2-proxy","port":80,"service":"oauth2-proxy.oauth2-proxy.svc.cluster.local","headers":{"inCheck":{"include":["x-forwarded-for", "cookie", "authorization"]}}}]}}}'
    
    ```

4.  To expose and secure the Service, create the following APIRule:

    ```
    cat <<EOF | kubectl apply -f -
    apiVersion: gateway.kyma-project.io/v2alpha1
    kind: APIRule
    metadata:
      name: {APIRULE_NAME}
      namespace: {APIRULE_NAMESPACE}
    spec:
      hosts: 
        - {SUBDOMAIN}.{DOMAIN_TO_EXPOSE_WORKLOADS}
      service:
        name: {SERVICE_NAME}
        port: {SERVICE_PORT}
      gateway: {GATEWAY_NAME}/{GATEWAY_NAMESPACE}
      rules:
        - extAuth:
            authorizers:
              - oauth2-proxy
          methods:
            - GET
          path: /*
    EOF
    ```

5.  To call the endpoint, send a `GET` request to the exposed Service:

    1.  To call the endpoint, send a `GET` request to the exposed Service:

        ```
        curl -ik -X GET https://{SUBDOMAIN}.{DOMAIN_TO_EXPOSE_WORKLOADS}/headers
        ```

        You get the `401 Unauthorized` response code.


    1.  Now, access the secured workload using the correct JWT.

        ```
        curl -ik -X GET https://{SUBDOMAIN}.{DOMAIN_TO_EXPOSE_WORKLOADS}/headers --header "Authorization:Bearer {ACCESS_TOKEN}"
        ```

        You get the `200 OK` response code.



