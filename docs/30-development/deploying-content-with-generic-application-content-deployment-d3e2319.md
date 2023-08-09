<!-- loiod3e23196166b443db17b3545c912dfc0 -->

# Deploying Content with Generic Application Content Deployment

This approach provides a mechanism for direct content deployment from SAP Cloud Deployment service to the content backend without the need for an intermediate Cloud Foundry application.



> ### Note:  
> This approach is supported only for MTA schema version 3.1 and higher.

> ### Note:  
> This approach is recommended for its light-weight nature, minimal footprint in your Cloud Foundry account and avoided overhead of transient content applications.

> ### Note:  
> The examples below are partial and they intend to show the different capabilities of content deployment. For specific application content, see the dedicated documentation linked below.

The mechanism utilizes the Generic Application Content Deployment protocol \(GACD\). It allows you to deploy content represented by an MTA module oftype `com.sap.application.content` to a certain listof supported services.



<a name="loiod3e23196166b443db17b3545c912dfc0__section_yqh_wvb_snb"/>

## Supported service offerings

Cloud Foundry service offerings that currently support GACD are:

-   `html5-apps-repo` \(For more information, see [Deploy Content Using Generic Application Content Deployer](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/07c679672e5f423e9dc631fc85b51da3.html?version=Cloud)\)
-   `portal` \(For more information, see [Add an SAP Fiori Launchpad Module](https://help.sap.com/docs/Portal_Service/ad4b9f0b14b0458cad9bd27bf435637d/b55594e28a7d47a2ab4bf1f03ebfd56b.html)\)
-   `workflow` \(For more information, see [Create a Workflow Module](https://help.sap.com/docs/WORKFLOW/e157c391253b4ecd93647bf232d18a83/b2df7c220b2245dcad11be747794c042.html?version=Cloud&locale=en-US)\)
-   `destination` \(For more information, see [Create Destinations Using the MTA Descriptor](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/8aeea65eb9d64267b554f64a3db8a349.html?version=Cloud)\)
-   `business logging` \(For more information, see [Using GACD](https://help.sap.com/docs/SAP_CP_BUS_REUSE_SERVICE_BL/9d9c6578dd284b7491e2b6ceb1395329/f4a898bd0f9b4619940dd049c5328ee4.html?locale=en-US)\)



<a name="loiod3e23196166b443db17b3545c912dfc0__section_p22_ckc_wxb"/>

## How Content is Deployed with Generic Application Content Deployment

The diagram below illustrates the steps and BTP components involved in the process of content deployment with Generic Application Content Deployment:

![](images/DeployingContentWithGenericApplicationContentDeploymentService_1616934.png)

The following steps describe the process of content deployment with Generic Application Content Deployment:

1.  A developer/operator runs MTA deployment – the flow demonstrates only modules of type `com.sap.application.content` indicating content \(for example - a single MTA module and multiple required services, only one of them is marked with parameter `content-target: true`\).

2.  SAP Cloud Deployment service prepares for the next steps. This step includes:

    1.  SAP Cloud Deployment service gets the existing services and service keys which are related to previous MTA deployment. The list comprises of a content service instance, a content service key and eventually additional services keys.
    2.  Based on the name, SAP Cloud Deployment service decides which of the existing service keys will be deleted, which will be kept, and whether new ones will be created. In the end, only one of them will be used as a content target.

3.  SAP Cloud Deployment service creates or reuses a service instance or instances that are relevant for the content deployment, not only the one that serves as a content target.

4.  SAP Cloud Deployment service creates or reuses a service key. This step might include the creation of several service keys needed for successful content deployment, not only the one that serves as a content target.

5.  SAP Cloud Deployment service fetches the credentials of the required service key\(s\). In this step content endpoint is detected from content target service key. The credentials of all remaining service keys serve as configurations for the next step.

6.  SAP Cloud Deployment service executes the content deployment to content endpoint and passes previously collected data as content configurations.

7.  SAP Cloud Deployment service deletes the discontinued service keys calculated in step 2. Normally these are service keys that are not part of the current MTA and were used in the previous deployment.

8.  MTA deployment completes and SAP Cloud Deployment service reports the status to the developer/operator.




<a name="loiod3e23196166b443db17b3545c912dfc0__section_tdh_wnc_wxb"/>

## Content Target

When an MTA module of type `com.sap.application.content` is present in your MTA, SAP Cloud Deployment service processes it and delivers its module content to the content target.

The content target is explicitly set with a flag in the MTA and it is unknown to the SAP Cloud Deployment service without it.

There should be only one content target defined per MTA module of type `com.sap.application.content`. This guarantees that the content will be deployed to only one place.

The content target is defined when a content module requires a service or service key, and in that required dependency the parameter `content-target` is set to `true`. In case of a missing or duplicated `content-target` parameter in more than one required dependency, the deployment will not proceed.

Normally, content modules require MTA resources that represent Cloud Foundry service instances or service keys. When multiple service instances or keys are required, they are used by default for content deployment configuration. For more information see the [Configuration from other service instances/keys](deploying-content-with-generic-application-content-deployment-d3e2319.md#loiod3e23196166b443db17b3545c912dfc0__ConfigOtherServiceKeys) section.



<a name="loiod3e23196166b443db17b3545c912dfc0__section_d1h_j2h_wxb"/>

## MTA Modelling



### Deliver file content

You can use a file or directory that is treated as content. The file or directory is part of the MTA archive, and its path is defined in the `MANIFEST.MF` file.

The following code block contains a snippet from an MTA deployment descriptor \(mtad.yaml\):

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
> 
> ```

The following code block contains the accompanying `MANIFEST.MF` file:

> ### Sample Code:  
> ```
> Name: content-module/data 
> MTA-Module: content-module 
> Content-Type: application/zip 
> 
> ```



### Delivery text / Inline content

You can enter content definitions inline in the MTA descriptor as part of module parameter `content`. In the example below the template for new destinations \(`foo-api` and `bar-api`\) will be deployed to `destination-service:`

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
>     service-plan: lite
> 
> ```



<a name="loiod3e23196166b443db17b3545c912dfc0__section_wc5_2gh_wxb"/>

## Service Keys in Content Deployment

When an MTA module of type `com.sap.application.content` requires an MTA resource, the SAP Cloud Deployment service will create or re-use a service key.

Service keys in content deployment are an alternative of service bindings between applications and services. When there is an intermediate content application, it might be bound to different services that provide specific capabilities. In direct content deployment, the required service keys have the same role. For example, a content module might require an xsuaa service instance, which might be used for secure communication at a later stage.

By default, service keys to all required services are created with the name that follows the template `<module_name>-<resource_name>-credentials`. For example, the result of the sample below will be a service instance with name `workflow_service` which will have a service key named `content-module-workflow_service-credentials`:

> ### Sample Code:  
> ```
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
> 
> ```

By default, the existing service keys are re-used in future deployments. This is done to save time from their re-creation and avoid potential issues if they are used outside of the MTA and their credentials are invalidated.



### Customizing service keys

You can customize the service keys created as part of the content deployment by using the required dependency parameter `service-key`. This way, you can define the service key name or pass service key creation parameters:

> ### Sample Code:  
> ```
> modules: 
> - name: content-module 
>    type: com.sap.application.content 
>    requires: 
>     - name: workflow_service 
>       parameters: 
>          content-target: true 
>          service-key: 
>            name: workflow_service-key 
>            config: 
>              <map entries for creation parameters> 
> 
> ```



### Re-create custom service keys for deployment

This option extends the customization of service keys explained above. Based on its name, an existing service key may be re-used or deleted, as described in [How Content is Deployed with Generic Application Content Deployment](deploying-content-with-generic-application-content-deployment-d3e2319.md#loiod3e23196166b443db17b3545c912dfc0__section_p22_ckc_wxb).

The option is particularly useful if you want to rotate and renew the credentials used for content deployment, like when they are based on user/password credentials or certificates.

You can set the service keys to automatically rotate for each new deployment by using the existing deployment parameter `${timestamp}` as a part of the name of the defined custom service key. Doing so ensures that the key will have a new name for each deployment, resulting in Deploy Service creating and using a new key for the related content deployment. The previously used service key will be deleted after the new one is in place.

> ### Sample Code:  
> ```
> modules: 
> - name: content-module 
>    type: com.sap.application.content 
>    requires: 
>     - name: workflow_service 
>       parameters: 
>          content-target: true 
>          service-key: 
>            name: workflow_service-key-${timestamp}
> 
> ```



### Using existing service keys

You can deploy content directly to an existing service key with a descriptor modeled appropriately. This option might be useful if you want to manage the lifecycle of the service key outside of the MTA:

> ### Sample Code:  
> ```
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
> 
> ```



### Using user-provided services

Sometimes, the content endpoint might not be exposed as a standard service broker in the BTP. In these cases, neither service instance nor service key can be created. The only option to utilize content deployment to such content target is via user-provided services.

> ### Sample Code:  
> ```
> modules: 
>  - name: content-module 
>    type: com.sap.application.content 
>    requires: 
>     - name: content-endpoint 
>       parameters: 
>          content-target: true 
> resources: 
>  - name: content-endpoint 
>    type: org.cloudfoundry.user-provided-service 
>    parameters: 
>       content_endpoint: https://my-content-endpoint.com
> 
> ```



<a name="loiod3e23196166b443db17b3545c912dfc0__section_rj3_m4h_wxb"/>

## Content Deployment Configuration

Sometimes content deployment needs a configuration, which might be environment or context specific and cannot part directly in the content itself.

There are two supported ways to pass additional configuration for content deployment:

-   Content Deployment Configuration from other service instances/keys

-   Inline Content Deployment Configuration




### Configuration from other service instances/keys

By default, all required MTA resources from content modules are processed and used for content deployment configuration. This includes the MTA resources of types `org.cloudfoundry.managed-service`, `org.cloudfoundry.existing-service`, `org.cloudfoundry.existing-service-key` and `org.cloudfoundry.user-provided-service`. A service key is used for each of those resources, except for `org.cloudfoundry.user-provided-service`.

In the example below, the content-module requires two services and only one of them is marked as content-target. The other required service is xsuaa, which will be used for content configuration, and it will guarantee more secure communication during end-to-end flow:

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
> 
> ```

When multiple service instances or keys are required, they are all used for content deployment configuration by default.



### Inline Content Deployment Configuration

You can provide content deployment configuration as part of the module parameter `config`:

> ### Sample Code:  
> ```
> modules: 
>  - name: content-module 
>    type: com.sap.application.content 
>    requires: 
>     - name: workflow_service 
>       parameters: 
>          content-target: true 
>    parameters: 
>       config: # the content deployment configuration 
>          env: dev 
> resources: 
>  - name: workflow_service 
>    type: org.cloudfoundry.managed-service 
>    parameters: 
>       service-plan: standard 
>       service: workflow
> 
> ```

**Related Information**  


[Deploy Content Using the Generic Application Content Deployer](deploy-content-using-the-generic-application-content-deployer-07c6796.md "Deploy content from the HTML5 Application Repository using the Generic Application Content Deployer (GACD).")

[Create Destinations Using the MTA Descriptor](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/8aeea65eb9d64267b554f64a3db8a349.html "Use the multitarget-application (MTA) descriptor to manage destinations for complex deployments.") :arrow_upper_right:

