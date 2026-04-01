<!-- loio4e35eb027f284b7fa6219bc70561fb4e -->

# Deploy

In order to offer a multitenant application based on an ABAP add-on product, a multi-target application \(MTA\) is developed and deployed to the Cloud Foundry environment on SAP BTP. The MTA integrates the different services required for this scenario, such as the ABAP Solution service, responsible for provisioning ABAP systems, tenants, and users on demand. For more in-depth information, see [Multitenant Applications](multitenant-applications-195031f.md).

Once you’ve configured your multitenant application, you can deploy it once for testing purposes in the global account for development. After testing the subscription process during this development phase, the multitenant application can be deployed to the global account for production. See [System Landscape/Account Model](https://help.sap.com/docs/btp/sap-business-technology-platform/concepts#system-landscape%252Faccount-model).

After the multitenant application has been deployed for production purposes, the SaaS solution is ready for commercialization.

You have two options for implementing and deploying the application. The recommended approach is to use the Maintain Solution app in the Landscape Portal. See [Maintain Solution](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/d2a73509305c4ea7971ee24e68509dd8.html).

Alternatively, you can create your own multitenant application. This allows you to modify parameters that are not exposed in the Maintain Solution app; however, the app should cover all common use cases. See Developing Multitenant Applications in the Abap Environment.





### gCTS Delivery

If you use gCTS instead of add-ons for delivering software components to production systems, you have to configure the multitenant application manually. In the configuration of the ABAP solution service the value for the add-on product name must be left empty. This is currently not supported by the Maintain Solution app. See [Delivery via Add-On or gCTS](https://help.sap.com/docs/btp/sap-business-technology-platform/delivery-via-add-on-or-gcts?version=Cloud).

Prerequisites

• To configure the sizing of a SaaS solution, you have to determine the expected load per region by using the Technical Monitoring Cockpit. See [Technical Monitoring Cockpit \(Cloud Version\)](https://help.sap.com/docs/btp/technical-monitoring-cockpit-cloud-version/technical-monitoring-cockpit-cloud-version).

• To implement and deploy a multitenant application for a SaaS solution, you have to assign the necessary entitlements in the provider subaccount, for example for the ABAP Solution service. See [Multitenant Applications](multitenant-applications-195031f.md) and [Entitlements and Quotas](https://help.sap.com/docs/btp/sap-business-technology-platform/entitlements-and-quotas?version=Cloud&q=entitlements%20and%20quotas).

