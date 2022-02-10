<!-- loioaa803382970c41d2970c7bf265475dfb -->

# Enable mTLS Authentication to SAP Authorization and Trust Management Service for Your Application

Enabling your application to retrieve access tokens from SAP Authorization and Trust Management service\(XSUAA\) over mutual transport layer security \(mTLS\) requires you to enable mTLS token retrieval for the service instance. Then ensure the binding includes the X.509 credentials.



<a name="loioaa803382970c41d2970c7bf265475dfb__prereq_yjw_1pz_2sb"/>

## Prerequisites

To handle tokens, use:

-   Application router version 10.7.1 or later

    For more information, see [https://www.npmjs.com/package/@sap/approuter](https://www.npmjs.com/package/@sap/approuter).

-   Our security libraries

    -   For Java or Spring, see [XSUAA Token Client and Token Flow API](https://github.com/SAP/cloud-security-xsuaa-integration/tree/main/token-client) on *Github*.

    -   For Python, see [SAP Python Security Library](https://pypi.org/project/sap-xssec/) on *Python Package Index*.

    -   For Node.js, see [@sap/sbf](https://www.npmjs.com/package/@sap/sbf) on *Newtons Poleless Magnet \(NPM\)*.


-   Your own integration

    For more information, see [Implementing Custom Token Retrieval from SAP Authorization and Trust Management Service with mTLS](implementing-custom-token-retrieval-from-sap-authorization-and-trust-management-service-w-63fd9f1.md).


> ### Recommendation:  
> Build automation into your deployment or CI/CD pipeline. Client certificates have a relatively short lifetime. The default lifetime for certificates managed by the service is 7 days. Only by automating the process, can you ensure that credentials are rotated and distributed in a timely manner. Otherwise, you risk authentication failures from expired certificates.



## Context

Use the same procedure as outlined in [Add Authentication and Functional Authorization Checks to Your Application](add-authentication-and-functional-authorization-checks-to-your-application-0a69484.md). Modify this procedure with the following steps.

Be mindful of whether you're updating an existing application or starting with a brand new development.

-   If you're adding mTLS to an existing application, add mTLS support to the credential types of the service instance. Then update all your bindings and service keys before removing the support for other credential types.

    > ### Tip:  
    > For an example of how to migrate from one secret type to another, see [Migrate from Instance Secrets to Binding Secrets](../50-administration-and-ops/migrate-from-instance-secrets-to-binding-secrets-dcee867.md).

-   If you're starting from scratch, you can build in mTLS support from the beginning, without worrying about disrupting existing bindings or service keys.




## Procedure

1.  Enable mTLS for the service instance.

    Add the credential type `x509` to the OAuth configuration of the service instance.

    -   The following is an example of the OAuth configuration from an application security descriptor \(`xs-security.json`\).

        ```
          "oauth2-configuration": {
            "credential-types": ["binding-secret","x509"]
          }
        
        ```

        In this example, binding secrets are the default credential type, but X.509 secrets are supported.

    -   The following is an example of the service as a resource in a multitarget application \(MTA\) descriptor \(`mta.yaml`\).

        ```
        resources:
          - name: myXSUAA
            type: com.sap.xs.uaa
            parameters:
              service-plan: application
              config:
                xsappname: mAapp
                oauth2-configuration:
                  credential-types:
                    - x509
                    - binding-secret
        ```

        In this example, X.509 secrets are the default credential type. When deployed, any preconfigured bindings get service-managed client certificates. After deployment, you can create additional bindings with binding secrets.


2.  Deploy the application or update the service instance.

3.  Create bindings or service keys with the X.509 credentials.

    You create the binding from the Cloud Foundry command-line interface \(cf CLI\),

    -   From the command-line interface, provide a `parameters.json` to configure the certificates managed by the service or to provide your own X.509 certificate.

        The following is an example of a `parameters.json` with the certificates managed by the service.

        ```
        {
          "credential-type": "x509",
          "x509": {
            "key-length": 2048,
            "validity": 8,
            "validity-type": "DAYS"
          }
        }
        ```

        The following is an example of a `parameters.json` with certificates you provide.

        ```
        {
          "credential-type": "x509",
          "x509": {
            "certificate": "-----BEGIN CERTIFICATE-----...-----END CERTIFICATE-----",
            "certificate-pinning": true
          }
        }
        ```

        Reference the `parameters.json` when you bind the service. For example:

        ```
        cf bind-service myApp myXSUAA -c parameters.json
        ```



**Related Information**  


[Parameters for X.509 Certificates Managed by SAP Authorization and Trust Management Service](../50-administration-and-ops/parameters-for-x-509-certificates-managed-by-sap-authorization-and-trust-management-servi-436ed68.md "Use the parameters to have the service generate X.509 certificates for you.")

[Parameters for Self-Managed X.509 Certificates](../50-administration-and-ops/parameters-for-self-managed-x-509-certificates-5168df6.md "Use these parameters to provide your own certificates for a binding or service key to service instances of the SAP Authorization and Trust Management service (XSUAA).")

[Rotate X.509 Secrets](../50-administration-and-ops/rotate-x-509-secrets-e5e7736.md "When your private key is exposed or your certificates are about to expire, it's time to rotate secrets. Rotating secrets can be as easy as unbinding and rebinding your application or service key.")

