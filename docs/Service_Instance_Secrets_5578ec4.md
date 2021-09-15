<!-- loio5578ec4b20e84d61b34fd0fe0d6deed5 -->

# Service Instance Secrets

When an application consumes a service instance of the SAP Authorization and Trust Management service \(XSUAA\), the application identifies itself to the service instance with a client ID and client secret. The client ID and client secret are the credentials with which an application authenticates itself to the service instance.

The system creates these credentials either when you bind the application to the service instance or when you create a service key for the service instance.

The service instance can use multiple secrets in the ***application*** plan.

-   The instance secret is the default secret. The secret is the same for all bindings of the service instance. The secret remains valid as long as the instance exists.

-   The binding secret must be enabled in the application security descriptor \(`xs-security.json`\) when you deploy the application. The secret remains valid as long as the binding or the service key exists.


> ### Note:  
> The ***apiaccess*** plan only uses binding secrets. However, some old instances of the ***apiaccess*** plan might still use the instance secret.

The following figure illustrates the XSUAA app and its information about the OAuth 2.0 client as part of a SAP Authorization and Trust Management service instance. A consuming application, functioning as an OAuth 2.0 client is bound to the SAP Authorization and Trust Management service instance. The instance secret is part of the environment of the consuming application and the information about the OAuth 2.0 client saved with the XSUAA app. Alternatively, this information is saved as part of a service key.

   
  
<a name="loio5578ec4b20e84d61b34fd0fe0d6deed5__fig_eyd_prh_sjb"/>Binding Between a SAP Authorization and Trust Management Service Instance and a Consuming Application

 ![](images/BindingInformation_4bcb021.png "Binding Between a SAP
									Authorization and Trust Management Service
				Instance and a Consuming Application") 

The `credential-types` parameter of the OAuth client configuration in the application security descriptor \(`xs-security.json`\) determines which secrets bindings support.

In the following example, the service instance creates a binding secret for all new bindings, but still accepts the instance secret.

> ### Example:  
> > ### Sample Code:  
> > ```
> > "oauth2-configuration": {
> >     "credential-types": ["binding-secret","instance-secret"]
> > }
> > ```

In the following example, the service instance creates a binding secret for all new bindings, but doesn’t accept the instance secret.

> ### Example:  
> > ### Sample Code:  
> > ```
> > "oauth2-configuration": {
> >     "credential-types": ["binding-secret"]
> > }
> > ```

**Related Information**  


[Rotate Binding Secrets](Rotate_Binding_Secrets_618441b.md "Service instances of the SAP Authorization and Trust Management service use different binding secrets for each binding. To rotate binding secrets, unbind and rebind any consuming applications.")

[Rotating Instance Secrets](Rotating_Instance_Secrets_8bfbbf5.md "When configured for instance secrets, a service instance of the SAP Authorization and Trust Management service uses the same instance secret for all bindings. You can't really rotate instance secrets, but must rotate the applications and service instance together.")

[Migrate from Instance Secrets to Binding Secrets](Migrate_from_Instance_Secrets_to_Binding_Secrets_dcee867.md "To simplify the management of secrets for service instances of the SAP Authorization and Trust Management service, we recommend that you configure service instances to use binding secrets.")

