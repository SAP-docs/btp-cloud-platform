<!-- loio767fb000a9fb4b269b02840bfba37fbe -->

# Development Descriptor

In our case, the following MTA extension descriptor would be suitable for a development deployment, as it uses the `${default-domain}` as `app-domain` and provides a `route-prefix`, which will avoid collisions due to the default domain. Additionally, we set the property `XS_APP_LOG_LEVEL` on the approuter module to `debug` to ensure that we have more detailed logging.

```
--- 
ID: abap-saas-reference-solution-dev
_schema-version: "3.1"
extends: abap-saas-reference-solution

parameters: 
  addon-product-name:  /NAMESPC/PRODUCTX
  appname: abap-saas-reference-solution-dev
  provider-admin-email: administrator@example.com
  saas-description: "ABAP based SaaS solution with an ABAP tenant per subscription"
  saas-display-name: "SaaS Solution (Multitenancy)"
  tenant-mode: multi

modules: 
  - name: approuter
    properties: 
      XS_APP_LOG_LEVEL: debug

```

