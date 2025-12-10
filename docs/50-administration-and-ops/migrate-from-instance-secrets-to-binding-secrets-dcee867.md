<!-- loiodcee867db42e48d7b4f3243e41695a7a -->

# Migrate from Instance Secrets to Binding Secrets

To simplify the management of secrets for service instances of the SAP Authorization and Trust Management service, we recommend that you configure service instances to use binding secrets.



<a name="loiodcee867db42e48d7b4f3243e41695a7a__context_wfv_jcp_sjb"/>

## Context

By default, service instances of the SAP Authorization and Trust Management service use the instance secret for all bindings of the service instance. In the application security descriptor \(`xs-security.json`\), enable binding secrets for service instances. All bindings have their own secret. You can enable both at once for the following plans:

-   Application plan


The API access plan only uses binding secrets.



<a name="loiodcee867db42e48d7b4f3243e41695a7a__steps_dsb_kcp_sjb"/>

## Procedure

1.  Modify the application security descriptor \(`xs-security.json`\) to support both instance secrets and binding secrets.

    Edit the OAuth client configuration of the `xs-security.json` as follows:

    > ### Sample Code:  
    > ```
    > "oauth2-configuration": {
    >     "credential-types": ["binding-secret","instance-secret"]
    > }
    > ```

2.  Update the service instance with the new application security descriptor.

3.  Unbind and rebind any consuming applications.

    With each new binding, the system creates a new binding secret.

4.  Replace any service keys with new service keys.

    At this point, none of the applications consuming your service instance need the instance secret anymore.

5.  Modify the application security descriptor \(`xs-security.json`\) to disable support for instance secrets.

    Edit the OAuth client configuration of the `xs-security.json` as follows:

    > ### Sample Code:  
    > ```
    > "oauth2-configuration": {
    >     "credential-types": ["binding-secret"]
    > }
    > ```

6.  Update the service instance with the new application security descriptor.


**Related Information**  


[Update a Service Instance](../30-development/update-a-service-instance-7f926eb.md "You can update a service instance from the xsuaa service using the service broker.")

[Creating Service Keys](../30-development/creating-service-keys-4514a14.md "You can use service keys to generate credentials to communicate directly with a service instance. Once you configure them for your service, local clients, apps in other spaces, or entities outside your deployment can access your service with these keys.")

[Service Instance Secrets](service-instance-secrets-5578ec4.md "When an application consumes a service instance of the SAP Authorization and Trust Management service (XSUAA), the application identifies itself to the service instance with a client ID and a secret. The client ID and secret are the credentials with which an application authenticates itself to the service instance.")

