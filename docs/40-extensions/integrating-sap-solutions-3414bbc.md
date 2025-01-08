<!-- loio3414bbc13ddc472a9be29b9036ad7c26 -->

# Integrating SAP Solutions

You can integrate several systems and services as part of the common business scenario. To do that, you create a formation in the SAP BTP cockpit that includes all systems that the scenario requires.

A formation is a logical grouping of SAP systems that can be integrated as part of a business scenario. Formations allow you to combine SAP solution systems to simplify the connectivity setup and to provide a unified view of all components required for the implementation of your integration or extension scenario. To create a fully functional formation, you have to include SAP solution systems. You do this configuration once and you can change it anytime.

See [Automating Integrations Using Formations](automating-integrations-using-formations-68b04fa.md).



<a name="loio3414bbc13ddc472a9be29b9036ad7c26__section_yrc_44p_fdc"/>

## Use Cases



### Integrate SAP Systems to Achieve a Business Scenario

This formation use case enables some of the SAP systems included in such a formation to communicate with each other.

These are the formations types following this use case:

-   *Integration with SAP Ariba Buying*. See [Automating Integrations with SAP Ariba Buying](automating-integrations-with-sap-ariba-buying-3c98c84.md).

-   *Integration with SAP Start*. See [Automating Integrations with SAP Start](automating-integrations-with-sap-start-f7d3f5e.md).

-   *Data Ingestion for Industry Cloud Solutions*. See [Automating Integrations with Data Ingestion for Industry Cloud Solutions](automating-integrations-with-data-ingestion-for-industry-cloud-solutions-0b23a32.md).

-   *Integration with SAP Ariba Central Invoice Management*. See [Automating Integrations with SAP Ariba Central Invoice Management](automating-integrations-with-sap-ariba-central-invoice-management-27ca5c2.md).




### Integrate SAP Systems with a Service in SAP BTP

There are formations dedicated to automate the integration between supported SAP systems and a service in SAP BTP. In this use case the topology is star where the service is in the center and is communicating with every SAP system that is included in the formation. The formation type is related to the service. The SAP systems that are included do not communication between each other.

These are the formations types following this use case:

-   *Eventing Between SAP Cloud Systems*. See [Enabling Events Exchange Between SAP Cloud Systems](enabling-events-exchange-between-sap-cloud-systems-1592246.md).

-   *Integration with SAP Master Data Integration*. See [Enabling Integration with SAP Master Data Integration](enabling-integration-with-sap-master-data-integration-9743f20.md).

-   *Integration with Joule*. See [Enabling Joule](enabling-joule-e208f1f.md).




### Integrate SAP Systems to Achieve an Extensibility Scenario

Automated configuration allows you to extend SAP solutions without affecting their core functions. It also provides a central repository for APIs and data, ensuring easy access to services for developing extensions.

These are the formations types following this use case:

-   *Side-by-Side Extensibility with Kyma*. See [Setting Up System Landscape for Kyma](setting-up-system-landscape-for-kyma-9154051.md).

-   *Developing with SAP Business Application Studio*. See [Setting Up System Landscape for SAP Business Application Studio](setting-up-system-landscape-for-sap-business-application-studio-272ca23.md).

-   *Integration with SAP Build*. See [Setting Up System Landscape for SAP Build](setting-up-system-landscape-for-sap-build-6424311.md).

-   *Integration with SAP Integration Suite*. See [Setting Up System Landscape for SAP Integration Suite](setting-up-system-landscape-for-sap-integration-suite-a14c276.md).


