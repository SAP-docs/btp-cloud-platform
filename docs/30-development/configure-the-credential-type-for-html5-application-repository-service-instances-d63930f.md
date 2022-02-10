<!-- loiod63930fa8042402f96003cdf46111529 -->

# Configure the Credential Type for HTML5 Application Repository Service Instances

When you create an HTML5 application repository service instance key or bind a service instance to an application, values for `client_id` and `client_secret` are generated. The `client_secret` is the equivalent to a password.

As of January 28, 2021, the credential type `binding_secret` is automatically used for the `client_ secret` value of new HTML5 application repository service instance keys. This increases the security because the credential type `binding_secret` creates a new `client_secret` for each binding and service key.

If you have older HTML5 application repository service instances, the `client_secret` value is the same for all bindings and service keys because the HTML5 application repository still uses the credentials type `instance_secret` for older HTML5 application repository service instances. To configure the more secure credential type `binding_secret` for your older HTML5 application repository service instances, please follow the instructions in [Configure the Credential Type binding\_secret for HTML5 Application Repository Service Instances](configure-the-credential-type-for-html5-application-repository-service-instances-d63930f.md#loiod63930fa8042402f96003cdf46111529__section_binding_secret).

As an alternative to the credential type `binding_secret`, you can also use the credential type `x.509` to authenticate your apps with X.509 certificates. For more information, see [Credential Type x509 for HTML5 Application Repository Service Instances](configure-the-credential-type-for-html5-application-repository-service-instances-d63930f.md#loiod63930fa8042402f96003cdf46111529__section_x509).



<a name="loiod63930fa8042402f96003cdf46111529__section_binding_secret"/>

## Configure the Credential Type `binding_secret` for HTML5 Application Repository Service Instances

1.  Extract the UUID part of the `xsappname` from the of the existing instance. For example:

    1.  > ### Sample Code:  
        > ```
        > cf create-service-key <serviceInstanceName> <serviceInstanceKeyName>
        > ```

    2.  > ### Sample Code:  
        > ```
        > 
        > cf service-key <serviceInstanceName> <serviceInstanceKeyName>
        > ……
        > "clientsecret": "HksDYy9RxYFUQeOHIzprqBam3vQ=", //Old instance secret
        > …
        >   "xsappname": "fec39a25-a570-46b0-8ac9-1691f8d663cc!b6711|html5-apps-repo-uaa!b6711",
        > ……
        > 
        > ```

    3.  Copy the UUID. In this example: **fec39a25-a570-46b0-8ac9-1691f8d663cc** 


2.  Create a file `instance-xs-security.json`, such as the following:

    > ### Sample Code:  
    > ```
    > 
    >  {
    >   "xs-security": {
    >     "xsappname": "fec39a25-a570-46b0-8ac9-1691f8d663cc",
    >     "oauth2-configuration": {
    >       "credential-types": ["binding-secret"]
    >     }
    >   }
    >  
    > 
    > ```

3.  Update the service instance:

    > ### Sample Code:  
    > ```
    > cf update-service <serviceInstanceName>  -c instance-xs-security.json
    > ```

4.  Check that the instance now creates binding secrets as follows:

    1.  > ### Sample Code:  
        > ```
        > cf create-service-key <serviceInstanceName>  <serviceInstanceKeyNameNew>       
        > ```

    2.  > ### Sample Code:  
        > ```
        > 
        > cf service-key <serviceInstanceName>  <serviceInstanceKeyNameNew>
        >  ……..
        > "clientid": "sb-fec39a25-a570-46b0-8ac9-1691f8d663cc!b6711|html5-apps-repo-uaa!b6711",
        >   "clientsecret": "8c902673-00d4-471f-9ebb-4463d4073fda$7NIo5batSFZCF1RNGcpNkRfo4mDj6vq-cElDFIcvcwg=", //New binding secret (long)
        > 
        >   "identityzone": …..,
        >   "identityzoneid": …..,
        >                                …….
        > 
        > ```





<a name="loiod63930fa8042402f96003cdf46111529__section_x509"/>

## Credential Type x509 for HTML5 Application Repository Service Instances

To use the HTML5 application repository service and authenticate with X.509 certificate, you need to acquire the required key, certificate, and base URLs. These are provided when you create an instance of the HTML5 application repository service and a binding or a service key for the instance.

When you bind an HTML5 applications repository service instance to an application, you have to explicitly provide the required configuration parameters for the authentication with x.509:

<code>cf bind-service &lt;application&gt; &lt;service-instance&gt; <b>-c parameters.json</b></code>

The same applies if you create service keys:

<code>cf create-service-key &lt;service-instance&gt; &lt;key-name&gt; <b>-c parameters.json</b></code>

The configuration for the credential type x509 must be wrapped with xsuaa. You have to use exactly the following format for the configuration:

```
{
  "xsuaa": {
    "credential-type": "x509",
    "x509": {
      "key-length": 2048, // specifies the byte length of the generated private key,
                          // defaults to 2048
      "validity": 7, // specifies the number of time units in validity-type,
                     // defaults to 7, thus the complete validity defaults to 7 days
      "validity-type": "DAYS" // specifies the validity time unit,
                              // only DAYS, MONTHS and YEARS are supported,
                              // defaults to DAYS
    }
  }
}
```

> ### Note:  
> The following applies to existing HTML5 application repository service instances:
> 
> Before you create a binding to a service instance or a service key as described above, you have to update of the service instance of your existing HTML5 application repository service instance. Use parameters to provide the configuration during the update of the existing service instance:
> 
> <code>cf update-service &lt;service-instance&gt; <b>-c update-instance-xs-security.json</b></code>
> 
> To configure the credential type x509 for existing HTML5 application repository service Instances, please follow the instructions below:



### Configuring Credential Type x509 for Existing HTML5 Application Repository Service Instances

To configure the credential type x509 for your existing HTML5 application repository service instances, perform the following steps:

1.  Extract the UUID part of the xsappname from the service key or the binding for the service instance. For example:

    1.  > ### Sample Code:  
        > ```
        > cf service-key <serviceInstanceName> <existingServiceInstanceKeyName>
        > ……
        > "clientsecret": "HksDYy9RxYFUQeOHIzprqBam3vQ=", //Old instance secret
        > …
        > "xsappname": "fec39a25-a570-46b0-8ac9-1691f8d663cc!b6711|html5-apps-repo-uaa!b6711",
        > ……
        > ```

    2.  Copy the UUID. In this example: **fec39a25-a570-46b0-8ac9-1691f8d663cc**


2.  Create a file `update-instance-xs-security.json` with the following format:

    > ### Sample Code:  
    > ```
    > {
    >  "xs-security": {
    >    "xsappname": "fec39a25-a570-46b0-8ac9-1691f8d663cc", //The UUID that was extracted before
    >    "oauth2-configuration": {
    >      "credential-types": ["x509"]
    >    }
    >  }
    > ```

3.  Update the service instance:

    `cf update-service <serviceInstanceName> -c update-instance-xs-security.json`

4.  Create a file `parameters.json`, such as the following: :

    > ### Sample Code:  
    > ```
    > {
    >   "xsuaa": {
    >     "credential-type": "x509",
    >     "x509": {
    >       "key-length": 2048,
    >       "validity": 7,
    >       "validity-type": "DAYS"
    >     }
    >   }
    > }
    > ```

    \(Note that the values of the "x509" properties used here are just examples.\)

5.  Create a binding or a service key with the credential type x509 configuration \(`parameters.json` file\). For example:

    `cf create-service-key <serviceInstanceName> <serviceInstanceKeyNameNew> -c parameters.json`

6.  Check that the instance now creates a certificate and that the credential-type is "x509", as follows:

    `cf service-key <serviceInstanceName> <serviceInstanceKeyNameNew>`

    The following binding is generated as a result:

    ```
    {
      ......
      "certificate": "-----BEGIN CERTIFICATE-----...-----END CERTIFICATE-----\n-----BEGIN CERTIFICATE-----..-----END CERTIFICATE-----\n-----BEGIN CERTIFICATE-----...-----END CERTIFICATE-----\n",
      "clientid": "........",
      "credential-type": "x509",
      ......
    }
    ```


