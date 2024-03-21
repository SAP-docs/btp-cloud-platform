<!-- loio0f48b2e84d73489692450ea7bf4d1916 -->

# Retrieve Credentials for Remote Applications

You need to get the credentials of a service instance for an application that runs outside SAP BTP.



<a name="loio0f48b2e84d73489692450ea7bf4d1916__prereq_tdj_3nb_yfb"/>

## Prerequisites

-   A service instance for your application is available.

    > ### Note:  
    > For mutual transport layer security \(mTLS\), the application security descriptor supports the `binding-secret` and `x509` credential types by default. For the creation of a service key that enables the `x509` credential type, you need to pass a parameter file. See [Binding Parameters of SAP Authorization and Trust Management Service](../50-administration-and-ops/binding-parameters-of-sap-authorization-and-trust-management-service-3240307.md).




## Context

> ### Note:  
> Applications that run inside the service manager instance at SAP BTP get their credentials after the respective service has been bound to the application. However, you can't use binding for an application that runs outside of the service manager instance at SAP BTP.

Instead, you use a service key that is created in the service instance of the remote application. You need to get the credentials of the service instance for the remote application. The UAA service broker manages all credentials, including those of the remote applications. The credentials you need are the OAuth 2.0 client ID and the client secret, or X.509 certificates.

First you generate a service key for the service instance of the remote application to enable access to the UAA service broker. Then you retrieve the generated service key with the credentials, including the OAuth 2.0 client ID and the client secret or X.509 certificates, from the UAA service broker. The remote application stores the service key. The application can now use this service key with the credentials \(OAuth 2.0 client ID and the client secret of the remote application\).

> ### Remember:  
> Rotate credentials before they expire or, if they don't expire, rotate them regularly \(see [Security Recommendations for SAP Authorization and Trust Management Service](../60-security/security-recommendations-for-sap-authorization-and-trust-management-service-0578b80.md)\).



## Procedure

1.  Create a service key for the service instance of the remote application. If you want to use mutual transport layer security \(mTLS\), you may need to request it in a separate binding configuration file \(see [Enable mTLS Authentication to SAP Authorization and Trust Management Service for Your Application](enable-mtls-authentication-to-sap-authorization-and-trust-management-service-for-your-app-aa80338.md) and [Binding Parameters of SAP Authorization and Trust Management Service](../50-administration-and-ops/binding-parameters-of-sap-authorization-and-trust-management-service-3240307.md)\).

    `cf create-service-key <service_instance_name> <service-key-name>`

    > ### Example:  
    > `cf create-service-key rem-app-service rem-app-sk`

    \(For mTLS\) `cf create-service-key <service_instance_name> <service-key-name> -c <parameter_file>`

    > ### Example:  
    > `cf create-service-key rem-app-service rem-app-sk -c parameters.json`

    The `parameters.json` file can have the following content for the usage of XSUAA-managed certificates:

    > ### Sample Code:  
    > ```
    > {
    >  "credential-type": "x509"
    > }
    > ```

2.  You want to retrieve the credentials including the OAuth 2.0 client ID and the client secret for the service instance of your remote application. Use the following command:

    `cf service-key <service_instance_name> <service_key_name>`

    > ### Example:  
    > `cf service-key rem-app-service rem-app-sk`

    Output with default `binding-secret` credential type:

    > ### Output Code:  
    > ```
    > {
    >   "apiurl": "https://api.authentication.corpdcen.acme.ondemand.com",
    >   "clientid" : "sb-sample-app!t1",
    >   "clientsecret" : "<client_secret>",
    >   "credential-type": "binding-secret",
    >   "identityzone" : "uaa",
    >   "serviceInstanceId": "cbb63529-d725-4326-880c-92cbcdd92",
    >   "subaccountid": "194e6a6d-c590-5030-98b3-1baa6d8fcda4",
    >   "tenantid": "095e5a7f-c480-5030-98b3-1cbb6e8fdfb4",
    >   "uaadomain": "authentication.corpdcen.acme.ondemand.com",
    >   "url" : "https://host.acme.com:40654/uaa-security",
    >   "xsappname" : "sample-app!t1", 
    >   "..."
    > }
    > ```

    \(For mTLS\) Output with `x.509` credential type:

    > ### Sample Code:  
    > ```
    > {
    >   "credentials": {
    >     "apiurl": "https://api.authentication.corpdcen.acme.ondemand.com",
    >     "certificate": "-----BEGIN CERTIFICATE-----\nMIIFvDCCA6...KJu+8fcIaUp7MVBIVZ\n>-----END CERTIFICATE-----\n",
    >     "certificate-pinning": true,
    >     "certurl": "https://mysubaccount-hmq7frea.authentication.cert.corpdcen.acme.ondemand.com",
    >     "clientid": "sb-x5app!t75135",
    >     "credential-type": "x509",
    >     "key": "-----BEGIN RSA PRIVATE KEY-----\<private_key>\n-----END RSA PRIVATE KEY-----\n",
    >     "serviceInstanceId": "cbb52529-d614-4326-880c-92ba937bcc92",
    >     "subaccountid": "<subaccount_ID>",
    >     "tenantid": "194e6b7e-c370-4941-98b3-1cbb6e8fdfb4",
    >     "uaadomain": "authentication.corpdcen.acme.ondemand.com",
    >     "url": "https://<subaccount>-hmq7frea.authentication.corpdcen.acme.ondemand.com",
    >     "xsappname": "x5app!t75135",
    >     "..."
    >   }
    > }
    > ```

    If your service needs an X.509 certificate and private key for mutual transport layer security \(mTLS\) in a single privacy enhanced mail \(PEM\) file, see [Extract Certificates for Mutual Transport Layer Security](https://help.sap.com/viewer/df50977d8bfa4c9a8a063ddb37113c43/Cloud/en-US/8a542ce870714550a3e70dc50bd453e6.html "Some SAP BTP services such as the SAP Destination service need an X.509 certificate and private key for mutual transport layer security (mTLS) in a single privacy enhanced mail (PEM) file. Extract this information from the service key of the service that needs to authenticate with the authentication server.") :arrow_upper_right:.


