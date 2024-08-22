<!-- loio0b23a32acddc4750840f82fef9a87383 -->

# Enabling Data Ingestion for Industry Cloud Solutions



<a name="loio0b23a32acddc4750840f82fef9a87383__section_hq5_kcg_lcc"/>

## Use

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

SAP’s industry cloud provides specialized industry-focused solutions to help you optimize, extend, and transform your core business processes. Developed by SAP and SAP partners and based on SAP Business Technology Platform \(SAP BTP\), industry cloud solutions integrate with SAP S/4HANA Cloud and SAP Business Network. They help you take advantage of the latest industry-relevant innovations and extend existing capabilities in an efficient way. For a list of all industry cloud solutions published by SAP, see [SAP Store](https://store.sap.com/dcp/en/search?sortCode=name-asc&query=:name-asc:useCases:Industry%20Cloud:publisher:SAP).

Data ingestion for industry cloud solutions allows supported industry cloud solutions to consume data from a shared data foundation instead of integrating with the source systems individually. This helps to simplify solution implementation, increase operational visibility, and improve data quality. For a list of all industry cloud solutions published by SAP that support data ingestion, see [Data Integration Overview](https://help.sap.com/docs/DI_ICS/925366f331c54ee88e2b61ddae0be9fc/88da41cc955e49f1b7080e882bae36d4.html).

To set up on SAP BTP systems that support data ingestion and are part of the industry cloud solutions published by SAP, you need to include them in a formation of type *Data Ingestion for Industry Cloud Solutions*. When you create a new formation of type *Data Ingestion for Industry Cloud Solutions*, a system of type *Data Ingestion for Industry Cloud Solutions* is automatically added to the *Systems* list and included in this formation.



<a name="loio0b23a32acddc4750840f82fef9a87383__section_o4m_jcg_lcc"/>

## Rules

When creating *Data Ingestion for Industry Cloud Solutions* formations, keep in mind the following rules:

-   Only systems that are part of the industry cloud solutions, support data ingestion, and are provisioned from SAP for Me can be included in formations of type *Data Ingestion for Industry Cloud Solutions*.

-   System that is part of the industry cloud solutions published by SAP are included in at most one *Data Ingestion for Industry Cloud Solutions* formation when creating this formation.

-   System of type *Data Ingestion for Industry Cloud Solutions* is automatically registered and included in the *Data Ingestion for Industry Cloud Solutions* formation.

-   System of type *Data Ingestion for Industry Cloud Solutions* cannot be excluded from the *Data Ingestion for Industry Cloud Solutions* formation. Once you delete this formation, the *Data Ingestion for Industry Cloud Solutions* system is automatically deleted.




<a name="loio0b23a32acddc4750840f82fef9a87383__section_znb_p1c_dwb"/>

## Prerequisites

You are a global account administrator, or you are a system landscape administrator. See [Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md).



<a name="loio0b23a32acddc4750840f82fef9a87383__section_v4q_p1c_dwb"/>

## Procedure

1.  In the *System Landscape* page of the SAP BTP cockpit, in the *Systems* list, browse the already added systems that are part of the industry cloud solutions published by SAP in your customer system landscape.

2.  Create a formation of type *Data Ingestion for Industry Cloud Solutions* and include the relevant systems in it.

    1.  Add any name that helps you identify your formation.

    2.  In the *Formation Type* dropdown menu, select *Data Ingestion for Industry Cloud Solutions*.

    3.  Select the systems that you want to include in the formation.

    4.  Review your selections and create the formation.



**Related Information**  


[Data Integration Overview](https://help.sap.com/docs/DI_ICS/925366f331c54ee88e2b61ddae0be9fc/88da41cc955e49f1b7080e882bae36d4.html)

