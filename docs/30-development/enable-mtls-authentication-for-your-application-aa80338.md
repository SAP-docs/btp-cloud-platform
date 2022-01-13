<!-- loioaa803382970c41d2970c7bf265475dfb -->

# Enable mTLS Authentication for Your Application

Enabling mutual transport layer security \(mTLS\) for your application requires you to enable mTLS authentication for the SAP Authorization and Trust Management service. Then ensure the binding includes the X.509 credentials.



## Context

Use the same procedure as outlined in [Add Authentication and Functional Authorization Checks to Your Application](add-authentication-and-functional-authorization-checks-to-your-application-0a69484.md). Modify this procedure with the following steps.



## Procedure

1.  Enable mTLS in the application security descriptor \(`xs-security.json`\).

    Add the credential type x509 to the Oauth configuration.

    ```
      "oauth2-configuration": {
        "credential-types": [
          "x509"
        ]
      }
    
    ```

2.  Either redeploy or update the service instance.

3.  Ensure the creation of bindings with the X.509 credentials.

    You create the binding from the Cloud Foundry command-line interface or in a `manifest.yml` when you deploy the application.

    -   From the command-line interface, provide a parameters.json to configure the certificates managed by the service or to provide your own X.509 certificates.

        The following is an example of a `parameters.json` with the certificates managed by the service.

        ```
        {
          "x509": {
            "key-length": 2048,
            "validity": 7,
            "validity-type": "DAYS"
          }
        }
        ```

        Reference this file when you bind the service. For example:

        ```
        cf bind-service myApp myXSUAA -c parameters.json
        ```

    -   In a manifest file, provide the binding parameters.

        The following is an example of a `manifest.xml` with certificates you provide.

        ```
        ---
        applications:
          - name: myApp
            memory: 1024M
            services:
              - name: myXSUAA
                parameters:
                  credential-type: x509
                  x509:
                    ensure-uniqueness: true
                    certificate: "-----BEGIN CERTIFICATE-----... -----END CERTIFICATE-----\n"
        
        ```



