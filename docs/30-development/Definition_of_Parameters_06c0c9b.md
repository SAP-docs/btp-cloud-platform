<!-- loio06c0c9b8036046ef963621aafc44af98 -->

# Definition of Parameters

Next, we define some parameters at the beginning of the MTA. Three of them are freely defined and have no special semantics to the MTA deployer. They can be referenced in the subsequent sections of the MTA using the syntax`${parameter-name}`. For more details on parameters, see [Parameters and Properties](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/490c8f71e2b74bc0a59302cada66117c.html).

-   **Freely-defined parameters:**
    -   app-domain: The domain that should be used for the approuter and therefore the SaaS application. In our example, this is the $\{default-domain\} \(equals to the cfapps-domain of the current landscapes\) for a development deployment; for production it should be the custom domain \(so here: `mydomain.com`\).
    -   appname: The value that should be used as xsappname and solution name \(here: `abap-saas-reference-solution`\).
    -   route-prefix: The value that should be used as a prefix in the route of the approuter, allowing it to deploy the same MTA to the same landscape muliple times using the default landscape domain.
-   **Parameter with semantics to MTA deployer:**
    -   enable-parallel-deployments: If set to true, deploys multiple modules at the same time.

```
parameters:
  app-domain:
  appname: abap-saas-reference-solution
  route-prefix:
  enable-parallel-deployments: true

```

**Related Information**  


[Definition of Parameters](Definition_of_Parameters_06c0c9b.md)

[Definition of MTA Modules](Definition_of_MTA_Modules_af521ff.md)

[Definition of the MTA Resources](Definition_of_the_MTA_Resources_1764436.md)

[Using MTA Extension Descriptors](Using_MTA_Extension_Descriptors_383f3a3.md)

[Build and Deploy](Build_and_Deploy_faf5106.md)

