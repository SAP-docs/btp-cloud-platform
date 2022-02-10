<!-- loioe5e77362635b40349497734c2480d506 -->

# Rotate X.509 Secrets

When your private key is exposed or your certificates are about to expire, it's time to rotate secrets. Rotating secrets can be as easy as unbinding and rebinding your application or service key.



<a name="loioe5e77362635b40349497734c2480d506__prereq_msw_g3w_sjb"/>

## Prerequisites

-   If you provide your own certificates, you've prepared new certificates.

-   If you need to replace any service keys, create the new service keys before proceeding.

    For more information, see [Creating Service Keys](../30-development/creating-service-keys-4514a14.md).




## Context

> ### Note:  
> The service doesn't check for certificate revocation. To stop the service from accepting a certificate that is still valid, delete the relevant bindings or service keys. As soon as the binding is deleted, the service stops accepting the certificate.
> 
> For bindings with self-managed certificates and the `certificate-pinning` parameter set to ***false***, you can rotate the secrets without deleting bindings. Just use a new certificate with the same subject and issuer distinguished name \(DN\). The service saves the new validity date of the new certificate.
> 
> For more information, see [Parameters for Self-Managed X.509 Certificates](parameters-for-self-managed-x-509-certificates-5168df6.md).



## Procedure

1.  Unbind the application that consumes your service instance.

    Use the following syntax:

    <code>cf unbind-service <i class="varname">&lt;APP_NAME&gt;</i> <i class="varname">&lt;SERVICE_INSTANCE&gt;</i></code>

    ```
    cf unbind-service my-app my-xsuaa-service
    ```

2.  Rebind the application that consumes your service instance.

    Use the following syntax:

    <code>cf bind-service <i class="varname">&lt;APP_NAME&gt;</i> <i class="varname">&lt;SERVICE_INSTANCE&gt;</i> [-c <i class="varname">&lt;PARAMETERS_AS_JSON&gt;</i>]</code>

    ```
    cf bind-service my-app my-xsuaa-service -c parameters.json
    ```

    If you provide your own certificates, include them in a `parameters.json` file.


**Related Information**  


[Binding Parameters of SAP Authorization and Trust Management Service](binding-parameters-of-sap-authorization-and-trust-management-service-3240307.md "When binding applications or creating service keys for services instances of the SAP Authorization and Trust Management service (XSUAA), provide configuration parameters in JSON format.")

[Binding Service Instances to Applications](../30-development/binding-service-instances-to-applications-e98280a.md "Use the SAP BTP cockpit or the Cloud Foundry Command Line Interface to bind service instances to applications:")

[Service Instance Secrets](service-instance-secrets-5578ec4.md "When an application consumes a service instance of the SAP Authorization and Trust Management service (XSUAA), the application identifies itself to the service instance with a client ID and a secret. The client ID and secret are the credentials with which an application authenticates itself to the service instance.")

