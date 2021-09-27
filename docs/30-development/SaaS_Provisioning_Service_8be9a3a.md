<!-- loio8be9a3a51232402082480914e020b2d3 -->

# SaaS Provisioning Service

The SaaS Provisioning Service needs the parameters as described in the chapter [Register the Multitenant Application to the SaaS Provisioning Service](Register_the_Multitenant_Application_to_the_SaaS_Provisioning_Service_2cd8913.md).

```
  - name: saas-registry
    type: org.cloudfoundry.managed-service
    parameters:
      service: saas-registry
      service-plan: application 
      service-name: ${appname}-saas-registry
      config:
        xsappname: ${appname}
        appName: ${appname}
        appUrls:
          getDependencies: https://cis${route-prefix}.${app-domain}/callback/v1.0/dependencies
          onSubscription: https://cis${route-prefix}.${app-domain}/callback/v1.0/tenants/{tenantId}

```

The parameter `appname` is referenced to

-   reference the xsappname of the xsuaa \(`xsappname: ${appname}`\)
-   create a unique service instance name \(`service-name: ${appname}-saas-registry`\).

The parameters `route-prefix` and `app-domain` are referenced to

-   define the `getDependencies` url: \(`https://cis${route-prefix}.${app-domain}/callback/v1.0/dependencies`\).
-   define the `onSubscription` url: \(`https://cis${route-prefix}.${app-domain}/ callback/v1.0/tenants/{tenantId}`\).

