<!-- loiod3e23196166b443db17b3545c912dfc0 -->

# Content Deployment

Direct content deployment provides a mechanism for deploying content to services without the need for an application-specific deployer.



> ### Note:  
> Content deployment is supported only for schema version 3.1 and higher.

The mechanism utilizes the Generic Application Content Deployment protocol \(GACD\). It allows you to deploy modules of type `com.sap.application.content`, which require a dependency to a service or an existing service key, where the required dependency parameter `content-target` is set to `true`. When a module is processed during deployment of a multitarget application, the SAP Cloud Deployment service delivers the module content to the service or key, marked as `content-target`.



<a name="loiod3e23196166b443db17b3545c912dfc0__section_yqh_wvb_snb"/>

## Supported service offerings

Cloud Foundry service offerings that currently support GACD are:

-   `html5-apps-repo`
-   `portal`
-   `workflow`
-   `destination`



<a name="loiod3e23196166b443db17b3545c912dfc0__section_wqx_wvb_snb"/>

## Supported features

The different content service offerings handle individually the lifecycle of their content, and employ different GACD deployment features:

-   [Delivering file content](Content_Deployment_d3e2319.md#loiod3e23196166b443db17b3545c912dfc0__deliver_file_content)
-   [Defining content inline](Content_Deployment_d3e2319.md#loiod3e23196166b443db17b3545c912dfc0__define_content_inline)
-    [Providing additional configurations](Content_Deployment_d3e2319.md#loiod3e23196166b443db17b3545c912dfc0__Provide_add_config)
-   [Customizing service keys](Content_Deployment_d3e2319.md#loiod3e23196166b443db17b3545c912dfc0__custom_serv_keys)
-   [Modeling service dependencies](Content_Deployment_d3e2319.md#loiod3e23196166b443db17b3545c912dfc0__model_serv_dependencies)
-   [Using existing service keys](Content_Deployment_d3e2319.md#loiod3e23196166b443db17b3545c912dfc0__use_existing_serv_keys)



### Delivering file content

You can use a file or directory that is treated as content. The file or directory is part of the MTA, and its path is defined in the `MANIFEST.MF` file.

The following codeblock contains the mtad.yaml data:

> ### Sample Code:  
> ```
> _schema-version: '3.1'
> ID: com.sap.example.content.deployment
> version: 0.0.1
> modules:
>  - name: content-module
>    type: com.sap.application.content
>    requires:
>     - name: workflow_service
>       parameters:
>          content-target: true
> resources:
>  - name: workflow_service
>    type: org.cloudfoundry.managed-service
>    parameters:
>       service-plan: standard
>       service: workflow
> ```

The following codeblock contains the accompanying `MANIFEST.MF` file:

> ### Sample Code:  
> ```
> 
> ...
> 
> Name: content-module/data
> MTA-Module: content-module
> Content-Type: application/zip
> 
> ...
> ```

In the example above, the `managed-service` creates a `workflow_service` with plan `standard`, and then uses it to deploy the content from a module type `content-module`.



### Defining content inline

You can enter content definitions inline in the MTA descriptor as part of module parameter `content`:

> ### Sample Code:  
> ```
> modules:
> - name: destination-content
>   type: com.sap.application.content
>   requires:
>   - name: destination-service
>     parameters:
>       content-target: true
>   - name: foo-api
>   - name: bar-api
>   parameters:
>     content:
>       subaccount:
>         destinations:
>         - Name: foo-api
>           URL: ~{foo-api/url}
>           forwardAuthToken: true
>         - Name: bar-api
>           URL: ~{bar-api/url}
>           forwardAuthToken: true
>   <...>
>   resources:
> - name: destination-service
>   type: org.cloudfoundry.managed-service
>   parameters:
>     service: destination
>     service-name: destination-service
>     service-plan: lite
> 
> 
> ```



### Providing additional configurations

You can provide a content deployment configuration as part of module parameter `config`:

> ### Sample Code:  
> ```
> _schema-version: '3.1'
> ID: com.sap.example.content.deployment
> version: 0.0.1
> modules:
>  - name: content-module
>    type: com.sap.application.content
>    requires:
>     - name: workflow_service
>       parameters:
>          content-target: true
>    parameters:
>       config:
>            <...>
> resources:
>  - name: workflow_service
>    type: org.cloudfoundry.managed-service
>    parameters:
>       service-plan: standard
>       service: workflow
> ```



### Customizing service keys

You can customize the service keys created as part of the content deployment by using the required dependency parameter `service-key`.

> ### Sample Code:  
> ```
> _schema-version: '3.1'
> ID: com.sap.example.content.deployment
> version: 0.0.1
> modules:
> - name: content-module
>    type: com.sap.application.content
>    requires:
>     - name: workflow_service
>       parameters:
>          content-target: true
>         ** service-key:
>            name: workflow\_service-key
>            config:
>              <map entries for creation parameters\>
> **
>     - name: xsuaa_service
>       parameters:
>          **service-key:
>            name: xsuaa\_service-key
>            config:
>              <map entries for creation parameters\>
> **
>  
> resources:
> - name: workflow_service
>    type: org.cloudfoundry.managed-service
>    parameters:
>       service-plan: standard
>       service: workflow
> - name: xsuaa_service
>    type: org.cloudfoundry.managed-service
>    parameters:
>       service-plan: application
>       service: xsuaa
> 
> 
> ```



### Modeling service dependencies

In some cases the content that is deployed might require multiple services where the `content-target` service requires credentials of other services. In order to model such a dependency you need a descriptor similar to the following:

> ### Sample Code:  
> ```
> _schema-version: '3.1'
> ID: com.sap.example.content.deployment
> version: 0.0.1
> modules:
>  - name: content-module
>    type: com.sap.application.content
>    requires:
>     - name: xsuaa_service
>     - name: html5_service
>       parameters:
>          content-target: true
> resources:
>  - name: html5_service
>    type: org.cloudfoundry.managed-service
>    parameters:
>       service-plan: app-host
>       service: html5-apps-repo
>  - name: xsuaa_service
>    type: com.sap.xs.uaa
> ```

In the example above, `html5_service` would gain access credentials to `xsuaa_service`.



### Using existing service keys

You can deploy content directly to an existing service key with a descriptor modeled appropriately:

> ### Sample Code:  
> ```
> _schema-version: '3.1'
> ID: com.sap.example.content.deployment
> version: 0.0.1
> modules:
>  - name: content-module
>    type: com.sap.application.content
>    requires:
>     - name: workflow_service_key
>       parameters:
>          content-target: true
> resources:
>  - name: workflow_service_key #this service key needs to exist beforehand
>    type: org.cloudfoundry.existing-service-key
>    parameters:
>       service-name: workflow_service #this service must be created and exist beforehand
> ```

> ### Note:  
> When there are services listed in the `requires` section, a service key is created and linked for each service during the deployment process.

**Related Information**  


[Deploy Content Using Generic Application Content Deployer](Deploy_Content_Using_Generic_Application_Content_Deployer_07c6796.md "Deploy content from the HTML5 Application Repository using the Generic Application Content Deployer (GACD).")

[Create Destinations Using the MTA Descriptor](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/8aeea65eb9d64267b554f64a3db8a349.html "Use the multitarget-application (MTA) descriptor to manage destinations for complex deployments.") :arrow_upper_right:

