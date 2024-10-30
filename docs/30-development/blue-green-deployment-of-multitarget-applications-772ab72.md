<!-- loio772ab72204f04946b79ce2d962e64970 -->

# Blue-Green Deployment of Multitarget Applications

Use the blue-green deployment technique by running two identical production environments, allowing seamless updates without downtime for Cloud Foundry Multitarget applications.

> ### Restriction:  
> Blue-green deployment is supported only for Cloud Foundry applications. It is not supported for bound services, such as service instances and their configuration, workflow content, and HTML5 repository content, among others. Live and idle applications are bound to the same service instances.

By using the blue-green deployment technique, you can update the system without downtime and with reduced risk. During the process, you can perform tests and validation of the new application version using productive data. A classical blue-green deployment of stateless applications, which are modeled as an MTA, is supported.

In the context of Multitarget applications, you have the following options for using blue-green deployment:

-   [Legacy Blue-Green Deployment](legacy-blue-green-deployment-764308c.md) - where the production environments are called “blue” and “green”
-   [Blue-Green Deployment Strategy](blue-green-deployment-strategy-7c83810.md) - where the production environments are called “live” and “idle”
-   [](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/2e4dfeded960446da4aa1c0b734fc81b.html "") :arrow_upper_right: - an alternative to the standard blue-green deployment strategy, where the "idle" application is incrementally scaled up to the desired instance count while the "live" application instances are gradually stopped

**Related Information**  


[Using Blue-Green Deployment To Reduce Downtime](https://docs.cloudfoundry.org/devguide/deploy-apps/blue-green.html)

