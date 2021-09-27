<!-- loio2cd8913a50bc4d3e8172f84bb4bfba20 -->

# Register the Multitenant Application to the SaaS Provisioning Service

To make a multitenant application available for subscription to SaaS consumer tenants, you \(the application provider\) must register the application in the Cloud Foundry environment via the `SaaS Provisioning` service \(`saas-registry`\).

The `SaaS Provisioning` service allows application providers to register multitenant applications and services in the Cloud Foundry environment in SAP Business Technology Platform. This activity is a one-time procedure per multitenant application.

1.  Create a service instance of the SaaS Provisioning service with a configuration JSON file in the Cloud Foundry space where the ABAP Solution instance is created.

    The configuration JSON file must follow the following format and set these properties:

    ```
    "xsappname" : "<xsappname>",
       "appUrls": {
          "getDependencies" : "<getDependenciesUrl>", 
          "onSubscription" : "<onSubscriptionUrl>/{tenantId}"
       },
       "displayName" : "<displayName>",
       "description" : "<description>",
       "category" : "<category>"
    }
    
    ```

    <a name="loio2cd8913a50bc4d3e8172f84bb4bfba20__table_kyy_5gw_qmb"/>Specify the following parameters:


    <table>
    <tr>
    <th>

    Parameters


    
    </th>
    <th>

    Description


    
    </th>
    </tr>
    <tr>
    <td>

    xsappname


    
    </td>
    <td>

    The xsappname configured in the security descriptor file used to create the XSUAA instance.


    
    </td>
    </tr>
    <tr>
    <td>

    getDependencies


    
    </td>
    <td>

    **\(Optional\)**Any URL that the application exposes for GET dependencies. If the application does not have dependencies and the callback is not implemented, it should not be declared. **Note:**The JSON response of the callback must be encoded as either UTF8, UTF16, or UTF32, otherwise an error is returned. **Important:** You can either provide your own getDependencies Callback or use the default implementation of the AppRouter \(recommended if no special logic is needed\). **But:** If an own implementation is provided you have to make sure that the ABAP Solution instance is returned as a dependency.

    The path is: /callback/v1.0/dependencies


    
    </td>
    </tr>
    <tr>
    <td>

    onSubscription


    
    </td>
    <td>

    Any URL that the application exposes via PUT and DELETE subscription. It must end with /\{tenantId\}. The tenant for the subscription is passed to this callback as a path parameter. You must keep \{tenantId\} as a parameter in the URL so that it is replaced at real time with the tenant calling the subscription. This callback URL is called when a subscription between a multitenant application and a consumer tenant is created \(PUT\) and when the subscription is removed \(DELETE\).**Important:**You can either provide your own onSubscription Callback or use the default implementation of the approuter \(recommended if no special logic is needed\).

    The path is: /callback/v1.0/tenants/\{tenantId\}


    
    </td>
    </tr>
    <tr>
    <td>

    displayName


    
    </td>
    <td>

    **\(Optional\)**The display name of the application when viewed in the cockpit. For example, in the application's tile. If left empty, takes the application's technical name.


    
    </td>
    </tr>
    <tr>
    <td>

    description


    
    </td>
    <td>

    **\(Optional\)** The description of the application when viewed in the cockpit. For example, in the application's tile. If left empty, takes the application's display name.


    
    </td>
    </tr>
    <tr>
    <td>

    category


    
    </td>
    <td>

    **\(Optional\)**The category to which the application is grouped in the Subscriptions page in the cockpit. If left empty, gets assigned to the default category.


    
    </td>
    </tr>
    </table>
    
    **Important:** When using default approuter implementation: Register a url that matches your TENANT\_HOST\_PATTERN.

    In this example:

    -   **dev**: TENANT\_HOST\_PATTERN: ^\(.\*\)-abap-saas-app.cfapps.eu10.hana.ondemand.com

    -   **o prod**: TENANT\_HOST\_PATTERN: ^\(.\*\).mydomain.com

    Use https://cis-abap-saas-app.cfapps.eu10.hana.ondemand.com \(dev\) or https://cis.mydomain.com \(prod\), this will result in having the approuter generate the right subscription url. **Important:**Use your own domain prefix for dev as it must be unique on the landscape \(not just abap-saas-app\).

    > ### Sample Code:  
    > Configuration JSON file \(example: config.json\):
    > 
    > ```
    > {
    >    "xsappname":"abap-saas-app",
    >    "appUrls":{
    >       "getDependencies":"https://cis-abap-saas-app.cfapps.eu10.hana.ondemand.com/callback/v1.0/dependencies",
    >       "onSubscription":"https://cis-abap-saas-app.cfapps.eu10.hana.ondemand.com/callback/v1.0/tenants/{tenantId}"
    >    },
    >    "displayName":"My ABAP SaaS Solution",
    >    "description":"A SaaS Solution based on the SAP BTP ABAP Environment"
    > }
    > 
    > ```

2.  Execute the following cf CLI command to create the service instance with the JSON configuration file:

    ```
    cf create-service saas-registry application <SAAS_REGISTRY_SERVICE_INSTANCE> -c <JSON_CONFIG_FILE>
    ```

    <a name="loio2cd8913a50bc4d3e8172f84bb4bfba20__table_ql5_v3w_qmb"/>Specify the following parameters:


    <table>
    <tr>
    <th>

    Parameters


    
    </th>
    <th>

    Description


    
    </th>
    </tr>
    <tr>
    <td>

    SAAS\_REGISTRY\_SERVICE\_INSTANCE


    
    </td>
    <td>

    The new name for your service instance. Use only alphanumeric characters, hyphens, and underscores.


    
    </td>
    </tr>
    <tr>
    <td>

    JSON\_CONFIG\_FILE


    
    </td>
    <td>

    The file name of the service-specific configuration parameters, in a valid JSON object \(described above\).


    
    </td>
    </tr>
    </table>
    
    `cf create-service saas-registry application saas-registry-application -c config.json`

    > ### Note:  
    > You can create the SaaS Provisioning service instance directly in the cockpit.

    For general instructions, see [Binding Service Instances to Applications](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/e98280a71f17413088f8a10838a1e4cc.html).

3.  To ensure that the environment variables in the application take effect, execute the following cf CLI command:

    ```
    cf restage <APP_NAME>
    ```

    <a name="loio2cd8913a50bc4d3e8172f84bb4bfba20__table_pcj_jjw_qmb"/>Specify the following parameters


    <table>
    <tr>
    <th>

    Parameters


    
    </th>
    <th>

    Description


    
    </th>
    </tr>
    <tr>
    <td>

    APP\_NAME


    
    </td>
    <td>

    The ID of your deployed multitenant application.


    
    </td>
    </tr>
    </table>
    
    > ### Sample Code:  
    > ```
    > cf restage saas-app
    > ```


