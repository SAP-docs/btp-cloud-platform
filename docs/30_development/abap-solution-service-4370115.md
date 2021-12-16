<!-- loio4370115a59a248cd876f0721303eaaab -->

# ABAP Solution Service

The ABAP Solution Service needs the parameters as described in the chapter [Define Your ABAP Solution](define-your-abap-solution-1697387.md).

```
  - name: abap-solution
    type: org.cloudfoundry.managed-service
    parameters: 
      service: abap-solution
      service-plan: standard
      service-name: ${appname}-abap-solution
      config:
        name: ${appname}
        sap_system_name: H01
        addon_product_name:  /NAMESPC/PRODUCTX
        consumer_tenant_limit: 10	
        size_of_runtime: 1
        size_of_persistence: 4
        tenant_mode: multi
        consumer_id_pattern: ([^-]*).*
        provider_admin_email: provider-admin@example.org
        usage: prod
        xs-security:
          xsappname: ${appname}

```

The parameter `appname` is referenced to

-   define the name of the solution \(`name: ${appname}`\)
-   to create a unique service instance name \(`service-name: ${appname}-abap-solution`\)
-   to reference the xsappname of the xsuaa \(`xsappname: ${appname}) in section (xs-security`\).

