<!-- loio618441ba629e4348831e5e5e51521592 -->

# Rotate Binding Secrets

Service instances of the SAP Authorization and Trust Management service use different binding secrets for each binding. To rotate binding secrets, unbind and rebind any consuming applications.



<a name="loio618441ba629e4348831e5e5e51521592__prereq_msw_g3w_sjb"/>

## Prerequisites

-   You've enabled support for binding secrets.

    For more information, see [Migrate from Instance Secrets to Binding Secrets](Migrate_from_Instance_Secrets_to_Binding_Secrets_dcee867.md).

-   If you have to replace any service keys, create the new service keys before proceeding.

    For more information, see [Creating Service Keys](../30-development/Creating_Service_Keys_4514a14.md).




## Procedure

1.  Unbind the application that consumes your service instance.

2.  Rebind the application that consumes your service instance.




<a name="loio618441ba629e4348831e5e5e51521592__result_nnf_m3w_sjb"/>

## Results

When you rebind the application, the system creates a new binding secret.



<a name="loio618441ba629e4348831e5e5e51521592__postreq_zrm_m3w_sjb"/>

## Next Steps

Delete any old service keys that you don't need anymore.

**Related Information**  


[Service Instance Secrets](Service_Instance_Secrets_5578ec4.md "When an application consumes a service instance of the SAP Authorization and Trust Management service (XSUAA), the application identifies itself to the service instance with a client ID and client secret. The client ID and client secret are the credentials with which an application authenticates itself to the service instance.")

