<!-- loio9aa67889b0164a22bcc6a99a11c99d5e -->

# Integrating Business Users from an External Identity Management System

You can use this communication scenario for the business user.

The communication scenario `SAP_COM_0093` allows you to use and provision business users from an external data source, for example an identity management system, in SAP Integrated Business Planning.

The communication scenario gives you access to two SOAP services:

-   `MANAGEBUSINESSUSERIN` lets you create business users in your system

-   `QUERYBUSINESSUSERIN` lets you read existing business users from your external data source into your own identity management system.

-   `QueryBusinessUserMetadaIn` lets you read metadata information for the service `MANAGEBUSINESSUSERIN` from an external data source such as an identity management system.

    The service provides the search parameter `RoleCategory`, which restricts the result set of the metadata information of the service. The response includes the metadata information based on the given criteria. If errors occur, the log contains information about the severity code, the message number, and message texts.

    > ### Note:  
    > This scenario processes personal data. For more information on how to handle data protection and privacy, see [Data Protection and Privacy](https://help.sap.com/docs/SAP_INTEGRATED_BUSINESS_PLANNING/685fbd2d5f8f4ca2aacfc35f1938d1c1/615b0755d6993f6ae10000000a44176d.html?locale=en-US).


For more information, see the service documentation on the [SAP Business Accelerator Hub](https://api.sap.com/) and search for *SAP IBP - Identity Management*.

**Related Information**  


[Inbound Service: Business User](inbound-service-business-user-a631f4e.md)

[Inbound Service: Business User - Read](inbound-service-business-user-read-535e7af.md)

[Business User - Read Metadata](business-user-read-metadata-dd6003b.md)

