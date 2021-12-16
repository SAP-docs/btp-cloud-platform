<!-- loioea445c6c808544ef90e4b03ed614087b -->

# Full MTA Descriptor

> ### Note:  
> Dependening on whether you are using delivery via software components \(gCTS\) \(see [Software Components](software-components-58480f4.md)\) instead of the add-on delivery process \(see [Build and Publish Add-on Products on SAP BTP ABAP Environment](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentAddons/)\), you need to remove the configuration parameter addon\_product\_name from the ‘abap-solution’ resource.

> ### Sample Code:  
> ```
> _schema-version: "3.1"
> ID: abap-saas-reference-solution
> version: 1.0.0
> 
> parameters:
>   app-domain: ${default-domain}
>   route-prefix: -${appname}
>   appname: 
>   addon-product-name:
>   provider-admin-email: 
>   saas-display-name: 
>   saas-description: 
>   tenant-mode: 
>   enable-parallel-deployments: true
> 
> modules:
>   - name: approuter
>     type: javascript.nodejs
>     path: router
>     parameters:
>       keep-existing-routes: true
>       routes:
>         - route: cis${route-prefix}.${app-domain}
>       app-name: ${appname}
>       memory: 1024MB
>     properties:
>       TENANT_HOST_PATTERN: (.*)${route-prefix}.${app-domain}
>       XS_APP_LOG_LEVEL: error
>       SAP_JWT_TRUST_ACL:
>         - clientid: "*"
>           identityzone: sap-provisioning
>     requires:
>       - name: xsuaa
>       - name: saas-registry
>       - name: abap-solution
>       - name: application-log
> 
> resources:
>   - name: xsuaa
>     type: com.sap.xs.uaa
>     requires:
>       - name: abap-solution
>     parameters:
>       service-plan: application
>       service-name: xsuaa
>       config:
>         xsappname: ${appname}
>         tenant-mode: shared
>         scopes:
>           - name: $XSAPPNAME.Callback
>             description: With this scope set, the callbacks for tenant onboarding, offboarding and getDependencies can be called.
>             grant-as-authority-to-apps:
>               - $XSAPPNAME(application,sap-provisioning,tenant-onboarding)
>         foreign-scope-references:
>           - uaa.user
>         role-collections:
>           - name: ${appname}-admin
>             role-template-references:
>               - $XSSERVICENAME(abap-solution).SolutionAdmin
> 
>   - name: saas-registry
>     type: org.cloudfoundry.managed-service
>     parameters:
>       service: saas-registry
>       service-plan: application 
>       service-name: saas-registry
>       config:
>         xsappname: ${appname}
>         appName: ${appname}
>         appUrls:
>           getDependencies: https://cis${route-prefix}.${app-domain}/callback/v1.0/dependencies
>           onSubscription: https://cis${route-prefix}.${app-domain}/callback/v1.0/tenants/{tenantId}
>         displayName: ${saas-display-name}
>         description: ${saas-description}
> 
>   - name: abap-solution
>     type: org.cloudfoundry.managed-service
>     parameters: 
>       service: abap-solution
>       service-plan: standard
>       service-name: abap-solution
>       config:
>         name: ${appname}
>         addon_product_name: ${addon-product-name}
>         size_of_runtime: 1
>         size_of_persistence: 4
>         tenant_mode: ${tenant-mode}
>         consumer_id_pattern: ([^-]*).*
>         provider_admin_email: ${provider-admin-email}
>         usage: prod
>         xs-security:
>           xsappname: ${appname}
>   - name: application-log
>     type: org.cloudfoundry.managed-service
>     parameters:
>       service: application-logs
>       service-plan: lite
>       service-name: application-log
> 
> ```

