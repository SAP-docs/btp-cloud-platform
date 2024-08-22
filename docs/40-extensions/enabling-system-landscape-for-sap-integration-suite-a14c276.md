<!-- loioa14c2769117043afb4e56da12d5ea885 -->

# Enabling System Landscape for SAP Integration Suite



<a name="loioa14c2769117043afb4e56da12d5ea885__section_g21_b52_lcc"/>

## Use

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

A registered SAP S/4HANA Cloud system in the SAP BTP cockpit can expose consumption bundles that contain APIs and events. You can easily discover and consume the APIs exposed by the SAP S/4HANA Cloud systems in your system landscape when you develop and extend applications on SAP BTP, Cloud Foundry environment. To do this, first you need to enable connectivity between your system landscape in SAP BTP cockpit and SAP Integration Suite. The integration requires performing several configuration steps starting with configuration on a global account level, and then, configuration on a subaccount level.



<a name="loioa14c2769117043afb4e56da12d5ea885__section_apz_d52_lcc"/>

## Rules

When creating *Integration with SAP Integration Suite* formations, keep in mind the following rule:

-   At most one system of type *SAP Integration Suite* can be included in one *Integration with SAP Integration Suite* formation.




## Prerequisites

-   You are a global account administrator, or you are a system landscape administrator. See [Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md).

-   You have a subscription to SAP Integration Suite. See[Subscribing and Configuring Initial Access to SAP Integration Suite](https://help.sap.com/docs/integration-suite/sap-integration-suite/subscribing-to-integration-suite?version=CLOUD).




<a name="loioa14c2769117043afb4e56da12d5ea885__section_npx_bbl_xbc"/>

## Procedure

The following procedure outlines the steps you need to perform to consume the APIs of registered SAP S/4HANA Cloud systems within SAP Integration Suite.

1.  Add and then register an SAP system of type *SAP S/4HANA Cloud* in the *System Landscape* page of SAP BTP cockpit.

    To expose information about its APIs and events and show this information on the *System Landscape* page, an SAP system of type *SAP S/4HANA Cloud* must be registered in the SAP BTP cockpit. Only when registered, the system communicates information about its APIs and other technical details across the landscape. See [Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](register-an-sap-s-4hana-cloud-system-in-a-global-account-in-sap-btp-28171b6.md).

2.  Create a formation of type *Integration with SAP Integration Suite* and include the SAP S/4HANA Cloud systems you want to expose to SAP Integration Suite. See [Including Systems in a Formation](including-systems-in-a-formation-68b04fa.md).

    > ### Note:  
    > In the formation type *Integration with SAP Integration Suite*, you can include only SAP systems of type *SAP S/4HANA Cloud*.


