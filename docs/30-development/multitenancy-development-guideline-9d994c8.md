<!-- loio9d994c89909c49e2957db840d7eace5c -->

# Multitenancy Development Guideline

Multitenancy is required if you want to run several customers on the same ABAP system. When building tenant-aware applications on top of the ABAP environment, you must follow dedicated rules to ensure, for example, a content separation between different customers.



## Architecture Overview and Basic Concept

The following sections explain how to host multiple tenants in one ABAP system by building a multitenant enabled solution. We use multiple clients in the ABAP environment as a technical means to implement multitenancy.

There are the following basic principles regarding multitenancy:

-   for the **tenant**: Strict data isolation is guaranteed between tenants on all levels of the system. It must be ensured that the tenants' data as well as their tenant-specific application extensions are under no circumstances mingled with the data or applications of any other tenant being operated in the same system.

-   for the **hosting provider**: The costs for operating multiple tenants in the same system must be significantly lower compared to single tenant systems. Multitenant systems must reduce the TCO of a hosted solution in such a way that the business case is met.

    > ### Note:  
    > Multitenancy is only one means to reduce the marginal costs of operations addressing system and hardware costs.


To some extent, these principles are contradictory. The first principle could be most easily fulfilled by single tenant systems, whereas the second principle imposes the need for sharing resources on each system level, for example, hardware, database, application server. Multitenancy can thus be described as sharing as much system resources as possible without violating the principle of tenant data isolation.

> ### Note:  
> Tenant isolation isn't completely ensured by the ABAP environment infrastructure. However, the following sections describe the design principles how multitenancy can be achieved in the ABAP environment by an evolution of the present multiclient capability of an ABAP system.

The ABAP environment is a Platform as a Service \(PaaS\) offering for ABAP. In a typical scenario, an independent software vendor \(ISV\) develops and runs a Software as a Service \(SaaS\) application in the ABAP environment and sells this application to end-customers. In order to avoid confusion with the term “customer”, as the ISV is also a customer of the ABAP environment, the following terminology is used in this document:

-   The **service provider** of the SaaS application is responsible for developing, maintaining, and operating the application on top of the ABAP environment. The service provider is typically an ISV or a development partner.

-   The **provider system** is an ABAP system in the ABAP environment that runs the SaaS application. The provider system is operated by the service provider and offers multitenancy capabilities.
-   The **service consumer** of the SaaS application is an end-customer of the service provider who has subscribed a tenant in a provider system.



<a name="loio9d994c89909c49e2957db840d7eace5c__section_erp_vcg_r4b"/>

## Assumptions and Limitations

-   Multitenancy is only supported in provider systems operated by the same service provider to run a single SaaS application.

-   Multitenancy isn't supported for the development scenario using the ABAP Development Tools \(ADT\). This means that several service providers can't share the same system for development. Furthermore, a consumer can't further develop or extend the provider’s SaaS application using ADT.

-   You as a service provider can build a multitenancy application following the respective guidelines.

-   Transport of objects isn't supported in a multitenant environment.

    Business configuration content is usually transported to a productive environment by using the transport API `IF_A4C_BC_HANDLER`, in this case, the user interface doesn't have to be implemented. To transport business configurations between systems, you can use the download/upload functionality, see

    [Upload Business Configuration](../50-administration-and-ops/upload-business-configuration-c8ca7be.md).

-   There is no system-controlled process to ensure that you as a service provider build your application in a multitenancy-compliant way. If strict data isolation is a legal requirement, we propose an external audit to ensure that your code doesn't break data isolation.

-   There are options to share data between tenants. Furthermore, native SAP HANA database access via ABAP-managed database procedures \(AMDP\) requires special considerations. It's only documented which functionality does have which impact on client isolation. There is no check ensuring that you as a service provider use these features in a multitenancy-compliant way.

-   To ensure tenant lifecycle procedures, the applications must be built in such a way that the procedures for tenant copy, tenant move, and tenant delete can deal with it.

    > ### Note:  
    > If you don't comply with these aspects of the guideline, this causes issues where SAP, you as a provider, and the consumer are involved.

-   Security and system logs store data in a cross-client persistence together.

-   Any multitenancy-specific certifications from SAP in addition to the already existing ABAP environment product certifications are out of scope.




<a name="loio9d994c89909c49e2957db840d7eace5c__section_kcl_j1n_t4b"/>

## Guidelines for Multitenancy Applications in the ABAP environment

The following sections cover the relevant guidelines for content separation in multiclient systems. We use the multiclient architecture of the ABAP system for multitenancy enablement and list the design principles to reach multitenancy.



<a name="loio9d994c89909c49e2957db840d7eace5c__section_ikr_x21_54b"/>

## Prerequisites

-   Store tenant-related data in client-dependent tables of type A, C, or L.

-   Store system-related data in client-independent tables of type S.

-   Always add the selection of the client to ABAP database procedures \(AMDPs\).

    Make sure consumers cannot modify the client parameter or any other part of the AMDP using the application or by tampering requests.

-   Don't generate development objects or other client-independent data system-locally in the provider system.

-   Don't evaluate the actual value of the 3-digit client field \(IF sy-mandt = ‘nnn’. …. ENDIF\).




<a name="loio9d994c89909c49e2957db840d7eace5c__section_uw2_nf1_54b"/>

## Database Table Design

You have to classify database tables according to their content. There are the following types:

-   Tenant Content \(client-dependent\)

    -   Tenant configuration data – tables with delivery class “C”

    -   Tenant application data – tables with delivery class “A”

    -   Tenant temporary data – tables with delivery class “L”



Database tables for tenant content must be client-dependent. This means that the first field of the table must be of datatype “CLNT”. We recommend using the inline declaration „abap.clnt“.

Only the content of client-dependent “C” and “A” tables is considered during tenant copy and tenant move. Content of client-independent tables which are not delivered from the development system and “L” tables are lost during tenant lifecycle processes such as tenant move.

During tenant delete, the content of all client-dependent tables is removed.

The delivery class must be “C”, “A”, or “L”.

The delivery classes “E”, “G” and “W” are not supported in the ABAP environment at all.

-   System Content \(client-independent\)

    -   System configuration data – tables with delivery class “S”


Store data that is defined by the service provider and not specific for any tenant in a client-independent “S” table. Define the content in the respective development system and export it as TABU entries via a development transport request. The content is considered as code and imported like other development artifacts into subsequent systems such as the provider system.



<a name="loio9d994c89909c49e2957db840d7eace5c__section_ohq_bh1_54b"/>

## Database Table Access

-   Read Access Using ABAP SQL

    Whenever you access table content, ensure that you don't violate tenant isolation. ABAP SQL does not support additions such as CLIENT SPECIFIED or USING CLIENT in the ABAP environment. As a result, access to other clients than SY-MANDT is technically not possible. But you have to define client-dependent tables properly so that the ABAP runtime applies this role accordingly.

-   Write Access Using ABAP SQL

    Do not write “S” tables in the provider system.

    > ### Note:  
    > If you write “S” tables in the provider system, this content is not considered during tenant lifecycle management events, such as tenant move, and you lose content. Furthermore, you violate tenant isolation, since every tenant has immediately access to the changes.

-   Access Using AMDP

    Access to SAP HANA database using AMDP is not controlled via the ABAP database interface. The client is just handed over as a parameter. This can easily violate the content separation and access a table data for another client. Make sure that the client is always passed via SY-MANDT.

    Consumers must never be able to modify the client parameter or any other part of the AMDP using the application or by tampering requests.

    > ### Note:  
    > In the future, it is highly recommended to use the AMDP option CDS SESSION CLIENT DEPENDENT or CLIENT INDEPENDENT.




