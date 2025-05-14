<!-- copy4464329723cb4de3a396677661f27f18 -->

# Exposing and Securing Workloads with a JWT

Learn how to expose a workload and secure it with a JSON Web Token \(JWT\). To get the token, create a client credentials application using SAP Cloud Identity Services - Identity Authentication.



<a name="copy4464329723cb4de3a396677661f27f18__prereq_g4r_ybm_rsb"/>

## Prerequisites

-   You have the Istio and API Gateway modules added. See [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).
-   You have access to Kyma dashboard. Alternatively, to use CLI instructions, you must install [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl) and configure it to communicate with your Kyma runtime instance. See [Access a Kyma Instance Using kubectl](access-a-kyma-instance-using-kubectl-3e25944.md).
-   You have installed [curl](https://curl.se/).
-   You have a deployed workload.

-   You have an SAP Cloud Identity Services - Identity Authentication tenant and you have created an OpenID Connect Application in your Identity Authentication tenant. See [Create OpenID Connect Application for JWT Bearer Flow](https://help.sap.com/docs/identity-authentication/identity-authentication/configure-apps-create-openid-connect-application-for-jwt-bearer-flow?version=Cloud).

-   You have configured a Secret for API Authentication and saved the values of Client ID and Client Secret. See [Configure Secrets for API Authentication](https://help.sap.com/docs/identity-authentication/identity-authentication/dev-configure-secrets-for-api-authentication?version=Cloud).
-   You have [set up your custom domain](https://kyma-project.io/#/api-gateway/user/tutorials/01-10-setup-custom-domain-for-workload). Alternatively, you can use the default domain of your Kyma cluster and the default Gateway `kyma-system/kyma-gateway`.

    > ### Note:  
    > Because the default Kyma domain is a wildcard domain, which uses a simple TLS Gateway, it is recommended that you set up your custom domain for use in a production environment.

    > ### Tip:  
    > To learn what the default domain of your Kyma cluster is, run the following command:
    > 
    > ```
    > kubectl get gateway -n kyma-system kyma-gateway -o jsonpath='{.spec.servers[0].hosts}'
    > ```




<a name="copy4464329723cb4de3a396677661f27f18__context_umr_nyg_y2c"/>

## Context

To interact with a workload that is secured using an API Rule of the JWT type, you need an access token. Follow these steps to obtain a JWT using an Identity Authentication tenant. Then, use either kubectl or Kyma dashboard to expose and secure your workload.



## Procedure

To obtain a JWT token, you must use curl. To create an APIRule custom resource \(CR\), you can use either Kyma dashboard or kubectl.

-   Use Kyma dashboard.

    1.  Export the name of your Identity Authentication instance and your client credentials as environment variables:

        ```
        export IDENTITY_AUTHENTICATION_INSTANCE={YOUR_IDENTITY_AUTHENTICATION_INSTANCE_NAME}
        export CLIENT_ID={YOUR_CLIENT_ID}
        export CLIENT_SECRET={YOUR_CLIENT_SECRET}
        ```

    2.  Encode your client credentials and export them as an environment variable:

        ```
        export ENCODED_CREDENTIALS=$(echo -n "$CLIENT_ID:$CLIENT_SECRET" | base64)
        ```

    3.  Get values of the `token_endpoint`, `jwks_uri`, and `issuer` parameters:

        ```
        curl -s https://$IDENTITY_AUTHENTICATION_INSTANCE.accounts400.ondemand.com/.well-known/openid-configuration
        ```

        > ### Note:  
        > You need the values of the `jwks_uri` and `issuer` parameters to secure your workload using an APIRule of the JWT type.

    4.  Export the value of the `token_endpoint` parameter as an environment variable:

        ```
        export TOKEN_ENDPOINT={YOUR_TOKEN_ENDPOINT}
        ```

    5.  Get the JWT:

        ```
        curl -X POST "$TOKEN_ENDPOINT" -d "grant_type=client_credentials" -d "client_id=$CLIENT_ID" -H "Content-Type: application/x-www-form-urlencoded" -H "Authorization: Basic $ENCODED_CREDENTIALS"
        ```

    6.  Go to the namespace in which you want to create an `APIRule` custom resource.

        The namespace must have Istio sidecar proxy injection enabled. See [Enabling Istio Sidecar Proxy Injection](enabling-istio-sidecar-proxy-injection-b3c6f1d.md).

    7.  Go to *Discovery and Network**→ API Rules* and select *Create*.

    8.  Provide all the required configuration details, such as APIRule CR's name, the name and port of the Service you want to expose, the Gateway's name, and the host in the format `{SUBDOMAIN}.{YOUR_DOMAIN}`.

    9.  Add a rule with the following configuration:


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
        
        `Access Strategy`
        
        </td>
        <td valign="top">
        
        *jwt*

        In the `JWT` section, add an authentication with your issuer and JSON Web Key Set URIs.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `Methods`
        
        </td>
        <td valign="top">
        
        *GET*
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `path`
        
        </td>
        <td valign="top">
        
        */\**
        
        </td>
        </tr>
        </table>
        
    10. Select *Create*.

    11. To call the endpoint, send a `GET` request to the Service:

        ```
        curl -ik -X GET https://{SUBDOMAIN}.{DOMAIN_NAME}/headers
        ```

        You get the error `401 Unauthorized`.

    12. Now, access the secured workload using the correct JWT.

        ```
        curl -ik -X GET https://{SUBDOMAIN}.{DOMAIN_NAME}/headers --header "Authorization:Bearer $ACCESS_TOKEN"
        ```

        If successful, you get the code `200 OK` in response.


-   Use kubectl.

    1.  Export the name of your Identity Authentication instance and your client credentials as environment variables:

        ```
        export IDENTITY_AUTHENTICATION_INSTANCE={YOUR_IDENTITY_AUTHENTICATION_INSTANCE_NAME}
        export CLIENT_ID={YOUR_CLIENT_ID}
        export CLIENT_SECRET={YOUR_CLIENT_SECRET}
        ```

    2.  Encode your client credentials and export them as an environment variable:

        ```
        export ENCODED_CREDENTIALS=$(echo -n "$CLIENT_ID:$CLIENT_SECRET" | base64)
        ```

    3.  Get values of the `token_endpoint`, `jwks_uri`, and `issuer` parameters:

        ```
        curl -s https://$IDENTITY_AUTHENTICATION_INSTANCE.accounts400.ondemand.com/.well-known/openid-configuration
        ```

        > ### Note:  
        > You need the values of the `jwks_uri` and `issuer` parameters to secure your workload using an APIRule of the JWT type.

    4.  Export the value of the `token_endpoint` parameter as an environment variable:

        ```
        export TOKEN_ENDPOINT={YOUR_TOKEN_ENDPOINT}
        ```

    5.  Get the JWT:

        ```
        curl -X POST "$TOKEN_ENDPOINT" -d "grant_type=client_credentials" -d "client_id=$CLIENT_ID" -H "Content-Type: application/x-www-form-urlencoded" -H "Authorization: Basic $ENCODED_CREDENTIALS"
        ```

    6.  Export the JWT as an environment variable:

        ```
        export ACCESS_TOKEN={YOUR_ACCESS_TOKEN}
        ```

    7.  To expose and secure your Service, replace all placeholders and create the following APIRule:

        ```
        cat <<EOF | kubectl apply -f -
        apiVersion: gateway.kyma-project.io/v2
        kind: APIRule
        metadata:
          name: {APIRULE_NAME}
          namespace: {APIRULE_NAMESPACE}
        spec:
          hosts:
            - {SUBDOMAIN}.{DOMAIN_NAME}
          service:
            name: {SERVICE_NAME}
            port: {SERVICE_PORT}
          gateway: {GATEWAY_NAME}/{GATEWAY_NAMESPACE}
          rules:
            - jwt:
                authentications:
                  -  issuer: {ISSUER}
                      jwksUri: {JWKS_URI}
              methods:
                - GET
              path: /*
        EOF
        ```

    8.  To call the endpoint, send a `GET` request to the Service

        ```
        curl -ik -X GET https://{SUBDOMAIN}.{DOMAIN_NAME}/headers
        ```

        You get the error `401 Unauthorized`.

    9.  Now, access the secured workload using the correct JWT.

        ```
        curl -ik -X GET https://{SUBDOMAIN}.{DOMAIN_NAME}/headers --header "Authorization:Bearer $ACCESS_TOKEN"
        ```

        If successful, you get the code `200 OK` in response.



<a name="loio70aee8a8e9c34c22a2ac0fc02b74789a"/>

<!-- loio70aee8a8e9c34c22a2ac0fc02b74789a -->

## Get a JSON Web Token

Follow the instructions to obtain a JWT.



## Procedure

1.  Export the name of your Identity Authentication instance and your client credentials as environment variables. Run:

    ```
    export IDENTITY_AUTHENTICATION_INSTANCE={YOUR_IDENTITY_AUTHENTICATION_INSTANCE_NAME}
    export CLIENT_ID={YOUR_CLIENT_ID}
    export CLIENT_SECRET={YOUR_CLIENT_SECRET}
    ```

2.  Encode your client credentials and export them as an environment variable:

    ```
    export ENCODED_CREDENTIALS=$(echo -n "$CLIENT_ID:$CLIENT_SECRET" | base64)
    ```

3.  Get values of the `token_endpoint` and `jwks_uri` parameters:

    ```
    curl -s https://$IDENTITY_AUTHENTICATION_INSTANCE.accounts400.ondemand.com/.well-known/openid-configuration
    ```

    > ### Note:  
    > You need the value of the `jwks_uri` parameter to secure your workload using an APIRule of the JWT type.

4.  Export the value of the `token_endpoint` as an environment variable:

    ```
    export TOKEN_ENDPOINT={YOUR_TOKEN_ENDPOINT}
    ```

5.  Get the JWT:

    ```
    curl -X POST "$TOKEN_ENDPOINT" -d "grant_type=client_credentials" -d "client_id=$CLIENT_ID" -H "Content-Type: application/x-www-form-urlencoded" -H "Authorization: Basic $ENCODED_CREDENTIALS"
    ```

6.  Export the JWT as an environment variable:

    ```
    export ACCESS_TOKEN={YOUR_ACCESS_TOKEN}
    ```




<a name="loio70aee8a8e9c34c22a2ac0fc02b74789a__result_lqv_ggn_rsb"/>

## Results

You got a JWT that you can use to interact with a workload.

<a name="loioc83ae5d38fee48f7a0aebd8833f4631d"/>

<!-- loioc83ae5d38fee48f7a0aebd8833f4631d -->

## Expose and Secure a Workload with a JWT

Use Kyma dashboard or kubectl to expose a workload and secure it with a JWT.



<a name="loioc83ae5d38fee48f7a0aebd8833f4631d__steps-unordered_bdn_n5f_xdc"/>

## Procedure

-   Use Kyma dashboard.

    1.  Create a namespace.

    2.  Go to *Discovery and Network**→ API Rules* and select *Create*.

    3.  Choose the name for the APIRule CR.

    4.  Add the name and port of the service you want to expose.

    5.  Add the Gateway.

    6.  Add a host in format \{SUBDOMAIN\}.\{YOUR\_DOMAIN\}.

    7.  Add a rule with the following configuration:

        -   `Path`: */.\**
        -   `Access Strategy Handler`: *jwt*
        -   `Methods`: *GET*

    8.  To access the secured service, call it using the JWT.

        ```
        curl -ik https://{SUBDOMAIN}.{YOUR_DOMAIN}/headers -H "Authorization: Bearer $ACCESS_TOKEN"
        ```

        This call returns the `200 OK` response code.


-   Use kubectl.

    1.  To expose and secure your workload, create the APIRule in your namespace.

        Replace all placeholders and run the following command. In the `jwks_uri` section, add your JSON Web Key Set URIs.

        ```
        cat <<EOF | kubectl apply -f -
        apiVersion: gateway.kyma-project.io/v1beta1
        kind: APIRule
        metadata:
          name: {APIRULE_NAME}
          namespace: {APIRULE_NAMESPACE}
        spec:
          host: {SUBDOMAIN}.{YOUR_DOMAIN}   
          service:
            name: {SERVICE_NAME}
            port: {SERVICE_PORT}
          gateway: {GATEWAY_NAME}/{GATEWAY_NAMESPACE}
          rules:
            - accessStrategies:
              - handler: jwt
                config:
                  jwks_urls:
                  - {JWKS_URI}
              methods:
                - GET
              path: /.*
        EOF
        ```

    2.  To access the secured service, call it using the JWT.

        ```
        curl -ik https://{SUBDOMAIN}.{YOUR_DOMAIN}/headers -H "Authorization: Bearer $ACCESS_TOKEN"
        ```

        This call returns the `200 OK` response code.





<a name="loioc83ae5d38fee48f7a0aebd8833f4631d__result_rcr_yvq_1bc"/>

## Results

You have secured your service using an APIRule with the JWT access strategy. You can use the JWT to interact with the service.

<a name="loio83359eaade534602ae219211c56c9207"/>

<!-- loio83359eaade534602ae219211c56c9207 -->

## Expose and Secure a Workload with a JWT Using kubectl

Use kubectl to expose a workload and secure it with a JWT.



## Procedure

1.  Create a namespace and export its value as an environment variable:

    ```
    export NAMESPACE={NAMESPACE_NAME}
    kubectl create ns $NAMESPACE
    ```

2.  Export the following values as environment variables:

    ```
    export DOMAIN_TO_EXPOSE_WORKLOADS={DOMAIN_NAME}
    export JWKS_URI={YOUR_JWKS_URI}
    ```

3.  To expose and secure your workload, create the APIRule in your namespace:

    ```
    cat <<EOF | kubectl apply -f -
    apiVersion: gateway.kyma-project.io/v1beta1
    kind: APIRule
    metadata:
      name: httpbin
      namespace: $NAMESPACE
    spec:
      service:
        name: httpbin
        port: 8000
        host: httpbin.$DOMAIN_TO_EXPOSE_WORKLOADS
      gateway: kyma-system/kyma-gateway
      rules:
        - accessStrategies:
          - handler: jwt
            config:
              jwks_urls:
              - $JWKS_URI
          methods:
            - GET
          path: /.* 
    EOF
    ```

4.  To access the secured service, call it using the JWT:

    ```
    curl -ik https://httpbin.$DOMAIN_TO_EXPOSE_WORKLOADS/headers -H "Authorization: Bearer $ACCESS_TOKEN"
    ```

    This call returns the `200 OK` response code.




<a name="loio83359eaade534602ae219211c56c9207__result_rcr_yvq_1bc"/>

## Results

You have secured your service using an APIRule with the JWT access strategy. You can use the JWT to interact with the service.

