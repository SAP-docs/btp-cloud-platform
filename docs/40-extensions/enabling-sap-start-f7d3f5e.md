<!-- loiof7d3f5ec8a0e4f9bb5b77d473be99e5a -->

# Enabling SAP Start



<a name="loiof7d3f5ec8a0e4f9bb5b77d473be99e5a__section_kbh_41c_dwb"/>

## Use

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

SAP Start is a predefined central entry point for accessing SAP cloud business solutions that are integrated with it, such as SAP S/4HANA Cloud

To set up SAP Start with SAP S/4HANA Cloud on SAP BTP you need to have all the necessary systems included in a formation of type *Integration with SAP Start* in the *System Landscape* page of the SAP BTP cockpit.

When creating *Integration with SAP Start* formations, keep in mind the following rules:

-   SAP Start systems can be included in at most one *Integration with SAP Start* formation.

-   At most one SAP Start system can be included in an *Integration with SAP Start* formation.

-   Only SAP S/4HANA Cloud systems that are registered with *All Communication Scenarios* or *Integration with SAP Start* communication scenario group can be part of a *Integration with SAP Start* formation. See [Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](register-an-sap-s-4hana-cloud-system-in-a-global-account-in-sap-btp-28171b6.md).




<a name="loiof7d3f5ec8a0e4f9bb5b77d473be99e5a__section_znb_p1c_dwb"/>

## Prerequisites

-   Integration with SAPYou are a global account administrator, or you are a system landscape administrator. See [Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md).

-   You have an Identity Authentication tenant. See [Indentity Authentication: Initial Setup](https://help.sap.com/docs/identity-authentication/identity-authentication/initial-setup?version=Cloud).

-   \(Optional: if you are using the *Set Up SAP Start* booster in the SAP BTP cockpit, this step will be automatically done by the booster.\) Check that you have a system of type *SAP Start* in the *Systems* list. This system is added through a subscription in SAP BTP cockpit associated with a given subaccount. The subscription has been discovered and added automatically through the subaccount.

-   Check that you have a system of type *SAP S/4HANA Cloud* in the *Systems* list in the *System Landscape* page. This system is auto-discovered because it is associated with your global account and has been discovered and added automatically to the list based on information of the existing system landscape.

    > ### Note:  
    > If you don't find your system of type *SAP S/4HANA Cloud* in the *Systems* list, add this system manually. See [Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](register-an-sap-s-4hana-cloud-system-in-a-global-account-in-sap-btp-28171b6.md).

-   Register the SAP S/4HANA Cloud system in the *Systems* list in the *System Landscape* page.

    When you register an SAP S/4HANA Cloud system, use the *Integration with SAP Start* communication scenario group when you get the registration token for the SAP S/4HANA Cloud system. This allows the automatic enablement of the communication scenario `SAP_COM_0647` after the corresponding system is added to the formation of type *Integration with SAP Start*.

    See [Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](register-an-sap-s-4hana-cloud-system-in-a-global-account-in-sap-btp-28171b6.md).




<a name="loiof7d3f5ec8a0e4f9bb5b77d473be99e5a__section_v4q_p1c_dwb"/>

## Procedure

If you have SAP Start set up in your subaccount in SAP BTP, follow these steps to configure the integration between SAP Start and SAP S/4HANA Cloud using a formation of type *Integration with SAP Start*.

If you want to have the end-to-end setup automatically, including creating the formation, use the *Set Up SAP Start* booster in the SAP BTP cockpit to guide you through the steps to configure SAP Start in your subaccount and integrate it with SAP S/4HANA Cloud.

1.  In the *Systems* list, find the systems of type *SAP Start* and *SAP S/4HANA Cloud* that you want to include in a formation.

2.  Create a formation of type *Integration with SAP Start* and include the relevant systems in it.

    1.  Add any name that helps you identify your formation.

    2.  In the *Formation Type* dropdown menu, select *Integration with SAP Start*.

    3.  Select the *SAP Start* and *SAP S/4HANA Cloud* systems that you want to include in the formation.

    4.  Review your selections and create the formation.





<a name="loiof7d3f5ec8a0e4f9bb5b77d473be99e5a__section_bbm_s3m_vvb"/>

## Next Steps

When the formation is created, you have SAP Start set up with SAP S/4HANA Cloud on SAP BTP. Then, set up SAP Task Center. See [Post-Setup Tasks](https://help.sap.com/docs/start/sap-start/post-setup-tasks).

