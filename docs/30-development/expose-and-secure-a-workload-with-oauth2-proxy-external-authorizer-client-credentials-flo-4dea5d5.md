<!-- loio4dea5d550b3d4b85b879d4def33f0a9c -->

# Expose and Secure a Workload with OAuth2 Proxy External Authorizer \(Client Credentials Flow\)

Learn how to expose and secure a workload using the [OAuth2 Proxy](https://oauth2-proxy.github.io/oauth2-proxy/) external authorizer and the OAuth 2.0 Client Credentials flow. SAP Cloud Identity Services acts as the OAuth2/OIDC Identity Provider \(IdP\) that issues JSON Web Tokens \(JWTs\).



<a name="loio4dea5d550b3d4b85b879d4def33f0a9c__prereq_adk_mv3_x2c"/>

## Prerequisites

-   You have an SAP BTP, Kyma runtime instance with the Istio and API Gateway modules added. These modules are added to your Kyma cluster by default.

    To check the list of added modules, choose *Modify Modules* in Kyma dashboard's *Cluster Details* section.

-   You have an SAP Cloud Identity Services tenant. See [Initial Setup](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/initial-setup?locale=en-US&version=Cloud&q=open+id+connect).
-   You have installed [Helm](https://helm.sh/docs/intro/install).



## Context

This procedure shows how to implement external authorization for your Kyma workloads using the OAuth2 Client Credentials flow. In this context, your application exchanges its credentials directly with SAP Cloud Identity Services to obtain an access token.

When the URL of your exposed workload is requested, the following steps take place:

1.  The client sends its client ID and client secret to SAP Cloud Identity Services.
2.  SAP Cloud Identity Services validates these credentials and responds with a JWT that contains specific scopes defining what resources the client can access.
3.  The client includes this JWT in the Authorization header when making requests to your secured Kyma workload.
4.  OAuth2 Proxy validates the JWT against SAP Cloud Identity Services and either allows the request to proceed to your workload or returns `401 Unauthorized` in response.

Unlike the Authorization Code flow that requires browser redirects and user consent, the Client Credentials flow enables direct server-to-server communication using only the application's own credentials. For more information, see [OAuth 2.0 RFC 6749](https://datatracker.ietf.org/doc/html/rfc6749#section-1.3.4) and [Client Credentials Flow](https://auth0.com/docs/get-started/authentication-and-authorization-flow/client-credentials-flow#how-it-works).

Follow these steps:

1.  [Create and Configure OpenID Connect Application](expose-and-secure-a-workload-with-oauth2-proxy-external-authorizer-client-credentials-flo-4dea5d5.md#loio4dea5d550b3d4b85b879d4def33f0a9c__task_onh_scn_nhc).
2.  [Get a JWT](expose-and-secure-a-workload-with-oauth2-proxy-external-authorizer-client-credentials-flo-4dea5d5.md#loio4dea5d550b3d4b85b879d4def33f0a9c__task_cq2_nfn_nhc).
3.  [Deploy OAuth2 Proxy as an External Authorizer](expose-and-secure-a-workload-with-oauth2-proxy-external-authorizer-client-credentials-flo-4dea5d5.md#loio4dea5d550b3d4b85b879d4def33f0a9c__task_uxf_4fn_nhc).
4.  [Expose Your Workload Using `extAuth` APIRule](expose-and-secure-a-workload-with-oauth2-proxy-external-authorizer-client-credentials-flo-4dea5d5.md#loio4dea5d550b3d4b85b879d4def33f0a9c__task_ikf_23n_nhc).

<a name="task_onh_scn_nhc"/>

<!-- task\_onh\_scn\_nhc -->

## Create and Configure OpenID Connect Application

You need an identity provider to issue JWTs. Creating an OpenID Connect application allows SAP Cloud Identity Services to act as your issuer and manage authentication for your workloads.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services. See [Access Admin Console](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/accessing-administration-console?locale=en-US&version=Cloud).

2.  [Create OpenID Connect Application](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/create-openid-connect-application-299ae2f07a6646768cbc881c4d368dac?locale=en-US&version=Cloud).

3.  [Configure OpenID Connect Application for Client Credentials Flow](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/client-cred-configure-openid-connect-application-for-client-credentials-flow?locale=en-US&version=Cloud).

4.  [Configure Secrets for API Authentication](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/dev-configure-secrets-for-api-authentication?version=Cloud&locale=en-US).


<a name="task_cq2_nfn_nhc"/>

<!-- task\_cq2\_nfn\_nhc -->

## Get a JWT



## Procedure

1.  Export the following values as environment variables:

    ```
    CLOUD_IDENTITY_SERVICES_INSTANCE="my-example-tenant.accounts.ondemand.com"
    CLIENT_ID="{YOUR-CLIENT-ID}"
    CLIENT_SECRET="{YOUR-CLIENT-SECRET}"
    ```

2.  Export base 64 encoded client ID and client secret.

    ```
    export ENCODED_CREDENTIALS=$(echo -n "$CLIENT_ID:$CLIENT_SECRET" | base64)
    ```

3.  Get `token_endpoint`, `jwks_uri`, and `issuer` from your OpenID application, and save these values as environment variables:

    ```
    TOKEN_ENDPOINT=$(curl -s https://$CLOUD_IDENTITY_SERVICES_INSTANCE/.well-known/openid-configuration | jq -r '.token_endpoint')
    echo token_endpoint: $TOKEN_ENDPOINT
    JWKS_URI=$(curl -s https://$CLOUD_IDENTITY_SERVICES_INSTANCE/.well-known/openid-configuration | jq -r '.jwks_uri')
    echo jwks_uri: $JWKS_URI
    ISSUER=$(curl -s https://$CLOUD_IDENTITY_SERVICES_INSTANCE/.well-known/openid-configuration | jq -r '.issuer')
    echo issuer: $ISSUER
    ```

4.  Get the JWT access token:

    ```
    ACCESS_TOKEN=$(curl -s -X POST "$TOKEN_ENDPOINT" \
        -d "grant_type=client_credentials" \
        -d "client_id=$CLIENT_ID" \
        -H "Content-Type: application/x-www-form-urlencoded" \
        -H "Authorization: Basic $ENCODED_CREDENTIALS" |  jq -r '.access_token')
    echo $ACCESS_TOKEN
    ```


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

To configure OAuth2 Proxy, expose your workload using APIRule custom resource \(CR\). Configure `extAuth` as the access strategy and add the `oauth2-proxy` authorizer.



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
> 3.  To test the connection, first, do not provide the JWT.
> 
>     ```
>     curl -ik -X GET https://httpbin.${EXPOSE_DOMAIN}/headers
>     ```
> 
>     You get the error `401 Unauthorized`.
> 
> 4.  Now, access the secured workload using the correct JWT.
> 
>     ```
>     curl -ik -X GET https://httpbin.${EXPOSE_DOMAIN}/headers --header "Authorization:Bearer ${ACCESS_TOKEN}"
>     ```
> 
>     You get code `200 OK` in response.

