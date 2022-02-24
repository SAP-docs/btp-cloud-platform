<!-- loio3240307e513e4bceaa75e4134d337fab -->

# Binding Parameters of SAP Authorization and Trust Management Service

When binding applications or creating service keys for services instances of the SAP Authorization and Trust Management service \(XSUAA\), provide configuration parameters in JSON format.

Set parameters according to the following use cases:

-   For instance or binding secrets, you want to supress the creation of client secrets.

-   For X.509 secrets, set parameters according to the following scenarios:

    -   The SAP Authorization and Trust Management service generates certificates for you.

    -   You already have your own public key infrastructure \(PKI\), with certificates issued from one of the supported certificate authorities \(CA\). See the links in the related information.



> ### Remember:  
> The types of secrets that a service instance can accept in a binding or service key is configured in the application security descriptor \(`xs-security.json`\).
> 
> For more information, see [Application Security Descriptor Configuration Syntax](../30-development/application-security-descriptor-configuration-syntax-517895a.md).

**Related Information**  


[Parameters for Suppressing Client Secrets](parameters-for-suppressing-client-secrets-974ac87.md "When binding or creating a service key for an xsuaa service instance, you can pass some parameters in JSON format or in a JSON file (see cf bind-service and cf create-service-key in the related links). The &quot;hide-secret&quot; element enables you to suppress the client secret when binding or creating a service key. It's useful if some applications only want to bind the xsuaa service for authorization purposes.")

[Parameters for X.509 Certificates Managed by SAP Authorization and Trust Management Service](parameters-for-x-509-certificates-managed-by-sap-authorization-and-trust-management-servi-436ed68.md "Use the parameters to have the service generate X.509 certificates for you.")

[Parameters for Self-Managed X.509 Certificates](parameters-for-self-managed-x-509-certificates-5168df6.md "Use these parameters to provide your own certificates for a binding or service key to service instances of the SAP Authorization and Trust Management service (XSUAA).")

[Trusted Certificate Authorities for X.509 Secrets](trusted-certificate-authorities-for-x-509-secrets-edd5613.md "Service instances of the SAP Authorization and Trust Management service (XSUAA) trust the following certificate authorities (CA). To use your own public key infrastructure (PKI) for bindings, the certificates must be issued from one of these CAs.")

