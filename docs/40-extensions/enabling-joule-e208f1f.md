<!-- loioe208f1fe75b748cb953b9e9db4b91bec -->

# Enabling Joule



<a name="loioe208f1fe75b748cb953b9e9db4b91bec__section_kbh_41c_dwb"/>

## Use

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

Leveraging its generative AI capabilities, Joule aims to understand your requests, retrieve information, and complete your tasks in a conversational way. You can describe the current task to Joule, who can help automate tasks or take you to places where you can find desired data. By using Joule, you can easily interact with the system and increase your productivity.

To use Joule in SAP systems, you have to integrate these systems with Joule. To do that, you have to include the SAP systems in a formation of type *Integration with Joule* on the *System Landscape* \> *Formations* page of the SAP BTP cockpit. The integration is between the Joule system and every SAP system in the formation, but not between each and every SAP system.

To see which SAP systems are supported, see [Joule Capabilities](https://help.sap.com/docs/JOULE/cfbd4200de484c19ab9b1333acaeb44e/41de8c499c72413c8e134493686a5348.html).



<a name="loioe208f1fe75b748cb953b9e9db4b91bec__section_h1s_5t2_lcc"/>

## Rules

When creating *Integration with Joule* formations, keep in mind the following rules:

-   At most one system of type *Joule* can be included in one *Integration with Joule* formation.

-   A system of type *Joule* can be included in at most one *Integration with Joule* formation.

-   Applicable to systems of type SAP Integrated Business Planning: you can include these systems in a formation of type *Integration with Joule* only if they are registered using the *All Communication Scenarios* communication scenario group. See [Register an SAP Integrated Business Planning System in a Global Account in SAP BTP](register-an-sap-integrated-business-planning-system-in-a-global-account-in-sap-btp-be85ce0.md).

-   Applicable to systems of type SAP SuccessFactors: you can include these systems in a formation of type *Integration with Joule* only after they have been registered. See [Register an SAP SuccessFactors System in a Global Account in SAP BTP](register-an-sap-successfactors-system-in-a-global-account-in-sap-btp-e956ba2.md).

-   Applicable to systems of type SAP S/4HANA Cloud: you can include these systems in a formation of type *Integration with Joule* only if they are registered using the *All Communication Scenarios* communication scenario group. See [Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](register-an-sap-s-4hana-cloud-system-in-a-global-account-in-sap-btp-28171b6.md).

    > ### Note:  
    > This documentation refers to SAP S/4HANA Cloud Public Edition. See [Introduction to the Universe of SAP S/4HANA Cloud Public Edition](https://help.sap.com/docs/SAP_S4HANA_CLOUD/f77dde055ecb4541b57787d362c46a36/2962fce53eef47b4b3a8e6c945adafbe.html).




<a name="loioe208f1fe75b748cb953b9e9db4b91bec__section_znb_p1c_dwb"/>

## Prerequisites

-   You are a global account administrator, or you are a system landscape administrator. See [Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md).

-   You have a Joule system and at least one other system of the supported types that fulfil the rules in the *Systems* page. The Joule system is auto-discovered.




<a name="loioe208f1fe75b748cb953b9e9db4b91bec__section_v4q_p1c_dwb"/>

## Procedure

The following procedure outlines the steps you need to perform to enable the integration between Joule and SAP systems.

As an alternative to the steps that follow, you can use the *Setting Up Joule* booster in the SAP BTP cockpit and have the end-to-end scenario set up. See [Run the Joule Booster](https://help.sap.com/docs/JOULE/6189c8655c484916bb8eb767126a653a/34157c476600476cb9180062db6002af.html?version=CLOUD).

> ### Note:  
> We recommend that you use the *Setting Up Joule* booster.

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

    See [Registering and Deregistering Systems](registering-and-deregistering-systems-2ffdaff.md).

2.  Create a formation of type *Integration with Joule* and include the relevant systems in it.

    1.  Add any name that helps you identify your formation.

    2.  In the *Formation Type* dropdown menu, select *Integration with Joule*.

    3.  Select the systems that you want to include in the formation. One of these systems must be of type *Joule*.

        > ### Note:  
        > Systems can only be added to one formation of type *Integration with Joule* in a global account.
        > 
        > Also, a formation of type *Integration with Joule* can contain only one system of type *Joule*.

    4.  Review your selections and create the formation.





<a name="loioe208f1fe75b748cb953b9e9db4b91bec__section_bbm_s3m_vvb"/>

## Next Steps

The next steps of the different SAP solutions interated with Joule are listed at [Integrating Joule with SAP Solutions](https://help.sap.com/docs/JOULE/a566dd86443f447aadfb5dfd9e1b7acc/702f3db8996a4a5bbceb6abd33c3ec69.html).

