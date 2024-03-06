<!-- loio0f48b2e84d73489692450ea7bf4d1916 -->

# Retrieve Credentials for Remote Applications

You need to get the credentials of a service instance for an application that runs outside of the instance of the Cloud Foundry environment at SAP BTP.



<a name="loio0f48b2e84d73489692450ea7bf4d1916__prereq_tdj_3nb_yfb"/>

## Prerequisites

-   A service instance for your application is available.

    > ### Note:  
    > The default credential type is `binding-secret`. If, as an option, you want to use authentication with mutual transport layer security \(mTLS\), you must enable the `x.509` credential type in your application security descriptor file \(see [oauth2-configuration](application-security-descriptor-configuration-syntax-517895a.md#loio517895a9612241259d6941dbf9ad81cb__section_zfs_lj3_rz)\).




## Context

> ### Note:  
> Applications that run inside the service manager instance at SAP BTP get their credentials after the respective service has been bound to the application. However, you can't use binding for an application that runs outside of the service manager instance at SAP BTP.

Instead, you use a service key that is created in the service instance of the remote application. You need to get the credentials of the service instance for the remote application. The UAA service broker manages all credentials, including those of the remote applications. The credentials you need are the OAuth 2.0 client ID and the client secret or X.509

First you generate a service key for the service instance of the remote application to enable access to the UAA service broker. Then you retrieve the generated service key with the credentials, including the OAuth 2.0 client ID and the client secret or X.509, from the UAA service broker. The remote application stores the service key. The application can now use this service key with the credentials \(OAuth 2.0 client ID and the client secret of the remote application\).



## Procedure

1.  Create a service key for the service instance of the remote application. If you want to use mutual transport layer security \(mTLS\), include the `x.509` credential type in a separate configuration file \(see [Enable mTLS Authentication to SAP Authorization and Trust Management Service for Your Application](enable-mtls-authentication-to-sap-authorization-and-trust-management-service-for-your-app-aa80338.md) and [Binding Parameters of SAP Authorization and Trust Management Service](../50-administration-and-ops/binding-parameters-of-sap-authorization-and-trust-management-service-3240307.md)\).

    `cf create-service-key <service_instance_name> <service-key-name>`

    > ### Example:  
    > `cf create-service-key rem-app-service rem-app-sk`

    \(For mTLS\) `cf create-service-key <service_instance_name> <service-key-name> -c <parameter_file>`

    > ### Example:  
    > `cf create-service-key rem-app-service rem-app-sk -c parameters.json`

2.  You want to retrieve the credentials including the OAuth 2.0 client ID and the client secret for the service instance of your remote application. Use the following command:

    `cf service-key <service_instance_name> <service_key_name>`

    > ### Example:  
    > `cf service-key rem-app-service rem-app-sk`

    Output with default `binding-secret` credential type:

    > ### Output Code:  
    > ```
    > {
    >   "clientid" : "sb-sample-app!i1",
    >   "verificationkey" : "-----BEGIN PUBLIC KEY-----MIIBIjANBgkqhkiG7w0BAQEFAAOCAQ1AMIIBCgKCEFEAyi7TbPYgsIV5t2WdkabI/XWryrTCzIZCj0mxbp+LMdVCrmufbT9bwZ2ZJlHB3x0DKk3Os9g2CFiB/2yCMm/jJe2CJJ06zhYGRIZwSu6r7Is7R4TEs8bhCQEV25LvEbK2qvZMUjxcjU+13VkN9NYViF9PRhbMxRX7i9OJeBHn/JyYFvvBxUnCIfiiLpnMiNB0tDkNf0EcPd3TWvmR8KwQGNnPT5ccpMD5fKQoC/K5wVy+BWa43Z1d3AAA4QYBPVQX+PcWifulF7xtZVqLPMDE4Q8eWQYaiGkk6A+RO0RCIJ/byMbvm50SPe8S6+obB/3j0eJ4b7phGFjpZbTv1UQIDAQAB-----END PUBLIC KEY-----",
    > 
    >   "xsappname" : "sample-app!i1", 
    >   "identityzone" : "uaa",
    >   "clientsecret" : "+Pf4sw772jkfDxlK9Hz2nX1gH3ycUb9sOW627XOjwUyc2F45OYagpiaPrk+AdbqBwTSi3a5qWLMI\njQvQpTPLIA==",
    >   "url" : "https://host.acme.com:40654/uaa-security"
    > }
    > ```

    \(For mTLS\) Output with `x.509` credential type:

    > ### Output Code:  
    > ```
    > {
    >   "credentials":
    > {
    >      "clientid": "sb-clone6e6b1297ff5a3accbb62c8ca0527mj5f!b75124|destination-xsappname!b13",
    >      "clientsecret": "ba306a76-832b-20de-bab1-2b24854f1cfd$NMlHejN9vh7MCL0EQ5XJ0S8OCwm649hGQnBWwAczV2A=",
    >      "credential-type": "binding-secret",
    >      "identityzone": "mysubaccoount-hmq7lrea",
    >      "instanceid": "6e5b8786-ff5a-4bcc-dd74-c6db0527cf5f",
    >      "tenantid": "094e5a7d-c590-6030-98b4-2cbb6e8fdfb5",
    >      "tenantmode": "dedicated",
    >      "uaadomain": "auth.corpdcen.acme.ondemand.com",
    >      "uri": "https://destination-configuration.cfapps.corpdcen.acme.ondemand.com",
    >      "url": "https://mysubaccount-hmq7frea.auth.corpdcen.acme.ondemand.com",
    >      "verificationkey": "-----BEGIN PUBLIC KEY-----\nMIIBIjANBglmbkiG9w0BAQEFAAOCBK8AMIICDgKDBQEAth3jstKlvvYAXZ5rHqkk\nTCRtTW3hJZbkzwmrAs5mTdjNdZZkA6AAMB8ZBkp0Qaw/CEsaUJseQVrCXhcwSz3P\nMoldRta/qVOyXDExkpW9pwh7T1S9vugmIkEMRW69cUVc1DQpC0q8pc1IdNHQ4y1p\nu2JerMSRaDX5CyzRuz4uqJtrCrhwIZt/+B13nuLKZgCbtTxkBNOGh2E7OnnpepDt\n52iXtMKvcxeRJzWKWx+No6+660wcRq46h/3nPWa+7IGmOswy2Cu4X35pSf5atIxj\nRWBEaI5IygaSq+mskKSowmcChYX7xdmPkDBO0GZaEtSYlPBcK/ZpkXN1Nr2DbEoq\n7wIDAQAB\n-----END PUBLIC KEY-----",
    >      "xsappname":
    > ..}
    > }
    > ```

    \(For mTLS\) If your service needs an X.509 certificate and private key for mutual transport layer security \(mTLS\) in a single privacy enhanced mail \(PEM\) file, see [Extract Certificates for Mutual Transport Layer Security](https://help.sap.com/viewer/df50977d8bfa4c9a8a063ddb37113c43/Cloud/en-US/8a542ce870714550a3e70dc50bd453e6.html "Some SAP BTP services such as the SAP Destination service need an X.509 certificate and private key for mutual transport layer security (mTLS) in a single privacy enhanced mail (PEM) file. Extract this information from the service key of the service that needs to authenticate with the authentication server.") :arrow_upper_right:.


