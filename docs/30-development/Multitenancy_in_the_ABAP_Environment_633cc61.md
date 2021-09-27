<!-- loio633cc61560734a8fb8dba64b4dd904a9 -->

# Multitenancy in the ABAP Environment



<a name="loio633cc61560734a8fb8dba64b4dd904a9__section_l5r_5yc_hpb"/>

## Multitenancy

Multitenancy in the ABAP environment enables independent software vendors or partners \(referred to as “**providers**”\) to develop and run ABAP solutions as Software-as-a-Service \(SaaS\) leveraging SAP BTP infrastructure while hosting several consumers on the same ABAP system.

**Consumers** \(= end customers of the provider\) subscribe to a provider’s multitenant SaaS application and use it in a specific tenant. Consumers access the provider’s SaaS application via a tenant-specific link, see [Consumer Access](Consumer_Access_a197d6f.md).

The *Landscape Portal* app functions as a central plane for tenant management that allows providers to perform lifecycle management operations such as add-on updates, creating test tenants or support users and more. For more information on how to access and use the *Landscape Portal*, see [Landscape Portal](Landscape_Portal_5eb70fb.md).

When building tenant-aware applications on top of the ABAP environment, providers need to follow dedicated rules to ensure a content separation between different consumers. To view these guidelines, see [Development Guideline to Enable Multitenancy of Products Built on the ABAP Environment](Development_Guideline_to_Enable_Multitenancy_of_Products_Built_on_the_ABAP_Environment_9d994c8.md).



<a name="loio633cc61560734a8fb8dba64b4dd904a9__section_xxc_jqp_qmb"/>

## Terminology

In this documentation, we will distinguish the following two user groups:

-   **Provider**: The service provider is responsible for the development and maintenance of the SaaS application. This is typically an independent software vendor or development partner.

-   **Consumer**: The service consumer is an end-customer of the service provider and uses the SaaS application in a specific tenant.




<a name="loio633cc61560734a8fb8dba64b4dd904a9__section_d3d_4rm_wpb"/>

## Prerequisites:

To use multitenancy in the ABAP environment, you need to fulfill the following prerequisites.

-   You have acquired an ABAP environment license for partners. For development purposes, please refer to the [SAP PartnerEdge TD&D price list](https://partneredge.sap.com/en/welcome.html?pexpRequestedURL=%2Fen%2Flibrary%2Fassets%2Fpartnership%2Fsales%2Forder_license%2Fpl_pl_part_price_list.html). For production licenses, please contact your SAP Account Manager.

-   As a service provider, you’ve been registered by SAP, have your own global account and production subaccount where your production ABAP instances reside, and have the Admin Cloud Foundry role assigned to your S-user.
-   You have assigned the following entitlements to your subaccounts in the SAP BTP cockpit:

    -   Services:

        -   ABAP Environment
            -   hana\_compute\_unit
            -   abap\_compute\_unit
            -   for add-on based delivery: saas\_oem
            -   for delivery via gCTS: standard
        -   ABAP Solution
        -   Cloud Foundry Runtime
    -   Applications:

        -   Landscape Portal
        -   Web Access for ABAP

-   **[Development Guideline to Enable Multitenancy of Products Built on the ABAP Environment](Development_Guideline_to_Enable_Multitenancy_of_Products_Built_on_the_ABAP_Environment_9d994c8.md "Multitenancy is required if you want to run several customers on the same ABAP system.
		When building tenant-aware applications on top of the ABAP
                                environment, you must
		follow dedicated rules to ensure, for example, a content separation between different
		customers.")**  
Multitenancy is required if you want to run several customers on the same ABAP system. When building tenant-aware applications on top of the ABAP environment, you must follow dedicated rules to ensure, for example, a content separation between different customers.
-   **[Landscape Portal](Landscape_Portal_5eb70fb.md)**  

-   **[Developing Multitenant Applications in the ABAP Environment](Developing_Multitenant_Applications_in_the_ABAP_Environment_195031f.md)**  

-   **[Consumer Offboarding](Consumer_Offboarding_c882a2a.md)**  


**Related Information**  


[Landscape Portal](Landscape_Portal_5eb70fb.md)

[Developing Multitenant Applications in the ABAP Environment](Developing_Multitenant_Applications_in_the_ABAP_Environment_195031f.md)

[Subscribe New Consumers](Subscribe_New_Consumers_b90cde1.md)

[Consumer Access](Consumer_Access_a197d6f.md)

[Consumer Offboarding](Consumer_Offboarding_c882a2a.md)

[Development Guideline to Enable Multitenancy of Products Built on the ABAP Environment](Development_Guideline_to_Enable_Multitenancy_of_Products_Built_on_the_ABAP_Environment_9d994c8.md "Multitenancy is required if you want to run several customers on the same ABAP system. When building tenant-aware applications on top of the ABAP environment, you must follow dedicated rules to ensure, for example, a content separation between different customers.")

