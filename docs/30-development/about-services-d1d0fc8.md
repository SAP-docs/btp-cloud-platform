<!-- loiod1d0fc8e78474494a59caad02259ec7e -->

# About Services

In the Cloud Foundry environment, you usually enable services by creating a service instance using either the SAP BTP cockpit or the Cloud Foundry command line interface \(cf CLI\), and binding that instance to your application.

In a PaaS environment, all external dependencies, such as databases, messaging systems, files systems, and so on, are services. In the Cloud Foundry environment, services are offered in a marketplace, from which users can create service instances on-demand. A service instances is a single instantiation of a service running on SAP BTP. Service instances are created using a specific service plan. A service plan is a configuration variant of a service. For example, a database may be configured with various "t-shirt sizes", each of which is a different service plan.

To integrate services with applications, the service credentials must be delivered to the application. To do so, you can bind service instances to your application to automatically deliver these credentials to your application. Or you can use service keys to generate credentials to communicate directly with a service instance. As shown in the figure below, you can deploy an application first and then bind it to a service instance:

  
  
**Using Services in the Cloud Foundry Environment**

![](images/Using_Services_CF_93c24e7.png "Using Services in the Cloud
                                Foundry
				Environment")

Alternatively, you can also bind the service instance to your application as part of the application push via the application manifest. For more information, see [https://docs.cloudfoundry.org/devguide/deploy-apps/manifest.html\#services-block](https://docs.cloudfoundry.org/devguide/deploy-apps/manifest.html#services-block).

> ### Note:  
> Have in mind that you need to create a service instance first before you integrate it into your application manifest.

The Cloud Foundry environment also allows you to work with user-provided service instances. User-provided service instances enable developers to use services that are not available in the marketplace with their applications running in the Cloud Foundry environment. Once created, user-provided service instances behave in the same manner as service instances created through the marketplace. For more information, see [Creating User-Provided Service Instances](creating-user-provided-service-instances-a44355e.md).

For more conceptual information about using services in the Cloud Foundry environment, see [https://docs.cloudfoundry.org/devguide/services/](https://docs.cloudfoundry.org/devguide/services/).

**Related Information**  


[Creating Service Instances](creating-service-instances-8221b74.md "Use the SAP BTP cockpit or the Cloud Foundry Command Line Interface to create service instances:")

[Binding Service Instances to Applications](binding-service-instances-to-applications-e98280a.md "Use the SAP BTP cockpit or the Cloud Foundry Command Line Interface to bind service instances to applications:")

[Creating Service Keys](creating-service-keys-4514a14.md "You can use service keys to generate credentials to communicate directly with a service instance. Once you configure them for your service, local clients, apps in other spaces, or entities outside your deployment can access your service with these keys.")

[Creating User-Provided Service Instances](creating-user-provided-service-instances-a44355e.md "User-provided service instances enable you to use services that are not available in the marketplace with your applications running in the Cloud Foundry environment.")

[Solutions and Services](../10-concepts/solutions-and-services-7613d9c.md#loio7613d9ce711e1014839a8273b0e91070 "Consume the solutions and services by SAP BTP according to your preferred development environment and use cases.")

