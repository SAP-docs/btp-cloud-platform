<!-- loio3ce5e05f7a1c48ebbad828c8f5d1c8d7 -->

# Extensibility Concepts

When implementing your extensibility scenario, there are a couple of concepts you need to understand to be able to benefit from the functionality that SAP BTP offers.



<a name="loio3ce5e05f7a1c48ebbad828c8f5d1c8d7__section_g41_vgk_qwb"/>

## Systems

A system is a specific instance of an SAP or third-party solution that is manually added or auto discovered and is listed in the SAP BTP cockpit.

When you want to add functionality to your SAP or third-party solution, you start by developing an extension application and deploying it in SAP BTP. Then, to allow the application to access the SAP or third-party solution, you add the system of this solution to the *System Landscape* page of the SAP BTP cockpit and you register it. The following system types are supported:

-   SAP S/4HANA Cloud

-   SAP Marketing Cloud

-   SAP SuccessFactors

-   SAP Cloud for Customer

-   SAP Commerce Cloud

-   SAP Field Service Management

-   Other System Type




### System Details

**Status**

The registration process can have the following status values:

-   No status

    The system has been added as a record to the list. You can get a registration token for it. However, the registration process on the corresponding solution's system side has not been performed or completed yet.

-   *Registered*

    The registration token has been used and the automated registration process has been completed successfully. Connectivity to the system has been established and it can be used in extension business scenarios.

-   *Error while Registering*

    The registration has failed.

-   *Deregistering*

    A deregistration process has started. As a result, the connectivity between the system and SAP BTP is disabled and extension scenarios cannot be established. The system remains in the system landscape list and you can register it again later on.

-   *Error while Deregistering*

    The deregistration has failed.

-   *Removing*

    A system removal process has started in the SAP BTP cockpit. You can remove a system from the list only when this system has been deregistered. Then, you can remove the system from the *Systems* list completely. To register the system again, first, you must add it to the list anew, and then, initiate the registration procedure.

-   *Error while Removing*

    The system removal has failed.


**Consumption Bundles, APIs, and Events**

Consumption bundles group logically APIs and events intended for communication with the SAP or third-party system. This grouping means that the consumption of the APIs or the events can happen by using the same set of credentials later on. When you register a system, you can also preview the number and the content of consumption bundles that are exposed for communication with the given system.

After you add your third-party systems, you can specify the set of APIs and events in consumption bundles. A consumption bundle organizes a set of related APIs and events into a single group for consumption purposes and expresses information about how the APIs and events that it contains can be accessed. All APIs and events that are part of the same consumption bundle need to be accessible through the same set of credentials. You add the consumption bundles in *System Details* of the respective third-party system.

You can explore the consumption bundles, the APIs, and the events configured for your system in *System Details*. To do that, go to the respective tab: *Consumption Bundles*, *APIs*, or *Events*.

**URL**

You can use the URL as an entry point to the corresponding system. Optionally, you can use it to identify duplicate systems added to the list.



### Discovery Mechanisms

There are different ways to add systems to the *System Landscape* page in the SAP BTP cockpit: manually or automatically. If a system of your solution is associated with your global account or through a subscription in SAP BTP cockpit associated with a given subaccount, it will appear in the list automatically. Otherwise, you have to add your system manually. Systems are added to the list in one of the following ways:

**Auto-Discovered**

An auto-discovered system is a system \(associated with the given global account\) that has been discovered and added automatically to the list based on information of the existing system landscape. Any SAP system of the supported system types that is associated with the same customer ID, with which your global account in SAP BTP is associated, will be added automatically in the system landscape list.

> ### Note:  
> If a given SAP system is missing on the *System Landscape* page, it may be associated with a different customer ID on the SAP BTP global account you are working in. In this case, you need to add the system manually, and then, register it.

**Subaccount/<my-subaccount\>**

Specifies that the system has been added through a subscription in SAP BTP cockpit associated with a given subaccount. The subscription has been discovered and added automatically through the subaccount.

**Manually-Added**

Specifies that the system has been added to the list manually by the global account administrator, using the *Add System* button and completing the wizard. The system has been associated with the global account in SAP BTP.

**Business Type**

When you have an auto-discovered SAP system, you can find information in the respective system details whether this system is used for test or production purposes for example. This information is loaded automatically and is presented in the *Business Type* field.



### Actions

These are the things you can do with a system:

**Adding**

