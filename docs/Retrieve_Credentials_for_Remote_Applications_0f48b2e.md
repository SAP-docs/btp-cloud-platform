<!-- loio0f48b2e84d73489692450ea7bf4d1916 -->

# Retrieve Credentials for Remote Applications

You need to get the credentials of a service instance for an application that runs outside of the instance of the Cloud Foundry environment at SAP BTP.



<a name="loio0f48b2e84d73489692450ea7bf4d1916__prereq_tdj_3nb_yfb"/>

## Prerequisites

-   A service instance for your application is available.




## Context

> ### Note:  
> Applications that run inside the instance of the Cloud Foundry environment at SAP BTP get their credentials after the respective service has been bound to the application. However, you cannot use binding for an application that runs outside of the instance of the Cloud Foundry environment at SAP BTP.

Instead, you use a service key that is created in the service instance of the remote application. You need to get the credentials of the service instance for the remote application. The UAA service broker manages all credentials, including those of the remote applications. The credentials you need are the OAuth 2.0 client ID and the client secret.

First you generate a service key for the service instance of the remote application to enable access to the UAA service broker. Then you retrieve the generated service key with the credentials, including the OAuth 2.0 client ID and the client secret, from the UAA service broker. The remote application stores the service key. The application can now use this service key with the credentials \(OAuth 2.0 client ID and the client secret of the remote application\).



## Procedure

1.  Create a service key for the service instance of the remote application.

    `cf create-service-key <service_instance_name> <service-key-name>`

    > ### Example:  
    > `cf create-service-key rem-app-service rem-app-sk`

2.  You want to retrieve the credentials including the OAuth 2.0 client ID and the client secret for the service instance of your remote application. Use the following command:

    `cf service-key <service_instance_name> <service_key_name>`

    > ### Example:  
    > `cf service-key rem-app-service rem-app-sk`

    > ### Output Code:  
    > ```
    > {
    >   "clientid" : "sb-sample-app!i1",
    >   "verificationkey" : "-----BEGIN PUBLIC KEY-----MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAyi7TbPYgsIV5t2WdkabI/XWoyrTTzIZCj0mxbp+LMdVCrmufbT9bwZ2ZJlHB3x0DKk3Os9g2CFiB/2yCMm/jJe2CJJ06zhYGRIZwSu6r7Is7R4TEs8bhCQEV25LvEbK2qvZMUjxcjU+13VkN9NYViF9PRhbMxRX7i9OJeBHn/JyYFvvBxUnCIfiiLpnMiNB0tDkNf0EcPd3TWvmR8KwQGNnPT5ccpMD5fKQoC/K5wVy+BWa43Z1d3AAA4QYBPVQX+PcWifulF7xtZVqLPMDE4Q8eWQYaiGkk6A+RO0RCIJ/byMbvm50SPe8S6+obB/3j0eJ4b7phGFjpZbTv1UQIDAQAB-----END PUBLIC KEY-----",
    > 
    >   "xsappname" : "sample-app!i1", 
    >   "identityzone" : "uaa",
    >   "clientsecret" : "+Pf4sw356jkfDxlK9Hz2nX1gH3sysb2sOW627XOjwUyc2F55OYagpiaPrk+AdbqBwTSi8a5qWLPI\njQvQpTPLIA==",
    >   "url" : "https://host.acme.com:30632/uaa-security"
    > }
    > ```


