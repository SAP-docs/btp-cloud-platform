<!-- loio2ce1a962c3be48dd8035513b0a2d7397 -->

# Create an XSUAA Instance



1.  Create a security descriptor file in JSON format that specifies the functional authorization scopes for the application:
    1.  Define the application provider tenant as a shared tenant:

        ```json
        "tenant-mode":"shared"
        ```

    2.  Provide access to the `SaaS Provisioning` service \(`saas-registry`\) for calling callbacks and getting the dependencies API by granting scopes:

        ```json
        "grant-as-authority-to-apps" : [ "$XSAPPNAME(application,sap-provisioning,tenant-onboarding)"]
        ```

    3.  Define a role collection which provides authorization for the initial user onboarding in the new ABAP tenant after a subscription was done. It must reference the “SolutionAdmin” role template of the ABAP solution service instance \(in this example the service instance is named “`solution-provider`“\):

        ```
        "role-collections": [
                {
                    "name": "abap-saas-app-admin",
                    "role-template-references": [
                        "$XSSERVICENAME(abap-solution).SolutionAdmin"
                    ]
                }
            ]
        
        ```

    4.  Define a foreign scope reference to ensure a token exchange will be possible and the ABAP systems can be called:

        ```json
        "foreign-scope-references": ["uaa.user"],
        ```

        Security descriptor file in JSON format:

        ```json
        {
            "xsappname": "abap-saas-app",
            "tenant-mode": "shared",
            "scopes": [
                {
                    "name": "$XSAPPNAME.Callback",
                    "description": "With this scope set, the callbacks for subscribe, unsubscribe and getDependencies can be called.",
                    "grant-as-authority-to-apps": [
                        "$XSAPPNAME(application,sap-provisioning,tenant-onboarding)"
                    ]
                }
            ],
            "foreign-scope-references": ["uaa.user"],
            "role-collections": [
                {
                    "name": "abap-saas-app-admin",
                    "role-template-references": [
                        "$XSSERVICENAME(solution-provider).SolutionAdmin"
                    ]
                }
            ]
        }
        ```

        For more information, see [Quick Start: Create Role Collections \(with Predefined Roles\)](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/fe750543788a40b79a49854590ad0b11.html).


2.  Create an xsuaa service instance:

    In the Cloud Foundry space in the provider's subaccount where your application is going to be deployed \(see [Deploy the Multitenant Application to the Provider Subaccount](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/2204416a491f4068ba36066ca1aa9ca0.html)\), create an xsuaa service instance with the security configurations, which you defined in the security descriptor file in the previous step, by executing this command in the Cloud Foundry command line interface \(cf CLI\):

    ```json
    cf create-service xsuaa application <XSUAA_INSTANCE_NAME> -c <XS_SECURITY_JSON>
    ```

    Specify the following parameters:


    <table>
    <tr>
    <th valign="top">

    Parameter


    
    </th>
    <th valign="top">

    Description


    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
        XSUAA\_INSTANCE\_NAME


    
    </td>
    <td valign="top">
    
        The new name for the xsuaa service instance. Use only alphanumeric characters, hyphens, and underscores.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        <XS\_SECURITY\_JSON\>


    
    </td>
    <td valign="top">
    
        The name of the security descriptor file from the previous step.


    
    </td>
    </tr>
    </table>
    
    ```json
    cf create-service xsuaa application xsuaa-application -c xs-security.json
    ```

    > ### Note:  
    > You can also create the service instance directly in the cockpit.

    For general instructions, see [Create Spaces Using the Cloud Foundry Command Line Interface](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/a2e5e29eca0b40da8d3a25e806329377.html).


