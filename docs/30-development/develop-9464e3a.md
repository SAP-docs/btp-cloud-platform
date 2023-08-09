<!-- loio9464e3af139d4e0581cb4e819886b0c8 -->

# Develop



Both the initial implementation and any further development of the add-on are performed in the development system of the development subaccount.

You can use various SAP technologies at this point, such as the ABAP RESTful application programming model \(RAP\) for modeling and implementing business objects and the browser-based IDE SAP Business Application Studio for developing SAP Fiori UIs. Depending on the business use case, some additional development effort may be necessary to implement suitable launchpad content, Identity & Access Management artifacts, or communication management artifacts.

Once you’ve completed these development activities, the solution is ready to be tested in a suitable test system.



<a name="loio9464e3af139d4e0581cb4e819886b0c8__section_s1q_ds4_drb"/>

## Prerequisites

-   For ABAP development, you need a developer user using ABAP Development Tools. See [Getting Started as a Developer in the ABAP Environment](../20-getting-started/getting-started-as-a-developer-in-the-abap-environment-4b896c9.md).
-   For UI development, you need a developer user using SAP Business Application Studio. See [Develop an SAP Fiori Application UI and Deploy it to ABAP Using SAP Business Application Studio](develop-an-sap-fiori-application-ui-and-deploy-it-to-abap-using-sap-business-application-eaaeba4.md).
-   For custom code migration, you need a business user that is assigned the business role based on business role template `SAP_BR_IT_PROJECT_MANAGER`, and a communication arrangement instance for `SAP_COM_0464`. See [Custom Code Migration](../50-administration-and-ops/custom-code-migration-651ef65.md).

<a name="loiofa5af4ecdf90496b8eec54fe0e22150c"/>

<!-- loiofa5af4ecdf90496b8eec54fe0e22150c -->

## ABAP Development

