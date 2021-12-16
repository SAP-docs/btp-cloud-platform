<!-- loio618441ba629e4348831e5e5e51521592 -->

# Rotate Binding Secrets

Service instances of the SAP Authorization and Trust Management service use different binding secrets for each binding. To rotate binding secrets, unbind and rebind any consuming applications.



<a name="loio618441ba629e4348831e5e5e51521592__prereq_msw_g3w_sjb"/>

## Prerequisites

-   You've enabled support for binding secrets.

    For more information, see [Migrate from Instance Secrets to Binding Secrets](migrate-from-instance-secrets-to-binding-secrets-dcee867.md).

-   If you have to replace any service keys, create the new service keys before proceeding.

    For more information, see [Creating Service Keys](../30_development/creating-service-keys-4514a14.md).




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
    cf bind-service my-app my-xsuaa-service
    ```




<a name="loio618441ba629e4348831e5e5e51521592__result_nnf_m3w_sjb"/>

## Results

When you rebind the application, the system creates a new binding secret.



<a name="loio618441ba629e4348831e5e5e51521592__postreq_zrm_m3w_sjb"/>

## Next Steps

Delete any old service keys that you don't need anymore.

**Related Information**  


[Service Instance Secrets](service-instance-secrets-5578ec4.md "When an application consumes a service instance of the SAP Authorization and Trust Management service (XSUAA), the application identifies itself to the service instance with a client ID and a secret. The client ID and secret are the credentials with which an application authenticates itself to the service instance.")

