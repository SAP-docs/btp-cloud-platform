<!-- loiodf5b424cbf9640aabaa5566d8bf14cc7 -->

# Automating Integrations with SAP Task Center



<a name="loiodf5b424cbf9640aabaa5566d8bf14cc7__section_kbh_41c_dwb"/>

## Use

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

SAP Task Center helps you integrate tasks into a central solution. The SAP Task Center service enables integration with SAP and non-SAP applications to provide a single entry point for end users to access all their assigned tasks. For example, you can work with task from SAP S/4HANA Cloud Public Edition on SAP BTP, Cloud Foundry runtime. See [What Is SAP Task Center?](https://help.sap.com/docs/task-center/sap-task-center/what-is-sap-task-center?version=Cloud).

To set up SAP Task Center with SAP S/4HANA Cloud on SAP BTP you need to have all the necessary systems included in a formation of type *Integration with SAP Task Center* in the *System Landscape* \> *Systems* page of the SAP BTP cockpit.

> ### Note:  
> This documentation refers to SAP S/4HANA Cloud Public Edition. See [Introduction to the Universe of SAP S/4HANA Cloud Public Edition](https://help.sap.com/docs/SAP_S4HANA_CLOUD/f77dde055ecb4541b57787d362c46a36/2962fce53eef47b4b3a8e6c945adafbe.html).



<a name="loiodf5b424cbf9640aabaa5566d8bf14cc7__section_scq_jxk_lcc"/>

## Rules

When creating *Integration with SAP Task Center* formations, keep in mind the following rules:

-   SAP Task Center system can be included in at most one *Integration with SAP Task Center* formation.

-   At most one SAP Task Center system can be included in an *Integration with SAP Task Center* formation.

-   Only SAP S/4HANA Cloud systems that are registered with *All Communication Scenarios* communication scenario group can be part of a *Integration with SAP Task Center* formation. See [Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](register-an-sap-s-4hana-cloud-system-in-a-global-account-in-sap-btp-28171b6.md).




<a name="loiodf5b424cbf9640aabaa5566d8bf14cc7__section_znb_p1c_dwb"/>

## Prerequisites

-   You are a global account administrator, or you are a system landscape administrator. See [Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md).

-   Check that you have a system of type *SAP S/4HANA Cloud* in the *Systems* list in the *Systems* page. This system is auto-discovered because it is associated with your global account and has been discovered and added automatically to the list based on information of the existing system landscape.

    > ### Note:  
    > If you don't find your system of type *SAP S/4HANA Cloud* in the *Systems* list, add this system manually. See [Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](register-an-sap-s-4hana-cloud-system-in-a-global-account-in-sap-btp-28171b6.md).

-   Register the SAP S/4HANA Cloud system in the *Systems* list in the *System Landscape* page.

    When you register an SAP S/4HANA Cloud system, use the *All Communication Scenarios* communication scenario group when you get the registration token for the SAP S/4HANA Cloud system. This allows the automatic enablement of the communication scenario `SAP_COM_0501` after the corresponding system is added to the formation of type *Integration with SAP Task Center*.

    See [Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](register-an-sap-s-4hana-cloud-system-in-a-global-account-in-sap-btp-28171b6.md).




<a name="loiodf5b424cbf9640aabaa5566d8bf14cc7__section_v4q_p1c_dwb"/>

## Procedure

If you have SAP Task Center set up in your subaccount in SAP BTP, follow these steps to configure the integration between SAP Task Center and SAP S/4HANA Cloud using a formation of type *Integration with SAP Task Center*.

1.  In the SAP BTP cockpit, in the *Systems* page, find the systems of type *SAP Task Center* and *SAP S/4HANA Cloud* that you want to include in a formation.

    The *SAP Task Center* system you are going to include in this formation must not be part of another formation of type *Integration with SAP Task Center*.

2.  In the *System Landscape* \> *Formations* page, create a formation of type *Integration with SAP Task Center* and include the relevant systems in it.

    1.  Add any name that helps you identify your formation.

    2.  In the *Formation Type* dropdown menu, select *Integration with SAP Task Center*.

    3.  Select the *SAP Task Center* and *SAP S/4HANA Cloud* systems that you want to include in the formation.

    4.  Review your selections and create the formation.





<a name="loiodf5b424cbf9640aabaa5566d8bf14cc7__section_bbm_s3m_vvb"/>

## Next Steps

You have set up the connection to SAP Task Center and can receive SAP S/4HANA Cloud Public Edition tasks in the SAP Task Center Web app. For more information on the Web app, see [SAP Task Center Web App](https://help.sap.com/docs/task-center/sap-task-center/sap-task-center-web-app?version=Cloud).