As a developer user, implement your custom business services with the ABAP RESTful application programming model. See [ABAP RESTful Application Programming Model](https://help.sap.com/viewer/923180ddb98240829d935862025004d6/Cloud/en-US/289477a81eec4d4e84c0302fb6835035.html). Maintain business catalogs \(see [Identity and Access Management \(IAM\)](identity-and-access-management-iam-5b62901.md)\) and communication scenarios \(see [Communication Management](communication-management-5b8ff39.md#loio5b8ff39ddb6741a29ddfcf587939e8f4)\) to expose services to business users and communication users. See [SAP Business Technology Platform](../sap-business-technology-platform-6a2c1ab.md), [ABAP Environment Learning Journey](https://help.sap.com/doc/221f8f84afef43d29ad37ef2af0c4adf/HP_2.0/en-US/49047e7668844d419ccee567923a475e.html), and [ABAP Environment Community](https://community.sap.com/topics/cloud-platform-abap-environment). Also consider starting out with a free tier option for the ABAP environment to get hands-on development experience. See [Trial Accounts and Free Tier](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/046f127f2a614438b616ccfc575fdb16.html?version=Cloud).

**Identity and Access Management**

SAP Fiori applications and business services are represented by IAM apps and can be used to define the necessary authorizations. In an IAM business catalog, you bundle multiple IAM apps and their predefined authorizations, for example, for a specific business area.

Additionally, you can define business role templates to make it easier for administrators to find the relevant business catalogs to create business roles. See [Identity and Access Management \(IAM\)](identity-and-access-management-iam-5b62901.md).

**Communication Management**

> ### Note:  
> Use customer-managed communication scenarios as a design time description to store technical information, such as inbound and outbound services and their service type, for example OData or SOAP by using the `create_by_comm_arrangement` method. See [Service Consumption via Communication Arrangements](service-consumption-via-communication-arrangements-86aece6.md).
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

See [Supported Protocols and Authentication Methods](supported-protocols-and-authentication-methods-437e9d4.md).

**Business Configuration**

Business configuration plays a major role in SaaS solutions. It refers to a predefined set of configuration options that affect its functionality and behavior. See [Business Configuration in SAP BTP ABAP Environment \(1\): Overview and BC Maintenance Apps](https://blogs.sap.com/2021/09/22/business-configuration-in-sap-btp-abap-environment-1-overview-and-bc-maintenance-apps/).

To maintain these configuration options, you have to create dedicated apps using the ABAP RESTful Application Programming Model. See [Create a Business Configuration App for Factory Calendar Using the ABAP RESTful Application Programming Model](https://developers.sap.com/mission.abap-dev-factory-calendar.html).

Using the business configurations API, you can register business configurations. These business configurations are then displayed in the list of all maintainable business configurations in the SAP Fiori App Maintain Business Configurations, if the user has the necessary authorizations for the service of the business configuration. See [Business Configuration Maintenance Object Cloud Platform API](business-configuration-maintenance-object-cloud-platform-api-508d406.md).



**Key User Extensibility Enablement**

Using SaaS solutions, you can provide key user extensibility for system-internal use \(contract C1\) and use in key user apps. This allows customers who use the solution to extend it to their specific requirements.

As a developer user, you have to implement key user extensibility in the development system in the Partner Development tenant \(client 100\) using ABAP Development Tools.

See [Providing Business Add-Ins](providing-business-add-ins-6747acb.md) for guidance on how to prepare business add-ins \(BAdIs\) so that customers can add their own business logic in the solution by using the *Custom Logic* app.

See [Configuring Predefined Custom Fields](../50-administration-and-ops/configuring-predefined-custom-fields-0033cbc.md) for guidance on how to equip your SaaS solution with support for customer-specific extension fields.

> ### Note:  
> Released APIs, such as BAdIs or predefined custom fields, must only be changed compatibly. Otherwise, for example, runtime errors might occur or an upgrade might fail.
> 
> Using API snapshots to store the state of a released object locally can provide incompatibility warnings in ABAP Development Tools where the current state of the released object is compared to the last API snapshot.
> 
> The provider is responsible for preparing the solution to be lifecycle-stable for consumption by customers. Thus, as a developer user, you need to take these warnings into consideration before activating new changes in released objects.



**Multitenancy**

With the ABAP environment, you can build multitenancy-enabled SaaS solutions. To do so, the add-on implementation has to follow certain guidelines. See [Multitenancy Development Guideline](multitenancy-development-guideline-9d994c8.md).

> ### Recommendation:  
> If the add-on implementation is aligned with the development guideline for multitenancy, we recommend configuring your solution by setting `tenant_mode = multi` so that the same ABAP service instance is used for multiple consumers.

> ### Tip:  
> For in-depth information about multitenancy, check out [Multitenancy](concepts-9482e7e.md#loioc8730736a52645b49ca76c08214bf181).

<a name="loiof3be8246edc74be59c10779443f67793"/>

<!-- loiof3be8246edc74be59c10779443f67793 -->

## UI Development

SAP Fiori applications are developed in SAP Business Application Studio on top of business services in the ABAP development system and then deployed to the ABAP development system to be part of the same software component as backend artifacts.

As a developer user, once business services are implemented as UI services, you can create SAP Fiori elements apps using SAP Business Application Studio. See [Develop an SAP Fiori Application UI and Deploy it to ABAP Using SAP Business Application Studio](develop-an-sap-fiori-application-ui-and-deploy-it-to-abap-using-sap-business-application-eaaeba4.md).

> ### Note:  
> Launchpad spaces and pages offer more flexibility to influence the launchpad layout for specific user groups. As of now, there is no possibility to create templates for a specific spaces/pages setup and to deliver this as part of an add-on. Therefore, for every consumer, this needs to be configured manually.
> 
> To simplify this process, we recommend structuring the IAM business catalogs that include IAM apps for the UI according to business roles by using business role templates. See [Providing Access to the SAP Fiori Application](providing-access-to-the-sap-fiori-application-b569abb.md).

<a name="loiof438645cb5664399a6b21f8d9bd3d004"/>

<!-- loiof438645cb5664399a6b21f8d9bd3d004 -->

## \(Optional\) Code Migration from On-Premise

Optionally, you can migrate existing custom ABAP code for add-on development purposes. This custom code migration process analyzes your existing code for cloud-readiness. See [How to Check your Custom ABAP Code for SAP BTP ABAP Environment](https://blogs.sap.com/2018/10/02/how-to-check-your-custom-abap-code-for-sap-cloud-platform-abap-environment/) and [Custom Code Migration](../50-administration-and-ops/custom-code-migration-651ef65.md).

After adapting the code and making necessary changes, you can migrate the code via abapGit. See [How to Bring your ABAP Custom Code to SAP BTP ABAP Environment](https://blogs.sap.com/2019/11/11/how-to-bring-your-abap-custom-code-to-sap-cloud-platform-abap-environment/).

