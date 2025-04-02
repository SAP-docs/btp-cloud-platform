<!-- loiof2e9bf2be2714186b4231decd62a160b -->

# Exposing Workloads Using oauth2-proxy

Learn how to configure [oauth2-proxy](https://github.com/oauth2-proxy/manifests/tree/main/helm/oauth2-proxy) external authorization provider in the Istio custom resource \(CR\).



<a name="loiof2e9bf2be2714186b4231decd62a160b__prereq_dl3_m44_vcc"/>

## Prerequisites

-   You have the Istio module added. If you use a Kyma domain to expose a workload, also the API Gateway module must be added. See [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).
-   You have installed [Helm](https://helm.sh/docs/intro/install/).
-   You have a deployed workload.



<a name="loiof2e9bf2be2714186b4231decd62a160b__context_fzk_14y_ycc"/>

## Context

The Istio CR allows configuring external authorization providers that operate over HTTP. To set up the oauth2-proxy external authorization provider in the Istio CR and expose your workload using an Istio VirtualService, follow these steps.



## Procedure

1.  Export the following values as environment variables:

    ```
    export WORKLOAD_NAME={WORKLOAD_NAME}
    export NAMESPACE={WORKLOAD_NAMESPACE}
    export DOMAIN_TO_EXPOSE_WORKLOADS={YOUR_DOMAIN}
    export GATEWAY={YOUR_GATEWAY}
    ```


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
    
    **WORKLOAD\_NAME**
    
    </td>
    <td valign="top">
    
    The name of your workload.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **NAMESPACE**
    
    </td>
    <td valign="top">
    
    The name of your workload's namespace.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **DOMAIN\_TO\_EXPOSE\_WORKLOADS**
    
    </td>
    <td valign="top">
    
    The domain that should be used to expose the workloads.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **GATEWAY**
    
    </td>
    <td valign="top">
    
    The Gateway that the VirtualService should use to route traffic to the workload.
    
    </td>
    </tr>
    </table>
    
2.  Create a VirtualService to expose the workload:

    ```
    cat <<EOF | kubectl apply -f -
    apiVersion: networking.istio.io/v1alpha3
    kind: VirtualService
    metadata:
      name: ext-authz
      namespace: $NAMESPACE
    spec:
      hosts:
      - "$WORKLOAD_NAME.$DOMAIN_TO_EXPOSE_WORKLOADS"
      gateways:
      - $GATEWAY
      http:
      - match:
        - uri:
            prefix: /
        route:
        - destination:
            port:
              number: 80
            host: $WORKLOAD_NAME.$NAMESPACE.svc.cluster.local
    EOF
    ```

3.  Export the following configuration values as environment variables:

    ```
    export CLIENT_ID={YOUR_CLIENT_ID}
    export CLIENT_SECRET={YOUR_CLIENT_SECRET}
    export COOKIE_SECRET={YOUR_COOKIE_SECRET}
    export OIDC_ISSUER_URL={YOUR_OIDC_ISSUER_URL}
    ```


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
    
    **CLIENT\_ID**
    
    </td>
    <td valign="top">
    
    The unique identifier for the client application that is registered with the external authorizer.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **CLIENT\_SECRET**
    
    </td>
    <td valign="top">
    
    A secret key known only to the client and the external authorizer. It is used to authenticate the client when communicating with the external authorizer. To generate this value, you can use the command `openssl rand -base64 32 | head -c 32 | base64`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **CLIENT\_COOKIE**
    
    </td>
    <td valign="top">
    
    A secret key used to sign and encrypt the cookies that are used for session management and user authentication. To generate this value, you can use the command `openssl rand -base64 32 | head -c 32 | base64`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **OIDC\_ISSUER\_URL**
    
    </td>
    <td valign="top">
    
    This is the URL of the OpenID Connect \(OIDC\) issuer. Typically, you can find the issuer at `https://{YOUR_IDENTITY_PROVIDER_INSTANCE}/.well-known/openid-configuration`.
    
    </td>
    </tr>
    </table>
    
4.  Create a `values.yaml` file with the oauth2-proxy configuration for your authorization server:

    > ### Tip:  
    > You can adapt this configuration to better suit your needs. See the [additional configuration parameters](https://oauth2-proxy.github.io/oauth2-proxy/configuration/overview/#config-options).

    ```
    cat <<EOF > values.yaml
    config:
      clientID: $CLIENT_ID
      clientSecret: $CLIENT_SECRET
      cookieSecret: $COOKIE_SECRET
    extraArgs:
      provider: oidc
      cookie-secure: false
      cookie-domain: "$DOMAIN_TO_EXPOSE_WORKLOADS"
      cookie-samesite: lax
      set-xauthrequest: true
      whitelist-domain: "*.$DOMAIN_TO_EXPOSE_WORKLOADS:*"
      reverse-proxy: true
      pass-access-token: true
      set-authorization-header: true
      pass-authorization-header: true
      scope: "openid email"
      upstream: static://200
      skip-provider-button: true
      redirect-url: "https://oauth2-proxy.$DOMAIN_TO_EXPOSE_WORKLOADS/oauth2/callback"
      oidc-issuer-url: https://$OIDC_ISSUER_URL
      code-challenge-method: S256
    EOF
    ```

5.  To install oauth2-proxy with the defined configuration, use [oauth2-proxy helm chart](https://github.com/oauth2-proxy/manifests):

    ```
    helm repo add oauth2-proxy https://oauth2-proxy.github.io/manifests
    helm install custom oauth2-proxy/oauth2-proxy -f values.yaml
    ```

6.  Register oauth2-proxy as an authorization provider in the Istio module:

    ```
    cat <<EOF | kubectl apply -f -
    apiVersion: operator.kyma-project.io/v1alpha1
    kind: Istio
    metadata:
      name: default
      namespace: kyma-system
    spec:
      config:
        numTrustedProxies: 1
        authorizers:
        - name: "oauth2-proxy"
          service: "custom-oauth2-proxy.$NAMESPACE.svc.cluster.local"
          port: 80
          headers:
            inCheck:
              include: ["authorization", "cookie"]
              add:
                x-auth-request-redirect: "https://%REQ(:authority)%%REQ(x-envoy-original-path?:path)%"
            toUpstream:
              onAllow: ["authorization", "path", "x-auth-request-user", "x-auth-request-email", "x-auth-request-access-token"]
            toDownstream:
              onAllow: ["set-cookie"]
              onDeny: ["content-type", "set-cookie"]
    EOF
    ```

7.  Create an AuthorizationPolicy CR with the `CUSTOM` action and the `oauth2-proxy` provider:

    ```
    cat <<EOF | kubectl apply -f -
    apiVersion: security.istio.io/v1
    kind: AuthorizationPolicy
    metadata:
        name: ext-authz
        namespace: test
    spec:
      action: CUSTOM
      provider:
        name: oauth2-proxy
      rules:
      - to:
        - operation:
            paths:
            - /headers
      selector:
        matchLabels:
          app: httpbin
    EOF
    ```

8.  Create a `DestinationRule` resource with a traffic policy for the external authorization provider:

    ```
    cat <<EOF | kubectl apply -f -
    apiVersion: networking.istio.io/v1
    kind: DestinationRule
    metadata:
      name: external-authz-https
      namespace: istio-system
    spec:
      host: $OIDC_ISSUER_URL
      trafficPolicy:
        tls:
          mode: SIMPLE
    EOF
    ```




<a name="loiof2e9bf2be2714186b4231decd62a160b__result_nbl_wjc_wcc"/>

## Results

When you access the URL of the exposed service, you are redirected to the authorization provider's page.

