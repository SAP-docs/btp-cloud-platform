<!-- loiod63930fa8042402f96003cdf46111529 -->

# Configure the Credential Type for HTML5 Application Repository Service Instances

When you create an HTML5 application repository service instance key or bind a service instance to an application, values for `client_id` and `client_secret` are generated. The `client_secret` is the equivalent to a password.

As of January 28, 2021, the credential type `binding_secret` is automatically used for the `client_ secret` value of new HTML5 application repository service instance keys. This increases the security because the credential type `binding_secret` creates a new `client_secret` for each binding and service key.

If you have older HTML5 application repository service instances, the `client_secret` value is the same for all bindings and service keys because the HTML5 application repository still uses the credentials type `instance_secret` for older HTML5 application repository service instances. To configure the more secure credential type `binding_secret` for your older HTML5 application repository service instances, please follow the instructions below.



<a name="loiod63930fa8042402f96003cdf46111529__section_np5_gy2_f4b"/>

## Configure the Credential Type `binding_secret` for HTML5 Application Repository Service Instances



1.  Extract the UUID part of the `xsappname` from the existing instance. For example:

    1.  > ### Sample Code:  
        > ```
        > cf create-service-key <serviceInstanceName> <serviceInstanceKeyName>
        > ```

    2.  > ### Sample Code:  
        > ```
        > 
        > cf service-key <serviceInstanceName> <serviceInstanceKeyName>
        > ……
        > "clientsecret": "HksDYy9RxYFUQeOHIzprqBam3vQ=", **//Old instance secret**
        > …
        >   "xsappname": "**fec39a25-a570-46b0-8ac9-1691f8d663cc**!b6711|html5-apps-repo-uaa!b6711",
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
    >     "xsappname": "**fec39a25-a570-46b0-8ac9-1691f8d663cc**",
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
    > cf update-service <serviceInstanceName>  -c **instance-xs-security.json**
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
        >   "clientsecret": "**8c902673-00d4-471f-9ebb-4463d4073fda$7NIo5batSFZCF1RNGcpNkRfo4mDj6vq-cElDFIcvcwg=", //New binding secret \(long\)
        > **
        >   "identityzone": …..,
        >   "identityzoneid": …..,
        >                                …….
        > 
        > ```


