<!-- loio37a896bfac604076ae825a1d37b0bd0a -->

# Setup of UI Development in SAP Business Application Studio \(Optional\)

If developers want to use SAP Business Application Studio to create and deploy SAP Fiori application UIs, you need to perform some administrative activities to set it up.

In the Cloud Foundry environment, SAP Business Application Studio is a service that provides a modular development environment, including the development of SAP Fiori applications. As an alternative to SAP Business Application Studio, you can also use SAP Web IDE. We recommend that you use SAP Business Application Studio.



<a name="loio37a896bfac604076ae825a1d37b0bd0a__section_bbn_q4x_4mb"/>

## Prerequisites

For setting up SAP Business Application Studio, you need the following:

-   You are a member of the global account.
-   You are an organization manager in your Cloud Foundry subaccount \(see also [Adding a User as Org Manager for the Cloud Foundry Organization](Adding_a_User_as_Org_Manager_for_the_Cloud_Foundry_Organization_57059dc.md)\).
-   You have created an ABAP service instance \(see also [Creating an ABAP System](Creating_an_ABAP_System_50b32f1.md)\).
-   You are a security administrator. If you have created a subaccount for the ABAP environment in the Cloud Foundry environment, your user automatically has the security administration role.



<a name="loio37a896bfac604076ae825a1d37b0bd0a__section_qvb_tht_r4b"/>

## Setting Up SAP Business Application Studio

> ### Note:  
> If you have run the booster *Prepare an Account for ABAP Development*, you can skip the first two steps.

![](images/Image_Map_Setup_of_Business_Application_Studio_67fdfeb.png)

-   [Subscribing to SAP Business Application Studio](Subscribing_to_SAP_Business_Application_Studio_0a9b42e.md)
-   [Assigning Permissions for SAP Business Application Studio](Assigning_Permissions_for_SAP_Business_Application_Studio_a08c1cb.md)
-   [Creating a Service Key for the ABAP System](Creating_a_Service_Key_for_the_ABAP_System_7af8259.md)
-   [Creating a Destination to the ABAP System for SAP Business Application Studio](Creating_a_Destination_to_the_ABAP_System_for_SAP_Business_Application_Studio_e597948.md)

1.  To enable the creation and deployment of SAP Fiori application UIs, subscribe to SAP Business Application Studio in the same subaccount in which you've created your ABAP service instance \(see [Subscribing to SAP Business Application Studio](Subscribing_to_SAP_Business_Application_Studio_0a9b42e.md)\).
2.  To allow developers to develop applications using SAP Business Application Studio, assign developers to the `Business_Application_Studio_Developer` role collection \(see [Assigning Permissions for SAP Business Application Studio](Assigning_Permissions_for_SAP_Business_Application_Studio_a08c1cb.md)\).
3.  Create a service key for your ABAP system, which you will need to set up a service destination \(see [Creating a Service Key for the ABAP System](Creating_a_Service_Key_for_the_ABAP_System_7af8259.md)\).
4.  To connect your ABAP system with SAP Business Application Studio, set up a destination in the same subaccount in which you have subscribed to SAP Business Application Studio \(see [Creating a Destination to the ABAP System for SAP Business Application Studio](Creating_a_Destination_to_the_ABAP_System_for_SAP_Business_Application_Studio_e597948.md)\).

-   **[Subscribing to SAP Business Application Studio](Subscribing_to_SAP_Business_Application_Studio_0a9b42e.md "If developers want to use SAP Business Application Studio as development environment for UIs, you need to subscribe to SAP Business
		Application Studio in your subaccount.")**  
If developers want to use SAP Business Application Studio as development environment for UIs, you need to subscribe to SAP Business Application Studio in your subaccount.
-   **[Assigning Permissions for SAP Business Application Studio](Assigning_Permissions_for_SAP_Business_Application_Studio_a08c1cb.md "Use the available role collection  Business_Application_Studio_Developer to assign the relevant
		permissions to your developers to work in SAP Business Application Studio.")**  
Use the available role collection `Business_Application_Studio_Developer` to assign the relevant permissions to your developers to work in SAP Business Application Studio.
-   **[Creating a Service Key for the ABAP System](Creating_a_Service_Key_for_the_ABAP_System_7af8259.md "Create a service key for the ABAP system, which will later be needed to configure a destination from SAP Business Application Studio to
		the ABAP system.")**  
Create a service key for the ABAP system, which will later be needed to configure a destination from SAP Business Application Studio to the ABAP system.
-   **[Creating a Destination to the ABAP System for SAP Business Application Studio](Creating_a_Destination_to_the_ABAP_System_for_SAP_Business_Application_Studio_e597948.md "")**  


