<!-- loioaf521ff55a3e4fd99733ae877446093d -->

# Definition of MTA Modules

Next, the modules must be defined. In our case, that's only the “approuter”. Keep in mind that all values under “properties” will be available as environment variables to the application once deployed. Furthermore, it is assumed that the source code to the approuter is in the folder “router” next to the “mta.yaml” as defined by the “path” property. See [Configure the Approuter Application](configure-the-approuter-application-3725815.md) to see which source code is needed there.

```
modules:
  - name: approuter
    type: javascript.nodejs
    path: router
    parameters:
      keep-existing-routes: true
      routes:
        - route: cis${route-prefix}.${app-domain}
      app-name: ${appname}
      memory: 1024MB
    properties:
      TENANT_HOST_PATTERN: (.*)${route-prefix}.${app-domain}
      XS_APP_LOG_LEVEL: error
      SAP_JWT_TRUST_ACL:
        - clientid: "*"
          identityzone: sap-provisioning

```

The “requires” section defines dependencies to the MTA resources we will define now. Each entry here will result in a service binding to the CF application “approuter” once deployed.

```
requires:
      - name: xsuaa
      - name: saas-registry
      - name: abap-solution

```

