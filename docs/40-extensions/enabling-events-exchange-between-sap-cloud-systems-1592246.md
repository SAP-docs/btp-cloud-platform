<!-- loio15922463e5a54538857795316eb4d997 -->

# Enabling Events Exchange Between SAP Cloud Systems



<a name="loio15922463e5a54538857795316eb4d997__section_kbh_41c_dwb"/>

## Use

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

Systems that are included in *Eventing Between SAP Cloud Systems* formations on the *System Landscape* page of the SAP BTP cockpit can publish and consume events. The process of publishing and consumption of events is in fact an exchange of event information across the customer system landscape and is driven by the system formations on the one hand side and the SAP Event Broker on the other.

The following procedure outlines the steps you need to perform to enable the exchange of events across the systems within the system landscape.



<a name="loio15922463e5a54538857795316eb4d997__section_znb_p1c_dwb"/>

## Prerequisites

You have subscribed to SAP Event Broker application.

See [Subscribing to SAP Event Broker Application](https://help.sap.com/docs/SAP_EMKS/19cb7423096b476d940924799c9e8f5a/53f34cca6bf74610836585e6af9b3745.html).



<a name="loio15922463e5a54538857795316eb4d997__section_v4q_p1c_dwb"/>

## Procedure

1.  Browse the already added systems in your customer system landscape or manually add and register any missing systems.

    The customer landscape features systems that are added to the list in one of the following ways:

    -   *Auto-discovered*

        An auto-discovered system is a system \(associated with the given global account\) that has been discovered and added automatically to the list based on information of the existing system landscape. Any SAP system of the supported system types that is associated with the same customer ID, with which your global account in SAP BTP is associated, will be added automatically in the system landscape list.

    -   *Subaccount/*<my-subaccount\>**

        A subscription in SAP BTP cockpit associated with a given subaccount. The subscription has been discovered and added automatically through the subaccount.

    -   *Manually added*

        Specifies that the system has been added to the list manually by the global account administrator, using the *Add System* button and completing the wizard. The system has been associated with the global account in SAP BTP.


    > ### Note:  
    > If a given SAP system is missing on the *System Landscape* page, it may be associated with a different customer ID on the SAP BTP global account you are working in. In this case, you need to add the system manually, and then, register it.

    See [Registering an SAP System](registering-an-sap-system-2ffdaff.md).

2.  Create a formation of type *Eventing Between SAP Cloud Systems* and include the relevant systems in it.

    To enable events exchange between the systems in your system landscape via SAP Event Broker, these systems must be grouped logically together and associated with the subaccount in SAP BTP. The grouping of systems into an eventing formation defines the use case with these systems and denotes that they can share events as part of the formation.

    See [Including Systems in a Formation](including-systems-in-a-formation-68b04fa.md).




<a name="loio15922463e5a54538857795316eb4d997__section_bbm_s3m_vvb"/>

## Next Steps

When the formation is prepared, navigate to the SAP Event Broker UI and enable the event subscriptions.

See [Enabling SAP Event Subscriptions](https://help.sap.com/docs/SAP_EMKS/19cb7423096b476d940924799c9e8f5a/e0b4046096524301ba1d738909368b9f.html).

