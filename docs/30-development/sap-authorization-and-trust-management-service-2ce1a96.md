<!-- loio2ce1a962c3be48dd8035513b0a2d7397 -->

# SAP Authorization and Trust Management Service



> ### Sample Code:  
> ```
> 
>   - name: xsuaa
>     type: com.sap.xs.uaa
>     requires:
>       - name: abap-solution
>     parameters:
>       service-plan: application
>       service-name: xsuaa
>       config:
>         oauth2-configuration:
>           redirect-uris:
>             - "https://*.${app-domain}/**"
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
>               - $XSSERVICENAME(${appname}-abap-solution).SolutionAdmin
> 
> ```

The `xsuaa` service instance, acts as an OAuth 2.0 client to the multitenant application, and to the `ABAP Solution` service instance. It provides access to the SaaS Provisioning service for calling callbacks and getting the dependencies API by granting corresponding scopes.

A role collection is defined as part of the xsuaa configuration which provides authorization for the initial user onboarding in the new ABAP tenant after a subscription was done.

For this purpose, the “SolutionAdmin” role is referenced. See [Quick Start: Create Role Collections \(with Predefined Roles\).](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/fe750543788a40b79a49854590ad0b11.html)

Finally, a foreign scope reference is defined to ensure a token exchange will be possible and the ABAP systems can be called.

