<!-- loio3725815e3be747cd96626dc14e5605f5 -->

# Configure the Approuter Application

You deploy the enhanced approuter application as a Cloud Foundry application and as a logical part of the multitenant application. Then you configure the approuter application as an external access point of the application. You need to deploy a separate application router for each multitenant application.



<a name="loio3725815e3be747cd96626dc14e5605f5__section_pl2_ffw_qmb"/>

## How does the application router and multitenancy work?

When a consumer accesses the application, their consumer tenant calls the multitenant application via the application router with their tenant-specific URL \(cf route\).



### Development Phase

During a development phase of your multitenant application, the following URL structure applies:

`<SUBSCRIBER_TENANT_SUBDOMAIN>-<APPROUTER_APPLICATION_HOST>.<SAP-PROVIDED_STANDARD_DOMAIN>`

In each development landscape, SAP provides a different standard domain you can use to create URLs.

Using that domain, and following the specified URL structure, a created URL would be:

 `tenant1-myapprouter.cfapps.sap.hana.ondemand.com` 

Here `tenant1-myapprouter` is the hostname, and `cfapps.sap.hana.ondemand.com` is the SAP-provided standard domain for this development landscape. In this format, create a new URL for each new tenant.

> ### Note:  
> When deploying the ASP approuter as MTA, **cf deploy** will overwrite all routes: If you have already created consumers in the development phase, have created a route for them, and then deploy changes on the approuter, these routes will be deleted because they are not defined in the mta.yaml. This can be resolved by adding the parameter "keep-existing-routes:true” to the approuter module.



### Production Phase

During a production phase of your multitenant application, apply for a custom domain via the custom domain service, then create a URL using the following structure:

 `*.<YOUR_CUSTOM_DOMAIN>` 

where \* is the wildcard hostname.

In this format, since the wildcard is replaced by an actual tenant during runtime, there is no need to create a new URL for each new tenant.

For more information, see [Using Custom Domains](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/2291aea5e22440f7a161bdeb9c16b664.html).

In both cases, the application router then derives the tenant from the URL and calls the tenant-aware XSUAA \(containing the user account and authentication service\), which is responsible for the authentication of the business user. The UAA reads the tenant and gets the customer-specific identity provider \(IdP\) from the tenant-specific identity zone. Then, the XSUAA delegates the authentication to the configured IdP, and creates a JSON Web Token \(JWT\) that contains the tenant, the current user, and the authorization scopes of the user. The JWT is then sent back to the application router, and from there to the application.

To read and store tenant-specific data, the multitenant application needs to know the tenant ID. To read the tenant ID, use the Container Security API to enable the multitenant application to read the tenant, user, and scopes from the given JWT. The API also validates whether the JWT is valid. The tenant information is contained in the `identityZone` user attribute.

For more information, see:

• [Web Access in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/70a62d12cf91493cb9d1ec3c04d19ff9.html)

• [What Is Authorization and Trust Management](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/649961f8d4ad463daca33b3a20deba4c.html)

• [Authentication for Applications](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/09f5bd3f346b4ee08b5ca084128e2e81.html)

For more information on the deployment of the approuter as standalone CF application, see [Deploy Business Applications in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/4946ea5421374924963ce8575a5f3d05.html).

For more information on the recommended approach with an MTA, see [MTA-Based Approach \(Recommended\)](MTA-Based_Approach_(Recommended)_ca0cc10.md).

