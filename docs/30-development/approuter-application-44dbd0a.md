<!-- loio44dbd0ae4d4b4d9c9c8371d711c22bfe -->

# Approuter Application



To authenticate business users of the application at runtime, a tenant-aware approuter application and the `xsuaa` service in SAP Business Technology Platform are used. This will also provide the necessary callbacks for the SaaS Provisioning Service.

The enhanced approuter application is as a logical part of the multitenant application and configured as an external access point of the application.

For more details on the application router, see [Application Router.](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/01c5f9ba7d6847aaaf069d153b981b51.html)

With the middleware `@sap/asp-middleware` component a library \(npm module\) is provided that enhances the approuter to also take care of automatically routing the consumer to their ABAP tenants. See [@sap/asp-middleware.](https://www.npmjs.com/package/@sap/asp-middleware) 



### Approuter Configuration

To make sure that the approuter routes all relevant requests to the ABAP Solution, a routing configuration is configured:

> ### Sample Code:  
> ```
> {
> 								"authenticationMethod": "route",
> 								"welcomeFile": "/ui",
> 								"logout": {
> 								"logoutEndpoint": "/sap/public/bc/icf/logoff",
> 								"logoutPage": "/ui"
> 								},
> 								"routes": [
> 								{
> 								"source": "^/sap/(.*)$",
> 								"target": "/sap/$1",
> 								"authenticationType": "xsuaa",
> 								"service": "com.sap.cloud.abap.solution",
> 								"csrfProtection": false
> 								},
> 								{
> 								"source": "^/ui(.*)$",
> 								"target": "/ui$1",
> 								"authenticationType": "xsuaa",
> 								"service": "com.sap.cloud.abap.solution",
> 								"csrfProtection": false
> 								}
> 								]
> 								}
> 							
> ```

-   **Requests to the …/sap/… path**are backend requests and will be routed to the ABAP Solution service after successful authentication. CSRF token protection is disabled for this route as CSRF protection is already enforced via the underlying services in the ABAP system.

-   **Requests to the …/ui/…**are requests to FLP and will be routed to the ABAP Solution service after successful authentication. CSRF token protection is disabled for this route as CSRF protection is already enforced via the underlying services in the ABAP system.


For more details on the parameters, see [Routing Configuration File.](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/c103fb414988447ead2023f768096dcc.html)



### Approuter Multitenancy

When a consumer accesses the application, their consumer tenant calls the multitenant application via the application router with their tenant-specific URL. The URL follows the same pattern for all application consumers and differs depending on the implementation phase of the multitenant application:

-   **During development phase:**

    `<SUBSCRIBER_TENANT_SUBDOMAIN>-<APPROUTER_APPLICATION_HOST>.<SAP-PROVIDED_STANDARD_DOMAIN>`

    In each development landscape, SAP provides a different standard domain you can use to create URLs.

    Using that domain, and following the specified URL structure, a created URL would be:

    tenant1-myapprouter.cfapps.sap.hana.ondemand.com

    Here `tenant1-myapprouter` is the hostname, and `cfapps.sap.hana.ondemand.com` is the SAP-provided standard domain for this development landscape. In this format, a new route must be created manually for each new tenant.

    The common pattern identifying tenant-specific URLs is defined with `TENANT_HOST_PATTERN: ^(.*)->-<APPROUTER_APPLICATION_HOST>.<SAP-PROVIDED_STANDARD_DOMAIN>`

-   **During production phase:**

    `*.<YOUR_CUSTOM_DOMAIN>`

    A custom domain is registered via the custom domain service, then a pattern with \* as the wildcard hostname can be established.

    In this format, since the wildcard is replaced by an actual tenant during runtime, there is no need to create a new route for each new tenant manually.

    The common pattern identifying tenant-specific URLs is defined with TENANT\_HOST\_PATTERN: ^\(.\*\)-<YOUR\_CUSTOM\_DOMAIN\>

    For more information, see [Using Custom Domains.](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/2291aea5e22440f7a161bdeb9c16b664.html)


The application router derives the tenant from the URL and calls the tenant-aware XSUAA, which is responsible for the authentication of the business user. The UAA reads the tenant and gets the customer-specific identity provider \(IdP\) from the tenant-specific identity zone. Then, the XSUAA delegates the authentication to the configured IdP, and creates a JSON Web Token \(JWT\) that contains the tenant, the current user, and the authorization scopes of the user. The JWT is then sent back to the application router, and from there to the application.

To read and store tenant-specific data, the multitenant application needs to know the tenant ID. Using the Container Security API, the multitenant application is enabled to read the tenant, user, and scopes from the given JWT. The API also validates whether the JWT is valid. The tenant information is contained in the `identityZone` user attribute.

For more information, see:

[Web Access in the Cloud Foundry Environment](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/70a62d12cf91493cb9d1ec3c04d19ff9.html)

[What Is Authorization and Trust Management](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/649961f8d4ad463daca33b3a20deba4c.html)

