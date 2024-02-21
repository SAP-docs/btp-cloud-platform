<!-- loio44bb2d3596554bf4b94ea344e40937dd -->

# Expose and Secure a Workload with a JSON Web Token

Learn how to expose a workload and secure it with a JSON Web Token \(JWT\). To get the token, create a client credentials application using SAP Cloud Identity Services - Identity Authentication.



<a name="loio44bb2d3596554bf4b94ea344e40937dd__prereq_g4r_ybm_rsb"/>

## Prerequisites

-   You have an SAP Cloud Identity Services - Identity Authentication tenant.

-   You have the default Istio and API Gateway modules in your cluster.

-   You have a workload deployed.




## Context

In order to interact with a workload secured with an API Rule of the JWT type, you need an access token. Follow these steps to get a JWT using an Identity Authentication tenant. Then expose and secure a workload with an API Rule of the JWT type.



## Procedure

1.  In your Identity Authentication instance, create and configure an Application to generate client credentials:

    1.  Go to *Applications & Resources* \> *Applications* and select *Create*.

    2.  In *Create Application*, type the *Display Name* and select *Save*.

    3.  In *Trust* \> *Single Sign-On*, set the *Protocol* to *OpenID Connect* and select *Save*.

    4.  In *Trust* \> *Application APIs*, go to *Client ID, Secrets and Certificates* and select *Add* to add a Secret. Click *Save* to confirm the Secret creation.

    5.  Save the client credentials, such as Client ID and Client Secret.


2.  Get a JWT:

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

    3.  Get values of the **token\_endpoint** and **jwks\_uri** parameters:

        ```
        curl -s https://$IDENTITY_AUTHENTICATION_INSTANCE.accounts400.ondemand.com/.well-known/openid-configuration
        ```

        > ### Note:  
        > You need the value of the **jwks\_uri** parameter to secure your workload using an API Rule of the JWT type.

    4.  Export the value of the **token\_endpoint** as an environment variable:

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


3.  Expose and secure a workload with an API Rule of the JWT type:

    1.  Create a Namespace and export its value as an environment variable:

        ```
        export NAMESPACE={NAMESPACE_NAME}
        kubectl create ns $NAMESPACE
        ```

    2.  Export the following values as environment variables:

        ```
        export DOMAIN_TO_EXPOSE_WORKLOADS={DOMAIN_NAME} #This is a Kyma domain or your custom subdomain e.g. api.mydomain.com.
        export JWKS_URI={YOUR_JWKS_URI}
        ```

    3.  Expose your workload and secure it by creating an API Rule custom resource in your Namespace:

        ```
        cat <<EOF | kubectl apply -f -
        apiVersion: gateway.kyma-project.io/v1alpha1
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

        This call returns the code `200` response.





<a name="loio44bb2d3596554bf4b94ea344e40937dd__result_lqv_ggn_rsb"/>

## Results

You got a JWT that you can use to interact with a workload secured with an API Rule of the JWT type. You also secured your service with an API Rule of the JWT type.

