<!-- loiofa5af4ecdf90496b8eec54fe0e22150c -->

# ABAP Development



As a developer user, implement your custom business services with the ABAP RESTful application programming model. See [ABAP RESTful Appliation Programming Model](https://help.sap.com/docs/btp/sap-abap-restful-application-programming-model/abap-restful-application-programming-model?version=Cloud). Maintain business catalogs \(see [Identity and Access Management \(IAM\)](identity-and-access-management-iam-5b62901.md)\) and communication scenarios \(see [Communication Management](https://help.sap.com/docs/abap-cloud/abap-integration-connectivity/communication-management)\) to expose services to business users and communication users. See [SAP Business Technology Platform](https://help.sap.com/docs/btp/sap-business-technology-platform/sap-business-technology-platform?version=Cloud), [ABAP Environment Learning Journey](https://learning.sap.com/products/business-technology-platform/development/abap?url_id=text-gl-lh), and [ABAP Environment Community](https://community.sap.com/topics/cloud-platform-abap-environment). Also consider starting out with a free tier option for the ABAP environment to get hands-on development experience. See [Trial Accounts and Free Tier](https://help.sap.com/docs/btp/sap-business-technology-platform/trial-accounts-and-free-tier?version=Cloud).



### Identity and Access Management

SAP Fiori applications and business services are represented by IAM apps and can be used to define the necessary authorizations. In an IAM business catalog, you bundle multiple IAM apps and their predefined authorizations, for example, for a specific business area.

Additionally, you can define business role templates to make it easier for administrators to find the relevant business catalogs to create business roles. See [Identity and Access Management \(IAM\)](identity-and-access-management-iam-5b62901.md).



### Communication Management

> ### Note:  
> Use customer-managed communication scenarios as a design time description to store technical information, such as inbound and outbound services and their service type, for example OData or SOAP by using the `create_by_comm_arrangement` method.
> 
> Instead of coding against destination names, using communication scenarios allows consumers of the SaaS solution to create communication arrangements based on provided communication scenarios. Therefore, you don't have to create specific destinations in the consumer subaccount.

> ### Restriction:  
> The ABAP environment only supports one communication configuration layer intended to be used by the consumer. It’s currently not possible to enforce a communication configuration exclusively managed by the service provider within the consumer tenant.

Services with the following protocols supported for **inbound communication** can be included as part of customer-managed communication scenarios:

-   HTTP
-   SOAP
-   RFC Internet/Cloud Connector

> ### Restriction:  
> RFC is currently not supported for inbound communication in consumer tenants.

For **outbound communication**, the following protocols are supported:

-   HTTP \(Internet\)
-   HTTP \(Cloud Connector\)
-   SOAP \(Internet\)
-   SOAP \(Cloud Connector\)
-   RFC \(Internet\)
-   RFC \(Cloud Connector\)

See [Developing External Service Consumption](https://help.sap.com/docs/btp/sap-business-technology-platform/developing-external-service-consumption-outbound-communication?version=Cloud).



### **Business Configuration**

Business configuration plays a major role in SaaS solutions. It refers to a predefined set of configuration options that affect its functionality and behavior. See [Business Configuration in SAP BTP ABAP Environment \(1\): Overview and BC Maintenance Apps](https://blogs.sap.com/2021/09/22/business-configuration-in-sap-btp-abap-environment-1-overview-and-bc-maintenance-apps/).

To maintain these configuration options, you have to create dedicated apps using the ABAP RESTful Application Programming Model. See [Create a Business Configuration App for Factory Calendar Using the ABAP RESTful Application Programming Model](https://developers.sap.com/mission.abap-dev-factory-calendar.html).

Using the business configurations API, you can register business configurations. These business configurations are then displayed in the list of all maintainable business configurations in the SAP Fiori App Maintain Business Configurations, if the user has the necessary authorizations for the service of the business configuration. See [Business Configuration Maintenance Object Cloud Platform API](business-configuration-maintenance-object-cloud-platform-api-508d406.md).



<a name="loiofa5af4ecdf90496b8eec54fe0e22150c__section_fpw_yvx_ffc"/>

## Providing Released APIs

APIs can be released for stable custom development based on different release contracts. Refer to [Released APIs](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide/released-apis).



### Developer Extensibility Enablement

Developer extensibility can be provided for APIs by defining the corresponding API state for system-internal use \(contract C1\) and use in ABAP for Cloud Development. This allows the APIs to be used across ABAP for Cloud Development software components and objects. Refer to [Releasing Development Objects](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide/setting-api-release-state).



### Key User Extensibility Enablement

Using SaaS solutions, you can provide key user extensibility for system-internal use \(contract C1\) and use in key user apps. This allows customers who use the solution to extend it to their specific requirements.

As a developer user, you have to implement key user extensibility in the development system in the Partner Development tenant \(client 100\) using ABAP Development Tools.

See [Providing Business Add-Ins](providing-business-add-ins-6747acb.md) for guidance on how to prepare business add-ins \(BAdIs\) so that customers can add their own business logic in the solution by using the *Custom Logic* app.

See [Configuring Predefined Custom Fields](../50-administration-and-ops/configuring-predefined-custom-fields-0033cbc.md) for guidance on how to equip your SaaS solution with support for customer-specific extension fields.



### Stability of Released APIs

Released APIs, such as BAdIs or predefined custom fields, must only be changed compatibly. Otherwise, for example, runtime errors might occur or an upgrade might fail. To ensure that released APIs are not changed incompatibly, run an ATC compatibility check. This check uses snapshots that are created using the*Manage API Snapshots* app and which are set to check-relevant, to check whether incompatible changes have been made to the released API. For more information, see [Manage API Snapshots](../50-administration-and-ops/manage-api-snapshots-8dda6b6.md).



<a name="loiofa5af4ecdf90496b8eec54fe0e22150c__section_gzv_yvx_ffc"/>

## Using Released API

You can use the object-level API state to release APIs for use in cloud development, without targeting a specific software component. With software component relations on the other hand, you can also provide access permissions, without stability requirements. In any case, such dependencies between software component should always be declared – especially in the case of add-on components. See [Software Component Relations](https://help.sap.com/docs/btp/sap-business-technology-platform-internal/software-component-dependencies?version=Cloud#software-component-relations).



<a name="loiofa5af4ecdf90496b8eec54fe0e22150c__section_kzr_hxx_ffc"/>

## Multitenancy

With the ABAP environment, you can build multitenancy-enabled SaaS solutions. To do so, the add-on implementation has to follow certain guidelines. See [Multitenancy Development Guideline](multitenancy-development-guideline-9d994c8.md).

> ### Recommendation:  
> If the add-on implementation is aligned with the development guideline for multitenancy, we recommend configuring your solution by setting `tenant_mode = multi` so that the same ABAP service instance is used for multiple consumers.

> ### Tip:  
> For in-depth information about multitenancy, check out [Multitenancy](multitenancy-c873073.md).

