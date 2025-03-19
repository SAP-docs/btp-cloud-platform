<!-- loio15922463e5a54538857795316eb4d997 -->

# Enabling Events Exchange Between SAP Cloud Systems



<a name="loio15922463e5a54538857795316eb4d997__section_kbh_41c_dwb"/>

## Use

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

Systems that are included in *Eventing Between SAP Cloud Systems* formations on the *System Landscape* page of the SAP BTP cockpit can publish and consume events. The process of publishing and consuming events is in fact an exchange of event information across the customer system landscape and is driven by the system formations on the one hand side and the SAP Cloud Application Event Hub on the other.

> ### Note:  
> By creating a formation of type *Eventing Between SAP Cloud Systems*, keep in mind that there may be event distribution charges incurred if you exceed the free quota limit when using SAP Cloud Application Event Hub. To learn more about usage and consumption costs, see [Usage and Consumption Costs](https://help.sap.com/docs/event-broker/event-broker-service-guide/usage-and-consumption-costs?version=Cloud).



<a name="loio15922463e5a54538857795316eb4d997__section_h1s_5t2_lcc"/>

## Rules

When creating *Eventing Between SAP Cloud Systems* formations, keep in mind the following rule:

-   Every system can be included in at most one *Eventing Between SAP Cloud Systems* formation.

-   If you register your SAP S/4HANA Cloud system using the *All Communication Scenarios* or *Eventing Between SAP Cloud Systems* communication scenario group when you get the registration token for this SAP S/4HANA Cloud system, the communication scenario `SAP_COM_0892` will be enabled automatically after this SAP S/4HANA Cloud system is added to the formation of type *Eventing Between SAP Cloud Systems* in the *Formations* page. See [Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](register-an-sap-s-4hana-cloud-system-in-a-global-account-in-sap-btp-28171b6.md).




<a name="loio15922463e5a54538857795316eb4d997__section_znb_p1c_dwb"/>

## Prerequisites

-   You are a global account administrator, or you are a system landscape administrator. See [Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md).

-   You have subscribed to the SAP Cloud Application Event Hub application. See [Subscribing to SAP Cloud Application Event Hub Application](https://help.sap.com/docs/SAP_EMKS/19cb7423096b476d940924799c9e8f5a/53f34cca6bf74610836585e6af9b3745.html).




<a name="loio15922463e5a54538857795316eb4d997__section_v4q_p1c_dwb"/>

## Procedure

The following procedure outlines the steps you need to perform to enable the exchange of events across the systems within the system landscape.

1.  In the SAP BTP cockpit, in the *System Landscape* \> *Systems* page of the SAP BTP cockpit, browse the already added systems in your customer system landscape or manually add and register any missing systems.

    The customer landscape features systems that are added to the list in one of the following ways:

    -   *Auto-discovered*

        An auto-discovered system is a system \(associated with the given global account\) that has been discovered and added automatically to the list based on information of the existing system landscape. Any SAP system of the supported system types that is associated with the same customer ID, with which your global account in SAP BTP is associated, will be added automatically in the system landscape list.

    -   *Subaccount/*<my-subaccount\>**

        A subscription in SAP BTP cockpit associated with a given subaccount. The subscription has been discovered and added automatically through the subaccount. Check the value of the *Discovery* column to see the subaccount where your system is subscribed.

    -   *Manually added*

        Specifies that the system has been added to the list manually by the global account administrator, using the *Add System* button and completing the wizard. The system has been associated with the global account in SAP BTP.


    > ### Note:  
    > If a given SAP system is missing on the *Systems* page, it may be associated with a different customer ID on the SAP BTP global account you are working in. In this case, you need to add the system manually, and then, register it.

    > ### Tip:  
    > When you register an SAP S/4HANA Cloud system, you can automate some of the required configuration steps at a later point. To do this, you can use the *All Communication Scenarios* or *Eventing Between SAP Cloud Systems* communication scenario groups when you get the registration token for the SAP S/4HANA Cloud system. This allows the automatic enablement of the communication scenario `SAP_COM_0892` after the corresponding system is added to the formation of type *Eventing Between SAP Cloud Systems*.

    See [Adding, Registering and Deregistering Systems](adding-registering-and-deregistering-systems-2ffdaff.md).

2.  Create a formation of type *Eventing Between SAP Cloud Systems* and include the relevant systems in it.

    1.  Add any name that helps you identify your formation.

    2.  In the *Formation Type* dropdown menu, select *Eventing Between SAP Cloud Systems*.

    3.  Select the systems that you want to include in the formation. One of these systems must be of type *SAP Event Broker*.

        > ### Note:  
        > Systems can only be added to one formation of type *Eventing Between SAP Cloud Systems* in a global account.
        > 
        > Also, a formation of type *Eventing Between SAP Cloud Systems* can contain only one system of type *SAP Event Broker*.

    4.  Review your selections and create the formation.





<a name="loio15922463e5a54538857795316eb4d997__section_bbm_s3m_vvb"/>

## Next Steps

When the formation is created, navigate to the SAP Cloud Application Event Hub application and enable the event subscriptions. See [Enabling SAP Event Subscriptions](https://help.sap.com/docs/event-broker/event-broker-service-guide/enable-subscriptions?version=Cloud).



<a name="loio15922463e5a54538857795316eb4d997__section_lq4_2sr_xyb"/>

## Remove a System from the Formation

If you want to remove an SAP system from a formation of type *Eventing Between SAP Cloud Systems*, make sure that all active event subscriptions are disabled first in SAP Cloud Application Event Hub. You can check your subscriptions in the SAP Cloud Application Event Hub application on the *Subscriptions* page. See [Disabling SAP Event Subscriptions](https://help.sap.com/docs/event-broker/event-broker-service-guide/disable-event-subscriptions?version=Cloud).

