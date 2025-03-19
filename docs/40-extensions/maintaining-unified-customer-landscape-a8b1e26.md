<!-- loioa8b1e2666e734fd2bfbca44b671585c4 -->

# Maintaining Unified Customer Landscape



<a name="loioa8b1e2666e734fd2bfbca44b671585c4__section_azd_yls_xyb"/>

## Use

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

Unified Customer Landscape is a service that offers customer landscape management capabilities. The frontend representation of this service is the *System Landscape* page in the SAP BTP cockpit. The dedicated *SAP S/4HANA Cloud Extensibility* and *SAP SuccessFactors Extensibility* services are also part of the Unified Customer Landscape capabilities.



<a name="loioa8b1e2666e734fd2bfbca44b671585c4__section_wpx_vls_xyb"/>

## Customer Landscape Discovery

The *System Landscape* page of the SAP BTP cockpit gives you a visual overview of your SAP and third-party systems associated with the given global account or a subaccount. There are different ways to add systems in the *Systems* \> *Systems* page: manually or automatically. If a system of your solution is associated with your global account or through a subscription in SAP BTP cockpit associated with a given subaccount, it will appear in the list automatically. Otherwise, you have to add your system manually. Systems are added to the list in one of the following ways:

-   Auto-Discovered

    An auto-discovered system is a system \(associated with the given global account\) that has been discovered and added automatically to the list based on information of the existing system landscape. Any SAP system of the supported system types that is associated with the same customer ID, with which your global account in SAP BTP is associated, will be added automatically in the system landscape list.

-   Subaccount/<my-subaccount\>

    Specifies that the system has been added through a subscription in SAP BTP cockpit associated with a given subaccount. The subscription has been discovered and added automatically through the subaccount.

-   Manually-Added

    Specifies that the system has been added to the list manually by the global account administrator, using the *Add System* button and completing the wizard. The system has been associated with the global account in SAP BTP.

    See [Adding, Registering and Deregistering Systems](adding-registering-and-deregistering-systems-2ffdaff.md).




<a name="loioa8b1e2666e734fd2bfbca44b671585c4__section_akf_mls_xyb"/>

## Integration and Extensibility

Unified Customer Landscape also helps you integrate and extend your SAP S/4HANA Cloud, SAP Ariba, SAP SuccessFactors, and other SAP and third-party systems in one single experience.

In the SAP BTP cockpit, you get a comprehensive overview of all your systems associated with your customer ID. These systems can be registered or auto discovered. They are conveniently listed as a record in the *Systems* list. Moreover, Unified Customer Landscape lets you integrate one or more systems in a common business case by including these systems in a formation.

See:

-   [Automating Integrations Using Formations](automating-integrations-using-formations-68b04fa.md)

-   [Extending SAP S/4HANA Cloud in the Cloud Foundry and Kyma Environment](extending-sap-s-4hana-cloud-in-the-cloud-foundry-and-kyma-environment-40b9e6c.md)

-   [Extending SAP Marketing Cloud in the Cloud Foundry and Kyma Environment](extending-sap-marketing-cloud-in-the-cloud-foundry-and-kyma-environment-18bb3d9.md)

-   [Extending SAP SuccessFactors in the Cloud Foundry and Kyma Environment](extending-sap-successfactors-in-the-cloud-foundry-and-kyma-environment-9e33934.md)

-   [Extending SAP Customer Experience Products in the Kyma Environment](extending-sap-customer-experience-products-in-the-kyma-environment-83df31a.md)


