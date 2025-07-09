<!-- loio44bb2d3596554bf4b94ea344e40937dd -->

# Exposing and Securing Workloads with a JWT

Learn how to expose a workload and secure it with a JSON Web Token \(JWT\). To get the token, create a client credentials application using SAP Cloud Identity Services - Identity Authentication.



<a name="loio44bb2d3596554bf4b94ea344e40937dd__prereq_g4r_ybm_rsb"/>

## Prerequisites

-   You have the Istio and API Gateway modules added. See [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).
-   You have access to Kyma dashboard. Alternatively, to use CLI instructions, you must install [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl) and configure it to communicate with your Kyma runtime instance. See [Access a Kyma Instance Using kubectl](access-a-kyma-instance-using-kubectl-3e25944.md).
-   You have installed [curl](https://curl.se/).
-   You have a deployed workload.

    > ### Note:  
    > To expose a workload using APIRule in version `v2`, the workload must be a part of the Istio service mesh. See [Enabling Istio Sidecar Proxy Injection](enabling-istio-sidecar-proxy-injection-b3c6f1d.md).

-   You have an SAP Cloud Identity Services - Identity Authentication tenant and you have created an OpenID Connect Application in it. See [Create OpenID Connect Application](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/230a13631d944b14bfb3b4f7310c1978.html?locale=en-US&state=PRODUCTION&version=Cloud) and [Configure OpenID Connect Application for JWT Bearer Flow](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/dd8cd7ac2c6d49a29d21505fd9aca773.html?locale=en-US&state=PRODUCTION&version=Cloud).

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




<a name="loio44bb2d3596554bf4b94ea344e40937dd__context_umr_nyg_y2c"/>

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



