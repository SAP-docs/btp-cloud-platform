<!-- loio3c98c84c61784e2985854cede54dd105 -->

# Automating Integrations with SAP Ariba Buying



<a name="loio3c98c84c61784e2985854cede54dd105__section_kbh_41c_dwb"/>

## Use

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

SAP Ariba Buying offers procurement users a unique buying experience through a guided process. SAP Ariba Buying provides buyers an easy process to shop for items. Buyers can search for, view and purchase items that are available in the connected shopping sites, or request items from suppliers. SAP Ariba Buying also helps buyers to track their purchase requests.

To set up SAP Ariba Buying with SAP S/4HANA Cloud on SAP BTP you need to have all the necessary systems included in a formation of type *Integration with SAP Ariba Buying* in the *System Landscape* \> *Systems* page of the SAP BTP cockpit.

> ### Note:  
> This documentation refers to SAP S/4HANA Cloud Public Edition. See [Introduction to the Universe of SAP S/4HANA Cloud Public Edition](https://help.sap.com/docs/SAP_S4HANA_CLOUD/f77dde055ecb4541b57787d362c46a36/2962fce53eef47b4b3a8e6c945adafbe.html).



<a name="loio3c98c84c61784e2985854cede54dd105__section_lmn_xwk_lcc"/>

## Rules

When creating *Integration with SAP Ariba Buying* formations, keep in mind the following rules:

-   SAP S/4HANA Cloud systems can be included in at most one *Integration with SAP Ariba Buying* formation.

-   Only SAP S/4HANA Cloud systems that are registered with *All Communication Scenarios* or *Integration with SAP Ariba Buying* communication scenario group can be part of a *Integration with SAP Ariba Buying* formation. See [Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](register-an-sap-s-4hana-cloud-system-in-a-global-account-in-sap-btp-28171b6.md).




<a name="loio3c98c84c61784e2985854cede54dd105__section_znb_p1c_dwb"/>

## Prerequisites

-   You are a global account administrator, or you are a system landscape administrator. See [Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md).

-   You have an Identity Authentication tenant. See [Indentity Authentication: Initial Setup](https://help.sap.com/docs/identity-authentication/identity-authentication/initial-setup?version=Cloud).

-   \(Optional: if you are using the *Set Up SAP Ariba Buying* booster in the SAP BTP cockpit, this step will be automatically done by the booster.\) Check that you have a system of type *SAP Ariba Buying* in the *Systems* page. This system is added through a subscription in SAP BTP cockpit associated with a given subaccount. The subscription has been discovered and added automatically through the subaccount. To have a system of type *SAP Ariba Buying* in the *Systems* page, you need to:

    -   You have subscribed to SAP Ariba Buying. See [Get a Subscription to SAP Ariba Buying](https://help.sap.com/docs/SAP_Ariba_Buying/28baac3abbeb4ea1a5ab25033f326c44/f8ff8be8a53a4f66965aaa86016cb18c.html).

    -   You have subscribed to the services required for SAP Ariba Buying. See [Subscribe to Services Required for SAP Ariba Buying](https://help.sap.com/docs/SAP_Ariba_Buying/28baac3abbeb4ea1a5ab25033f326c44/2b8c251c8d744c0b8345b0fd11e7574d.html).


-   Check that you have a system of type *SAP S/4HANA Cloud* in the *Systems* page. This system is auto-discovered because it is associated with your global account and has been discovered and added automatically to the list based on information of the existing system landscape.

    > ### Note:  
    > If you don't find your system of type *SAP S/4HANA Cloud* in the *Systems* page, add this system manually. See [Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](register-an-sap-s-4hana-cloud-system-in-a-global-account-in-sap-btp-28171b6.md).

-   Register the SAP S/4HANA Cloud system in the *Systems* page.

    When you register an SAP S/4HANA Cloud system, use the *Integration with SAP Ariba Buying* communication scenario group when you get the registration token for the SAP S/4HANA Cloud system. This allows the automatic enablement of the communication scenarios `SAP_COM_0545` and `SAP_COM_0A00` after the corresponding system is added to the formation of type *Integration with SAP Ariba Buying*. See [Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](register-an-sap-s-4hana-cloud-system-in-a-global-account-in-sap-btp-28171b6.md).




<a name="loio3c98c84c61784e2985854cede54dd105__section_v4q_p1c_dwb"/>

## Procedure

If you have SAP Ariba Buying set up in your subaccount in SAP BTP, follow these steps to configure the integration between SAP Ariba Buying and SAP S/4HANA Cloud using a formation of type *Integration with SAP Ariba Buying*.

If you want to have the end-to-end setup automatically, including creating the formation, use the *Set Up SAP Ariba Buying* booster in the SAP BTP cockpit to guide you through the steps to configure SAP Ariba Buying in your subaccount and integrate it with SAP S/4HANA Cloud.

1.  In the *Systems* page, find the systems of type *SAP Ariba Buying* and *SAP S/4HANA Cloud* that you want to include in a formation.

2.  In the *System Landscape* \> *Formations* page, create a formation of type *Integration with SAP Ariba Buying* and include the relevant systems in it.

    1.  Add any name that helps you identify your formation.

    2.  In the *Formation Type* dropdown menu, select *Integration with SAP Ariba Buying*.

    3.  Select the *SAP Ariba Buying* and *SAP S/4HANA Cloud* systems that you want to include in the formation.

    4.  Review your selections and create the formation.





<a name="loio3c98c84c61784e2985854cede54dd105__section_bbm_s3m_vvb"/>

## Next Steps

When the formation is created, you have SAP Ariba Buying set up with SAP S/4HANA Cloud on SAP BTP.

