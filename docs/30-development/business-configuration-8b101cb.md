<!-- loio8b101cb491424ade93ce6741f41f99c1 -->

# Business Configuration

Find out how to create custom business configuration objects to enrich your extensibility solutions.



<a name="loio8b101cb491424ade93ce6741f41f99c1__section_ybx_5y3_zsb"/>

## Context

An important part of a business application is business configuration. Business configuration in enterprise software refers to a predefined set of configuration options that affect its functionality and behavior. You can use your `SAP ABAP Environment` to create custom business configuration objects. Find out which tasks a developer \(business role `SAP_BR_DEVELOPER`\) needs to perform in order to implement business configuration objects. Mind that lifecycle management is usually performed by a separate user. See [Business Configuration Change Logs](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/latest/en-US/5c6cf20499894f1083e80dba7c5963d4.html) for more information.



<a name="loio8b101cb491424ade93ce6741f41f99c1__section_zbx_5y3_zsb"/>

## Procedure

Consider the following to implement your custom business configuration objects:

-   Business configuration objects are based on database tables with the delivery type C \(`@AbapCatalog.deliveryClass : #C`\). This indicates that the content in these tables can be transported between tenants.

-   Business configuration content is usually not directly maintained in a productive system, but created in a development system and then transported to the test and productive system. As a result, the corresponding transport handling must also be implemented.

-   Business users need a way to maintain content. The number of maintenance objects often exceeds the number of master data or transactional apps, yet at the same time, they are used less frequently. This suggests using a highly standardized way of providing business configuration maintenance apps.

-   Business configuration administration often involves the maintenance of language-dependent texts.


To enable the maintenance of content, a full business object is built on top of the table and exposed via an OData service, following the [RAP \(Restful ABAP Programming\)](https://help.sap.com/viewer/923180ddb98240829d935862025004d6/latest/en-US/289477a81eec4d4e84c0302fb6835035.html) model. The resulting service can be consumed by a frontend application, allowing business users to maintain business configuration content. For more information on the implementation details, please refer to the [Factory Calendar Tutorial](https://developers.sap.com/mission.abap-dev-factory-calendar.html).

SAP offers theMaintain Business Configurations Fiori application as a standardized tool for business configuration maintenance. This allows the creation of a generic maintenance app, eliminating the need for any frontend development.

As an alternative, you can also enable your business configuration object for upload or download, allowing you to quickly and reliably maintain large amounts of content. In this case, you're not required to develop a full business object. The generic file upload app supports the file format that can be downloaded from SAP ERP or SAP S/4HANA systems, thus supporting an easy migration of data from SAP on-premise systems. For more information, see [here](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/latest/en-US/c8ca7bec802a4ebcbd9444a9b1827ee0.html).

Should you have special requirements to your maintenance UI, you can also create and deploy your own custom Fiori application. For more information, see [here](develop-an-sap-fiori-application-ui-and-deploy-it-to-abap-using-sap-business-application-eaaeba4.md).

> ### Note:  
> Although the management of customizing transport requests is usually done in the [Export Customizing Transports](../50-administration-and-ops/export-customizing-transports-fa7366c.md) app by the business process configuration expert, developers can also create such transport requests using the transport organizer view in ABAP Development Tools.

