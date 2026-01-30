<!-- loioa829516c2d7f455f9d5a27bc470f7d5e -->

# Expose and Secure a Workload with OAuth2 Proxy External Authorizer \(Authorization Code Flow\)

Learn how to expose and secure a workload using the [OAuth2 Proxy](https://oauth2-proxy.github.io/oauth2-proxy/) external authorizer and the OAuth 2.0 Authorization Code flow. SAP Cloud Identity Services acts as the OAuth2/OIDC Identity Provider \(IdP\) that authenticates users.



<a name="loioa829516c2d7f455f9d5a27bc470f7d5e__prereq_adk_mv3_x2c"/>

## Prerequisites

-   You have the Istio and API Gateway modules in your cluster. See [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).
-   You have an SAP Cloud Identity Services tenant. See [Initial Setup](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/initial-setup?locale=en-US&version=Cloud&q=open+id+connect).
-   You have installed [Helm](https://helm.sh/docs/intro/install).



## Context

This procedure shows how to implement external authorization for your Kyma workloads using the OAuth 2.0 Authorization Code flow.

When the user visits a URL of your exposed workload, the following steps take place:

1.  OAuth2 Proxy redirects the user's browser to the SAP Cloud Identity Services authorization endpoint. This redirection includes several parameters, such as the OAuth2 Proxy's client ID and the callback URL \(`https://oauth2-proxy.{YOUR_DOMAIN}/oauth2/callback`\) where SAP Cloud Identity Services returns the user after granting or denying access.
2.  The user logs in to SAP Cloud Identity Services.
3.  After successsful authentication, SAP Cloud Identity Services redirects the browser back to the callback URL. This redirection includes an authorization code and any local state previously supplied by OAuth2 Proxy.
4.  OAuth2 Proxy requests an access token from the SAP Cloud Identity Services token endpoint using the authorization code received in the previous step. This request includes OAuth2 Proxy's client ID and client secret for authentication, as well as the callback URL.
5.  SAP Cloud Identity Services authenticates OAuth2 Proxy, validates the authorization code, and verifies that the callback URL matches the one you configured in the OpenID Connect application. If everything is valid, SAP Cloud Identity Services responds with an access token, an ID token, and optionally, a refresh token. OAuth2 Proxy then establishes a session and allows for forwarding the original request to your workload.

For more information on the Authorization Code flow, see [OAuth 2.0 RFC 6749](https://datatracker.ietf.org/doc/html/rfc6749#section-4.1) and [How Authorization Code Flow works](https://auth0.com/docs/get-started/authentication-and-authorization-flow/authorization-code-flow#how-authorization-code-flow-works).

Follow these steps:

1.  [Create and Configure OpenID Connect Application](expose-and-secure-a-workload-with-oauth2-proxy-external-authorizer-authorization-code-flo-a829516.md#loioa829516c2d7f455f9d5a27bc470f7d5e__task_onh_scn_nhc).
2.  [Deploy OAuth2 Proxy as an External Authorizer](expose-and-secure-a-workload-with-oauth2-proxy-external-authorizer-authorization-code-flo-a829516.md#loioa829516c2d7f455f9d5a27bc470f7d5e__task_uxf_4fn_nhc).
3.  [Expose Your Workload Using `extAuth` APIRule](expose-and-secure-a-workload-with-oauth2-proxy-external-authorizer-authorization-code-flo-a829516.md#loioa829516c2d7f455f9d5a27bc470f7d5e__task_uxf_4fn_nhc).

<a name="task_onh_scn_nhc"/>

<!-- task\_onh\_scn\_nhc -->

## Create and Configure OpenID Connect Application

In SAP Cloud Identity Services, create an OpenID Connect application and configure it for the Authorization Code flow.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services. See [Access Admin Console](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/accessing-administration-console?locale=en-US&version=Cloud).

2.  [Create OpenID Connect Application](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/create-openid-connect-application-299ae2f07a6646768cbc881c4d368dac?locale=en-US&version=Cloud).

3.  [Configure OpenID Connect Application for Authorization Code Flow](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/auth-code-configure-openid-connect-application-for-authorization-code-flow?locale=en-US&version=Cloud). When configuring the application, add the `https://oauth2-proxy.{YOUR_DOMAIN}/oauth2/callback` redirect URI and choose the *Authorization Code* grant type.

    The redirect URI is where the IdP sends the user back after a successful login. In this case, replace `{YOUR_DOMAIN}` with the name of the host on which you expose your service in Kyma.

4.  Configure a secret for API authentication. See [Configure Secrets for API Authentication](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/dev-configure-secrets-for-api-authentication?version=Cloud&locale=en-US).


<a name="task_uxf_4fn_nhc"/>

<!-- task\_uxf\_4fn\_nhc -->

## Deploy OAuth2 Proxy as an External Authorizer



## Procedure

1.  Export the domain name:

    ```
    EXPOSE_DOMAIN=$(kubectl get gateway -n kyma-system kyma-gateway -o jsonpath='{.spec.servers[0].hosts[0]}')
    EXPOSE_DOMAIN=${EXPOSE_DOMAIN#*.}
    GATEWAY=kyma-system/kyma-gateway
    ```

    This procedure uses the default domain of your Kyma cluster and the default Gateway. Alternatively, you can replace these values and use your custom domain and Gateway instead.

2.  Create a namespace for deploying the OAuth2 Proxy.

    ```
    kubectl create ns oauth2-proxy
    kubectl label namespace oauth2-proxy istio-injection=enabled --overwrite
    ```

3.  Add the [oauth2-proxy helm chart](https://github.com/oauth2-proxy/manifests) to your local Helm registry.

    ```
    helm repo add oauth2-proxy https://oauth2-proxy.github.io/manifests
    helm repo update oauth2-proxy
    ```

4.  Replace the placeholders and define the OAuth2 Proxy configuration for your authorization server.

    You can adjust this configuration as needed. See the [additional configuration parameters](https://oauth2-proxy.github.io/oauth2-proxy/configuration/overview/#config-options).

    ```
    helm upgrade --install oauth2-proxy --namespace oauth2-proxy oauth2-proxy/oauth2-proxy \
    --set config.clientID="${CLIENT_ID}" \
    --set config.clientSecret="${CLIENT_SECRET}" \
    --set config.cookieName="" \
    --set config.cookieSecret="$(openssl rand -base64 32 | head -c 32 | base64)" \
    --set extraArgs.provider=oidc \
    --set extraArgs.auth-logging="true" \
    --set extraArgs.cookie-domain="${EXPOSE_DOMAIN}" \
    --set extraArgs.cookie-samesite="lax" \
    --set extraArgs.cookie-secure="false" \
    --set extraArgs.force-json-errors="true" \
    --set extraArgs.login-url="static://401" \
    --set extraArgs.oidc-issuer-url="${TENANT_URL}" \
    --set extraArgs.pass-access-token="true" \
    --set extraArgs.pass-authorization-header="true" \
    --set extraArgs.pass-host-header="true" \
    --set extraArgs.pass-user-headers="true" \
    --set extraArgs.request-logging="true" \
    --set extraArgs.reverse-proxy="true" \
    --set extraArgs.scope="openid email" \
    --set extraArgs.set-authorization-header="true" \
    --set extraArgs.set-xauthrequest="true" \
    --set extraArgs.skip-jwt-bearer-tokens="true" \
    --set extraArgs.skip-oidc-discovery="false" \
    --set extraArgs.skip-provider-button="true" \
    --set extraArgs.standard-logging="true" \
    --set extraArgs.upstream="static://200" \
    --set extraArgs.whitelist-domain="*.${EXPOSE_DOMAIN}:*" \
    --wait
    ```

    Check if the Oauth2 Proxy Pods are running:

    ```
    kubectl --namespace=oauth2-proxy get pods -l "app=oauth2-proxy"
    ```

5.  Register OAuth2 Proxy as an authorization provider in the Istio module:

    ```
    kubectl patch istio -n kyma-system default --type merge --patch '{"spec":{"config":{"authorizers":[{"name":"oauth2-proxy","port":80,"service":"oauth2-proxy.oauth2-proxy.svc.cluster.local","headers":{"inCheck":{"include":["x-forwarded-for", "cookie", "authorization"]}}}]}}}'
    ```

    For more information about the fields set above, see the [Istio Custom Resource documentation](https://kyma-project.io/external-content/istio/docs/user/04-00-istio-custom-resource.html).


<a name="task_ikf_23n_nhc"/>

<!-- task\_ikf\_23n\_nhc -->

## Expose Your Workload Using `extAuth` APIRule

To configure OAuth2 Proxy, expose your workload using the APIRule custom resource \(CR\). Configure `extAuth` as the access strategy and add the `oauth2-proxy` authorizer.



## Procedure

You can either use Kyma dashboard or kubectl.

-   Use Kyma dashboard.

    1.  Go to *Discovery and Network → API Rules* and choose *Create*.

    2.  Provide all the required configuration details.

    3.  Add a rule with the following configuration.

        -   **Access Strategy**: `extAuth`
        -   In **External Authorization**, add the `oauth2-proxy` authorizer.
        -   Add allowed methods and the request path.

    4.  Choose *Create*.


-   Use kubectl.

    To expose and secure your Service, create the APIRule CR. In the rules section, define the **extAuth** field and add the `oauth2-proxy` authorizer.

    ```
    ...
      rules:
        - path: /*
          methods: ["GET"]
          extAuth:
            authorizers:
              - oauth2-proxy
    ...
    
    ```




## Results

To access your workload, copy the host link defined in your APIRule and open it in a browser. You're redirected to Cloud Identity Services first, where you need to log in. If the login is successful, you can access your application.



### Example

See the following example APIRule with **extAuth** authorizer that exposes the sample HTTPBin Deployment:

> ### Example:  
> 1.  Create the `httpbin-system` namespace and deploy a sample HTTPBin Deployment.
> 
>     ```
>     kubectl create ns httpbin-system
>     kubectl label namespace httpbin-system istio-injection=enabled
>     kubectl apply -f \
>     https://raw.githubusercontent.com/istio/istio/master/samples/httpbin/httpbin.yaml \
>     -n httpbin-system
>     
>     ```
> 
> 2.  Expose the workload with an APIRule using the extAuth access strategy.
> 
>     ```
>     cat <<EOF | kubectl apply -f -
>     apiVersion: gateway.kyma-project.io/v2
>     kind: APIRule
>     metadata:
>       name: httpbin
>       namespace: httpbin-system
>     spec:
>       gateway: ${GATEWAY}
>       hosts:
>         - httpbin.${EXPOSE_DOMAIN}
>       service:
>         name: httpbin
>         port: 8000
>       rules:
>         - path: /*
>           methods: ["GET"]
>           extAuth:
>             authorizers:
>               - oauth2-proxy
>     EOF
>     ```
> 
>     Check if the APIRule's status is ready:
> 
>     ```
>     kubectl --namespace=oauth2-proxy get apirules httpbin -n httpbin-system
>     ```
> 
> 3.  When you open `httpbin.${EXPOSE_DOMAIN}`, the page displays HTTPBin endpoints.

