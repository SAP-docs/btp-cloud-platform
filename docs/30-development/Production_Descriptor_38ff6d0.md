<!-- loio38ff6d04b3a64cc380da9c7329d9926a -->

# Production Descriptor

In our case, the following MTA extension descriptor would be suitable for a production deployment, as it uses a custom domain as `app-domain` and provides no `route-prefix`. Furthermore, it defines an additional wildcard route for tenant access \(`"*.${app-domain}"`\).

```
--- 
ID: abap-saas-reference-solution-prod
_schema-version: "3.1"
extends: abap-saas-reference-solution

parameters: 
  addon-product-name: /NAMESPC/PRODUCTX
  appname: abap-saas-reference-solution
  provider-admin-email: administrator@example.com
  saas-description: "ABAP based SaaS solution with an ABAP tenant per subscription"
  saas-display-name: "SaaS Solution (Multitenancy)"
  tenant-mode: multi
  route-prefix: ""
  app-domain: mydomain.com

modules:
  - name: approuter
    parameters:
      routes:
        - route: "cis${route-prefix}.${app-domain}"
        - route: "*${route-prefix}.${app-domain}"
```

