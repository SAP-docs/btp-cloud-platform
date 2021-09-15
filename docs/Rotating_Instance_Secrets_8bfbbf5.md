<!-- loio8bfbbf5fb2094f8fafc9295ce6ea37a1 -->

# Rotating Instance Secrets

When configured for instance secrets, a service instance of the SAP Authorization and Trust Management service uses the same instance secret for all bindings. You can't really rotate instance secrets, but must rotate the applications and service instance together.

> ### Recommendation:  
> Migrate to using binding secrets instead of instance secrets.
> 
> Using instance secrets forces you to redeploy the entire application under a new `xsappname` and repeat the assignment of any role collections.
> 
> For more information, see [Migrate from Instance Secrets to Binding Secrets](Migrate_from_Instance_Secrets_to_Binding_Secrets_dcee867.md).

**Related Information**  


[Service Instance Secrets](Service_Instance_Secrets_5578ec4.md "When an application consumes a service instance of the SAP Authorization and Trust Management service (XSUAA), the application identifies itself to the service instance with a client ID and client secret. The client ID and client secret are the credentials with which an application authenticates itself to the service instance.")