Adding a system to the list in the *System Landscape* page is just the first step of the system registration process. When you have only added a system, the system is not yet registered in the global account in SAP BTP. It appears in the system landscape list as a record with empty \(or initialized\) status. That is, the required configuration on the system side has not been performed, and therefore, the newly added system cannot exchange or expose its technical details, metadata, APIs, or events. Only when the registration process is complete and the system is registered with SAP BTP, it can exchange the relevant information and enable the extension scenario.

**Registering**

When registering a system, the required configuration on the system side has been performed, and therefore, the newly added system can exchange or expose its technical details, metadata, APIs, or events. Only when the registration process is complete and the system is registered with SAP BTP, it can exchange the relevant information and enable the extension scenario.

The registration of the newly added systems is based on a registration token. The token is used for the pairing of the system and the corresponding global account. After you add a system, you can get the token in the SAP BTP cockpit. Then, you can use it to configure the integration on the corresponding system side. By using the registration token on the system side and registering the system, the system administrator allows the integration of the system with SAP BTP.

The system gets a *Registered* status, only when a token is issued and the registration is complete on the corresponding system side. In general, the *Registered* status means that the communication between the system and SAP BTP has been established. However, depending on the system and its requirements, additional configuration might be needed for the enablement of a fully functional extension scenario. The additional configuration, depending on the system type, is outlined in the corresponding documents listed in the *Related Information* section. See [Registering an SAP System](registering-an-sap-system-2ffdaff.md).

**Specifics When Registering SAP S/4HANA Cloud Systems**

When you register an SAP S/4HANA Cloud system, you can automate some of the required configuration steps at a later point using communication scenario groups. The communication scenario groups are entities that are part of the registration token that you use to register your SAP S/4HANA Cloud systems and are associated with one or more communication scenarios in SAP S/4HANA Cloud.

For example, you can use the Event Mesh communication scenario group when you get the registration token for the SAP S/4HANA Cloud system. This allows the automatic enablement of the communication scenario `SAP_COM_0892` after the corresponding system is added to the formation of type *Eventing Between SAP Cloud Systems*.

You can configure the communication scenario groups when registering an SAP S/4HANA Cloud system in the SAP BTP cockpit, in *System Landscape* \> *Systems*. See [Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](register-an-sap-s-4hana-cloud-system-in-a-global-account-in-sap-btp-28171b6.md).

**Merging**

You have added your SAP systems manually at a given point in time and you have registered them. Then, you notice that you have the exact same systems in the list in the *Systems* page only this time they are auto-discovered and are not registered. To avoid duplicates and streamline the list of systems, you can merge the auto-discovered SAP systems with your manually added systems. The logic automatically detects duplicates based on their URL and system type. Note that you can only merge auto-discovered SAP systems without assigned status in a target system that has already been registered. That is, you cannot merge registered auto-discovered systems. See [Merging SAP Systems](merging-sap-systems-5592d86.md).

**Deregistering**

Deregistering a system means that the connectivity between this system and the global account is disabled and extension scenarios cannot be established. You can deregister a system from the *Actions* column, or from the *System Details* page that you access when selecting the system from the *System* list. See [Deregistering or Removing a System](deregistering-or-removing-a-system-0c6f498.md).

**Removing**

Removing a system means that this system is no longer part of the system landscape list. To remove a system from the list, first you have to deregister it. You can remove a system from the *Actions* column, or from the *System Details* page that you access when selecting the system from the *System* list. See [Deregistering or Removing a System](deregistering-or-removing-a-system-0c6f498.md).

You can see the discovery mechanism and access all the actions related to the systems listed in the SAP BTP cockpit, in *System Landscape* \> *Systems*. See [Registering an SAP System](registering-an-sap-system-2ffdaff.md).



<a name="loio3ce5e05f7a1c48ebbad828c8f5d1c8d7__section_rs4_f4r_qwb"/>

## Formations

A formation is a logical grouping of SAP or third-party systems that can be extended in a business scenario. Formations allow you to combine SAP or third-party solution systems and a subaccount in SAP BTP to simplify the connectivity setup and to provide a unified view of all components required for the implementation of your extension scenario. To create a fully functional formation, you can use a two-step wizard. At the first step, you specify a custom formation name and assign a subaccount to it. At the second step, you can include an SAP or third-party solution system in the formation. You do this configuration once and you can change it anytime.

