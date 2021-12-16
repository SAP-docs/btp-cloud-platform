<!-- loioe5e77362635b40349497734c2480d506 -->

# Rotate X.509 Secrets

When your private key is exposed or your certificates are about to expire, it's time to rotate secrets. Rotating secrets can be as easy as unbinding and rebinding your application or service key.



<a name="loioe5e77362635b40349497734c2480d506__prereq_msw_g3w_sjb"/>

## Prerequisites

-   If you provide your own certificates, you've prepared new certificates.

-   If you need to replace any service keys, create the new service keys before proceeding.

    For more information, see [Creating Service Keys](../30_development/creating-service-keys-4514a14.md).




## Context

> ### Tip:  
> If the secret was configured with `certificate-pinning` was set to ***false***, you can skip unbinding and rebinding the application. Just use a new certificate with the same subject and issuer distinguished name \(DN\). The service saves the new validity date of the new certificate. Certificates with older validity dates are rejected.

> ### Note:  
> The service doesn't check for certificate revocation. The only way to revoke an X.509 secret is to rotate the secret.



## Procedure

1.  Unbind the application that consumes your service instance.

    Use the following syntax:

    `cf unbind-service *<APP\_NAME\>* *<SERVICE\_INSTANCE\>*`

    ```
    cf unbind-service my-app my-xsuaa-service
    ```

2.  Rebind the application that consumes your service instance.

    Use the following syntax:

    `cf bind-service *<APP\_NAME\>* *<SERVICE\_INSTANCE\>* [-c *<PARAMETERS\_AS\_JSON\>*]`

    ```
    cf bind-service my-app my-xsuaa-service -c parameters.json
    ```

    If you provide your own certificates, include them in a `parameters.json` file.


**Related Information**  


[Binding Parameters of X.509 Secrets](binding-parameters-of-x-509-secrets-3240307.md "When binding applications or creating service keys for services instances of the SAP Authorization and Trust Management service (XSUAA) you can configure what kinds of X.509 certificates to use for secrets. The service can generate certificates for you or, if you already have your own public key infrastructure (PKI), you can use your own.")

[Binding Service Instances to Applications](../30_development/binding-service-instances-to-applications-e98280a.md "Use the SAP BTP cockpit or the Cloud Foundry Command Line Interface to bind service instances to applications:")

[Service Instance Secrets](service-instance-secrets-5578ec4.md "When an application consumes a service instance of the SAP Authorization and Trust Management service (XSUAA), the application identifies itself to the service instance with a client ID and a secret. The client ID and secret are the credentials with which an application authenticates itself to the service instance.")

