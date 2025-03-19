<!-- loio480a5a7a77054100a37b3ed483b39bd4 -->

# Deploying Content

Learn how to deploy, redeploy, and undeploy content from the HTML5 Application Repository.

In the Cloud Foundry environment, the Generic Application Content Deployer \(GACD\) is the preferred module for the application deployment. GACD deployment enables asynchronous uploads, making it more suitable for handling large content. This method helps mitigate the risk of network-related timeouts due to long response times. Additionally, with GACD, you do not need to deploy a Cloud Foundry application within your space. See [Deploy Content Using the Generic Application Content Deployer](deploy-content-using-the-generic-application-content-deployer-07c6796.md).

In the Kyma environment, you use the HTML5 Application Deployer. See [Deploy Content Using HTML5 Application Deployer](deploy-content-using-html5-application-deployer-9b178ab.md).

The following applies to deployment with both modules:

> ### Note:  
> The HTML5 Application Repository service does not provide the technical capabilities to support the collection, processing, and storage of personal data. The file names used for deploying the HTML5 applications are not intended for personal data.

You use a service instance of the app-host service plan to deploy your applications to the HTML5 Application Repository.

> ### Note:  
> If you delete an app-host service instance, the apps that are deployed with this app-host service instance are deleted from the HTML5 Application Repository.

> ### Restriction:  
> Delta deployments are not supported.
> 
> If you deploy new application content using an existing app-host service instance, the new application content will completely replace the old application content that had been previously deployed with this service instance in the HTML5 Application Repository.
> 
> For example, if you have already deployed the applications a, b, and c with the instance 123 and now want to deploy the new applications d and e, you can do one of the following to avoid overwriting the applications a, b, and c:
> 
> -   Redeploy instance 123 with applications a, b, c, d, and e \(with the new and the old applications\).
> 
> -   Create a new instance 456 and use this instance to deploy the applications d and e.

**Related Information**  


[Deploy Content Using the Generic Application Content Deployer](deploy-content-using-the-generic-application-content-deployer-07c6796.md "Deploy content from the HTML5 Application Repository using the Generic Application Content Deployer (GACD).")

[Deploy Content Using HTML5 Application Deployer](deploy-content-using-html5-application-deployer-9b178ab.md "Use the HTML5 application deployer module to deploy the content of the HTML5 applications to the HTML5 Application Repository.")

[Redeploy Content](redeploy-content-9ed190c.md "You can redeploy changed content to the existing app-host service instance.")

[Undeploy Content](undeploy-content-fab96a6.md "To undeploy content you need to delete the content from the repository and delete the app-host service plan instance.")