> ### Note:  
> You can assign a subaccount to the formation during the formation creation only. While you can include or exclude systems in the formation anytime, you cannot unassign or reassign subaccounts later on. Instead, you must recreate the formation.

Extension business cases often involve extending several SAP or third-party solutions at a time. For example, for a given business case you might need to extend the functionality or the UI as follows:

-   An SAP SuccessFactors system, and an SAP S/4HANA Cloud system. First, you need to configure the connectivity of each of these systems to Cloud Foundry, Kyma, or both environments. Extension applications of both solutions are part of the same business need.

-   An SAP Commerce Cloud system, and an SAP S/4HANA Cloud system. Again, you first configure the connectivity of each of these systems to the Kyma environment.

-   A single system of the supported SAP or third-party solutions.

-   SAP or third-party systems that expose event data, which can be shared and exchanged with the systems included in the formation.


When creating a formation in the SAP BTP cockpit, you include the systems of the different SAP or third-party solutions you want to extend. If your business case features more than one system, you can use the corresponding button to include additional systems in the formation. You can start the dialog as many times and add systems to your formation as you want.



### Systems Details in a Formation

**Consumption Bundle APIs**

A consumption bundle can group logically a set of APIs for communication with the SAP or third-party system.

**Consumption Bundle Events**

A consumption bundle can group logically a set of events for communication with the SAP or third-party system.



### Types

The formation type defines the use case. Therefore, depending on the use case, you can specify one of the following formation types:

**Side-by-Side Extensibility with Kyma**

Formations of type *Side-by-Side Extensibility with Kyma* enable business scenarios that involve extending the functionality of several systems at a time with SAP BTP Kyma environment instance. See [Enabling Side-by-Side Extensibility with Kyma](enabling-side-by-side-extensibility-with-kyma-9154051.md).

**Eventing Between SAP Cloud Systems**

Systems that are included in *Eventing Between SAP Cloud Systems* formations on the *System Landscape* page of the SAP BTP cockpit can publish and consume events. The process of publishing and consumption of events is in fact an exchange of event information across the customer system landscape and is driven by the system formations on the one hand side and the SAP Event Broker on the other.

**Developing with SAP Business Application Studio**

Formations of type *Developing with SAP Business Application Studio* enable connectivity between given SAP systems of type *SAP S/4HANA Cloud* from the *System Landscape* page of SAP BTP cockpit and the SAP Business Application Studio, you must create a formation of the corresponding type and include the SAP S/4HANA Cloud systems in it. See [Enabling System Landscape for SAP Business Application Studio](enabling-system-landscape-for-sap-business-application-studio-272ca23.md).



### Formation Status

A formation can have the following status values:

-   No status

-   *Action Required*

    The formation has been created but you cannot use it productively yet.

    Based on the formation type and the subaccount that you specified, it might require an SAP BTP Kyma environment instance or an SAP Business Application Studio subscription. Although the SAP BTP cockpit allows you to create such a formation, to enable and make use of it, you must also create the respective instance or subscription.

-   *Synchronizing*

    Systems that are included in the formation are currently synchronizing in the background.

-   *Error*

    An error occurred while some of the systems that are included in the formation were synchronizing in the background.




### Actions

**Creating Formations**

Create a logical grouping of the systems that you want to extend.

**Including/Excluding Systems in a Formation**

Include additional systems to a given formation or exclude already included systems from a formation.

If your business case features more than one system, you can include additional systems in the formation. You can include as many systems as you want to your formation.

**Resynchronizing Systems in a Formation**

When you include systems in a formation, these systems are synchronized in the background. If an error occurs, you can resynchronize these systems to restart the synchronization process. To do that, choose *Resynchronize* for the particular formation. You will have this action available only for formations that are in status *Error*.

**Reseting and Resynchronizing Systems in a Formation**

If you want to reconfigure the systems in a formation from scratch without excluding them, you have to choose *Reset and Resynchronize*. You will have this action available only for formations that have no status in SAP BTP cockpit their formation type is Side-by-Side Extensibility with Kyma.

**Deleting Formations**

Detach the systems, unassign the subaccount, and delete the formation at one go.

When you start a formation deletion process, first the systems are excluded from the formation, then, the subaccount is unassigned, and last, the formation is deleted from the list completely.

You can create and configure formations in the SAP BTP cockpit, in *System Landscape* \> *Formations*. See [Including Systems in a Formation](including-systems-in-a-formation-68b04fa.md).