<a name="loio9d994c89909c49e2957db840d7eace5c__section_qnd_rs1_54b"/>

## Code Generation

Development artifacts such as Data Dictionary objects, classes, or interfaces, which are typically created via ABAP Development Tools \(ADT\), are always client-independent. Changes are always recorded in transport requests.

> ### Note:  
> It is not allowed to generate development artifacts in a non-development system, such as a provider system. This generation violates the content separation and is not be considered during tenant move and copy procedures. You are only allowed to generate development artifacts in **development systems** in the ABAP environment. You can use the XCO library for that purpose. If you generate development artifacts, the service provider is responsible for ensuring that the generated artifacts are transported into all required provider systems. Standard lifecycle events such as a tenant move don't consider such client-independent artifacts.



<a name="loio9d994c89909c49e2957db840d7eace5c__section_rc4_vt1_54b"/>

## Multitenant-Aware Programming

-   Cross-Client Locking \(Enqueue\)

    Lock Objects are associated to database tables or structures. The runtime API in the ABAP environment is `CL_ABAP_LOCK_OBJECT_FACTORY` and the returned instance of type `IF_ABAP_LOCK_OBJECT`.

    > ### Note:  
    > Only lock client-dependent database tables or structures having a `CLIENT` field.

-   CL\_ABAP\_CONTEXT\_INFO=\> GET\_SYSTEM\_DATE and TIME

    The system date/time \(methods `CL_ABAP_CONTEXT_INFO=>GET_SYSTEM_DATE`, `CL_ABAP_CONTEXT_INFO=>GET_SYSTEM_TIME`\) is always based on UTC time zone. The system time zone can't be changed tenant-specifically. As a usual approach in cloud environments, it needs to be considered in your code, as it gives the same date and time for all tenants.

-   Usage of System Information \(sy-sysid and sy-mandt\)

    Storing SY-SYSID and SY-MANDT explicitly in database tables is not allowed. This would lead to issues after tenant copy or tenant move, because both values are not unique and not stable in the system landscape. A dedicated API is provided to get a unique and stable identifier for the tenant. See [Tenant](tenant-bbb4dc2.md).




<a name="loio9d994c89909c49e2957db840d7eace5c__section_u1d_pbt_v4b"/>

## Connectivity

Outbound communication management in the ABAP environment differs from the on-premise usage of SM59 destinations \(see [Outbound Communication](https://help.sap.com/docs/abap-cloud/abap-integration-connectivity/outbound-communication-48d3624d9f7d47d7ab712d110cb02d77?version=sap_btp)\). It is recommended to connect tenants and systems via communication arrangements, see [Communication Management](https://help.sap.com/docs/abap-cloud/abap-integration-connectivity/communication-management).

> ### Restriction:  
> The ABAP environment only supports one communication configuration layer that is intended for the consumer. It is currently not possible to enforce a communication configuration exclusively managed by the service provider within the consumer tenant.



<a name="loio9d994c89909c49e2957db840d7eace5c__section_srx_qct_v4b"/>

## Limitations

There might be some use cases where the guidelines provided are not applicable, for example, when sharing data across tenants or sharing aggregated customer data.

For such use cases, the operations concept needs to be documented and an alignment with SAP is required. We recommend checking the operational impact on tenant move and tenant copy procedures. In addition, we recommend a review for multiclient content separation.



<a name="loio9d994c89909c49e2957db840d7eace5c__section_gmr_m2t_v4b"/>

## Usage of SAP-Delivered SAP Fiori Apps

SAP has delivered several SAP Fiori apps for the administration of an ABAP environment system. These SAP Fiori apps are targeting different roles, such as administrator, project manager, and developer. Regarding multitenancy, some of these apps are covering client-independent objects and configuration according to their purpose. For example, the SAP Fiori app Manage Software Components allows you to import software components, which has an immediate impact on all tenants. Therefore, you need to carefully choose which SAP-delivered business catalogs to include in the business roles of your SaaS application.

