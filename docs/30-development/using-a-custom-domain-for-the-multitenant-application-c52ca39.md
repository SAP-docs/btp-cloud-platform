<!-- loioc52ca397062a4f9e9cff449babe82122 -->

# Using a Custom Domain for the Multitenant Application

The SAP Custom Domain Service \(see [SAP Custom Domain service](https://discovery-center.cloud.sap/serviceCatalog/custom-domain?region=all&service_plan=custom-domain&commercialModel=cpea)\) lets you configure your own custom domain \(see [What Is Custom Domain?](https://help.sap.com/docs/custom-domain/custom-domain-manager/what-is-custom-domain?version=Cloud)\) to publicly expose your application instead of using an SAP-provided default/shared/standard domain like cfapps.eu10.hana.ondemand.com for your application URLs.

By using this service, subaccount owners can make their SAP BTP applications accessible via a custom domain that is different from the default one; for example, myshop.com.

In case of multitenant applications \(see [Multitenant Applications](multitenant-applications-195031f.md)\), using a custom domain comes with another advantage: For each subscription there needs to be a CF route \(see [Routes](https://docs.cloudfoundry.org/devguide/deploy-apps/routes-domains.html#routes)\) that is mapped to the approuter module of the multitenant application, so that the application is accessible via a URL.

While using a default domain, a new route like `<SUBSCRIBER_TENANT_SUBDOMAIN>-<APPROUTER_APPLICATION_HOST>.<SAP-PROVIDED_STANDARD_DOMAIN>` must be created manually for each new tenant.

By configuring the multitenant application with a custom domain, a route with a wildcard hostname like `*.<YOUR_CUSTOM_DOMAIN>` can be mapped, so that there is no need to create a new route for each new tenant manually. For more information, refer to [Approuter Application](approuter-application-44dbd0a.md).

It is recommended to use a custom domain for your multitenant application only during the production phase; during the development phase using a default domain is sufficient.

Please follow the steps outlined in [Configuring Custom Domains](https://help.sap.com/docs/custom-domain/custom-domain-manager/configuring-custom-domains?version=Cloud) or[Get Started with the Custom Domain Manager](https://developers.sap.com/tutorials/btp-custom-domain-manager-getting-started.html) \(refer to PaaS-User\) to register your custom domain in the provider subaccount’s CF org \(see [Multitenancy in the ABAP Environment](multitenancy-in-the-abap-environment-633cc61.md)\). After registering the custom domain successfully, the domain becomes available as private domain \(see [Private domains](https://docs.cloudfoundry.org/devguide/deploy-apps/routes-domains.html#private-domains)\) for route creation in any space of the provider subaccount’s CF org.

To create a multitenant application for use with a custom domain, following configurations are adjusted accordingly:

-   `TENANT_HOST_PATTERN` configuration of the approuter application: String containing a regular expression with a capturing group. The request host is matched against this regular expression. The value of the first capturing group is used as tenant id. Please refer to [TENANT\_HOST\_PATTERN](https://help.sap.com/docs/btp/sap-business-technology-platform/environment-variables?state=DRAFT#loioba527058dc4d423a9e0a69ecc67f4593__section_zhq_xch_wx).

-   SaaS Registry Callback URLs getDependencies and onSubscription. Please refer to [Saas Provisioning Service](saas-provisioning-service-cbc379e.md).

-   XSUAA OAuth 2.0 Client configuration redirect-uris. Please refer to [Listing Allowed Redirect URIs](https://help.sap.com/docs/btp/sap-business-technology-platform/security-considerations-for-sap-authorization-and-trust-management-service?version=Cloud#loio88b7d9d4c6ff4498b48dbc0b7be8a294) 

-   [CF routes](https://docs.cloudfoundry.org/devguide/deploy-apps/routes-domains.html#routes) assigned to approuter application


For the subscriptions to the multitenant application to work correctly, configured SaaS Registry callback URLs need to be reachable \(cis… route\). For Application Routing routing to work, the approuter needs to be able to resolve the application URL based on current `TENANT_HOST_PATTERN` configuration.

You can use the[Maintain Solution](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/d2a73509305c4ea7971ee24e68509dd8.html) app in the Landscape Portal to easily create such a multitenant application with custom domain, please refer to [Create Deployment Configuration](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/146b71650f254d57b403ec982eea82ff.html) → **Step 3: Routing Information**.

Or, if you are following the MTA-based approach to create your multitenant application, in the [MTA Extension descriptor for production phase](https://github.com/sap-software/abap-saas-reference-solution/blob/main/extensions/examples/prod.mtaext) these configurations are changed using following MTA parameters:

-   app-domain: the registered custom domain, e.g. mydomain.com

-   route-prefix: needs to be empty because application URLs are mapped using following structure:`*.<YOUR_CUSTOM_DOMAIN>` \(dot separator\) and therefore do not include a route prefix


A route with wildcard hostname for tenant access is added to the approuter module, on top of the route used for SaaS Registry callback URLs:

> ### Sample Code:  
> ```
> 
> modules: 
> 
>   - name: approuter 
>     parameters: 
>       routes: 
>         - route: "cis${route-prefix}.${app-domain}" 
>         - route: "*${route-prefix}.${app-domain}" 
> ```

To reduce risks use[Blue-Green Deployment of Multitarget Applications](https://help.sap.com/docs/btp/sap-business-technology-platform/blue-green-deployment-strategy) while deploying multitenant application MTA during production phase.

After MTA build and deployment, the approuter application is created with a route cis.mydomain.com that is used for the SaaS Registry callback URLs `getDependencies` and `onSubscription`. On top of that a route with wild card hostname `*.mydomain.com` is mapped to the approuter. In this format, since the wildcard is replaced by an actual tenant during runtime, there is no need to create a new route for each new tenant manually.

If you change the domain type of your multitenant application from shared to custom domain, you need to update the application URL of existing subscriptions. Please use the option to update the application URL of an active subscription in the [Subscription Management Dashboard](https://help.sap.com/docs/btp/sap-business-technology-platform/using-subscription-management-dashboard?version=Cloud). In such case, make sure to inform application consumers beforehand about temporary downtimes that might occur during this change.

