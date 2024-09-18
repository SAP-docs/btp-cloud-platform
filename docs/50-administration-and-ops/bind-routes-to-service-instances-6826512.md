<!-- loio68265122869b4ab881cdd309b47a20ba -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Bind Routes to Service Instances

You can bind a route to a service instance in the SAP BTP cockpit.



<a name="loio68265122869b4ab881cdd309b47a20ba__prereq_k3r_zcb_kcc"/>

## Prerequisites

In SAP BTP, Cloud Foundry environment, only user-provided and fully-brokered services are currently supported.

-   You must have the Space Developer or the Space Supporter role.

-   The service instance and the route are in the same Cloud Foundry space.

-   To bind a route to a user-provided service instance, the service instance must include the URL of the route service. To include it, set the `route_service_url` property.

-   To bind a route to a managed service instance, make sure this service can be bound by setting route forwarding in the `requires` property:

    `requires=[route_forwarding]`




## Context

Before you proceed with the route binding, keep in mind the following:

-   You can have a route bound to an application and a service instance at the same time.

-   You can bind one or multiple routes to a single service instance.


Now that you're aware of these specifics, let's continue with the route binding steps.



## Procedure

1.  Navigate to the *Routes* page in your Cloud Foundry space in the cockpit.

2.  Choose <span class="SAP-icons-V5"></span> \(Bind Route Service\) from the *Actions* column.

3.  Select a service instance from the dropdown.

    The dropdown contains a list of all service instances that you can bind to the route. If an existing service instance can't be bound to a route, you won't see it in the dropdown.

    If you want to create a new service instance from your services available in the Service Marketplace, see [Creating Service Instances in Cloud Foundry](https://help.sap.com/docs/service-manager/sap-service-manager/creating-service-instances-in-cloud-foundry).

    To create a new user-provided service instance, see [Creating User-Provided Service Instances in Cloud Foundry Environment](https://help.sap.com/docs/service-manager/sap-service-manager/creating-user-provided-service-instances-in-cloud-foundry-environment).

4.  \(Optional\) If you want to customize the route binding service, mark the *Specify Parameters* checkbox.

    You have the option to either upload your own JSON file or you can directly enter JSON parameters and their values in the field below.

    For more information about what parameters you can use, see [https://v3-apidocs.cloudfoundry.org/version/3.138.0/index.html\#service-route-binding](https://v3-apidocs.cloudfoundry.org/version/3.138.0/index.html#service-route-binding).

5.  Choose *Bind*.


**Related Information**  


[About Routes in the Cockpit](about-routes-in-the-cockpit-4af288c.md "To enable your end users to reach your application, create a route and map it to the application in the SAP BTP cockpit.")

