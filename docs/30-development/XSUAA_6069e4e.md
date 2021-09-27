<!-- loio6069e4efa8bc456997c9a25abdb69a43 -->

# XSUAA

The xsuaa instance needs the parameters as defined in the chapter [Create an XSUAA Instance](Create_an_XSUAA_Instance_2ce1a96.md). This results in the following MTA resource:

```
resources:
  - name: xsuaa
    type: com.sap.xs.uaa
    parameters:
      service-plan: application
      service-name: ${appname}-xsuaa
      config:
        xsappname: ${appname}
        tenant-mode: shared
        scopes:
          - name: $XSAPPNAME.Callback
            description: With this scope set, the callbacks for tenant onboarding, offboarding and getDependencies can be called.
            grant-as-authority-to-apps:
              - $XSAPPNAME(application,sap-provisioning,tenant-onboarding)
        foreign-scope-references:
          - uaa.user
        role-collections:
          - name: ${appname}-admin
            role-template-references:
              - $XSSERVICENAME(${appname}-abap-solution).SolutionAdmin

```

The parameter `appname` is referenced to

-   use it as xsappname of the xsuaa
-   reference the name of the ABAP Solution instance`((${appname}-abap-solution` in section `role-template-references`\)
-   create a unique service instance name \(`service-name: ${appname}-xsuaa`\).

