<!-- loio08b1effc53634890a525f945017e2edc -->

# Extensions

The extension capabilities of SAP Business Technology Platform \(SAP BTP\) enables developers to implement loosely coupled extension applications securely, thus implementing additional workflows or modules on top of the existing SAP cloud solution they already have.



<a name="loio08b1effc53634890a525f945017e2edc__section_cl5_p4h_q3b"/>

## Unified Customer Landscape

The Unified Customer Landscape service provides capabilities for automated extensibility and integration of SAP and third-party systems.

All standard SAP solutions are offered with customizing capabilities. Additionally, customers often have their own requirements for innovative or industry-specific extensions and the extension capabilities of SAP BTP can help them build, deploy, and operate their new functionality.

You can extend standard SAP solutions without disrupting their performance and core processes. When building extension applications, you can also benefit from the automation of the integration between the cloud platform and the extended SAP solutions.

You can also benefit from an automated integration between SAP systems or between SAP systems and a specific service in SAP BTP.

Using the Unified Customer Landscape service, you can maintain your customer landscape. The frontend representation of this service is the *System Landscape* page in the SAP BTP cockpit. The dedicated SAP S/4HANA Cloud Extensibility and SAP SuccessFactors Extensibility services are also part of the Unified Customer Landscape capabilities. See [Maintaining Unified Customer Landscape](maintaining-unified-customer-landscape-a8b1e26.md).

To get a full list of terms related to the extensibility and integration concepts in the Unified Customer Landscape area, see [Extensibility Concepts](extensibility-concepts-3ce5e05.md).



<a name="loio08b1effc53634890a525f945017e2edc__section_uxx_xdg_ndc"/>

## Registering and Deregistering Systems

To connect a system with a global account in SAP BTP, you need to have the system listed in the *System* page.

[Registering and Deregistering Systems](registering-and-deregistering-systems-2ffdaff.md)



<a name="loio08b1effc53634890a525f945017e2edc__section_xlp_ycg_ndc"/>

## Extending SAP Solutions

The extension capabilities of SAP BTP provide a standard way for extending SAP solutions and developing event-driven extensions and applications. This framework includes:

-   Simplified, standardized and unified extensibility and configuration for the SAP solutions.

-   Central catalog per customer for all connected SAP systems where data such as APIs, events, credentials and other is stored. You can benefit from business services and actionable events across end-to-end business processes.


You have the following options to extend your SAP solution using the SAP SuccessFactors Extensibility or SAP S/4HANA Cloud Extensibility services:

-   Extensions with automated configurations in the Cloud Foundry runtime: applicable for SAP S/4HANA Cloud, SAP Marketing Cloud, and SAP SuccessFactors.

-   Extensions with automated configurations in the Kyma runtime: applicable for SAP S/4HANA Cloud, SAP Marketing Cloud, SAP SuccessFactors, SAP Cloud for Customer, SAP Commerce Cloud, and SAP Field Service Management.


If you have to group the systems of different SAP solutions in the same business case, you can set up the connectivity between all these systems and a global account in SAP BTP in a single formation in the SAP BTP cockpit. See [Including Systems in a Formation](including-systems-in-a-formation-68b04fa.md).

See [Extending SAP Solutions](extending-sap-solutions-346864d.md).



<a name="loio08b1effc53634890a525f945017e2edc__section_gqf_qqq_tkb"/>

## Troubleshooting

If you encounter a problem when extending an SAP S/4HANA Cloud or an SAP SuccessFactors system, go through the following troubleshooting information first:

-   [Troubleshooting for SAP S/4HANA Cloud Extensibility Service](troubleshooting-for-sap-s-4hana-cloud-extensibility-service-3725f59.md)

-   [Troubleshooting for SAP SuccessFactors Extensibility Service](troubleshooting-for-sap-successfactors-extensibility-service-46f358f.md)


**Related Information**  


[SAP BTP Developer's Guide: Extending Existing SAP Solutions Using SAP BTP](https://help.sap.com/docs/btp/btp-developers-guide/extending-existing-sap-solutions-using-sap-btp?version=Cloud)

