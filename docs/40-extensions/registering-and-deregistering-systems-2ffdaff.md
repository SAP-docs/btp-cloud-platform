<!-- loio2ffdaff0f1454acdb046876045321c91 -->

# Registering and Deregistering Systems

To connect an SAP system with a global account in SAP BTP, you need to register the system. You can also add and work with a third-party systems.



## Prerequisites

-   You are a global account administrator, or you are a system landscape administrator of the global account where you want to register your SAP system. See [Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md).

-   Before adding your system, make sure it's not already auto-discovered and listed automatically in the *System Landscape* \> *Systems* page.




## Registering SAP Systems

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

For some system types, such as SAP SuccessFactors, SAP S/4HANA Cloud, SAP Marketing Cloud and SAP systems from the SAP Customer Experience portfolio, adding a system to the list in the *Systems* page is just the first step of the system registration process. When you have only added a system, the system is not yet registered in the SAP BTP global account. That is, the required configuration on the system side has not been performed, and therefore, the newly added system cannot exchange or expose its technical details, metadata, APIs, or events. Only when the registration process is complete and the system is registered with SAP BTP, it can exchange the relevant information and enable the extension scenario.

If your system is associated with the given global account, this system is discovered and added automatically to the *Systems* page based on information of the existing system landscape. Any SAP system that is associated with the same customer ID, with which your global account in SAP BTP is associated, will be auto-discovered.

> ### Note:  
> If a given SAP system is missing on the *Systems* page, it may be associated with a different customer ID on the SAP BTP global account you are working in. In this case, you need to add the system manually, and then, register it.

> ### Note:  
> You cannot migrate the registered SAP systems between global accounts.
> 
> If you want to start using another global account, you will have to register your SAP systems again.

For systems of type SAP SuccessFactors, SAP S/4HANA Cloud, SAP Marketing Cloud and SAP systems from the SAP Customer Experience portfolio, the registration of the newly added systems is based on a registration token. The registration token is used for the pairing of the system and the corresponding global account. After you add a system, you can get the token in the SAP BTP cockpit. Then, you can use it to configure the integration on the corresponding system side. By using the registration token on the system side and registering the system, the system administrator allows the integration of the system with SAP BTP.

When you add an SAP system of type SAP SuccessFactors, SAP S/4HANA Cloud, SAP Marketing Cloud and SAP systems from the SAP Customer Experience portfolio, it appears in the system landscape list as a record with empty \(or initialized\) status. The system gets a *Registered* status, only when a token is issued and the registration is complete on the corresponding system side. In general, the *Registered* status means that the communication between the system and SAP BTP has been established. However, depending on the system and its requirements, additional configuration might be needed for the enablement of a fully functional extension scenario. The additional configuration, depending on the system type, is outlined in the corresponding documents listed in the *Related Information* section.

> ### Note:  
> When registering SAP systems of the same type, you can have up to 1000 tokens per global account ready to be used. Tokens that are already used to register an SAP system are not included in this number.
> 
> This means that you cannot have more than 1000 systems in the Systems list of the same type with an empty status and generated token that is not used yet.

For system types different than SAP SuccessFactors, SAP S/4HANA Cloud, SAP Marketing Cloud and SAP systems from the SAP Customer Experience portfolio, when adding a system in the *Systems* page, this system is registered directly but no status is displayed.

The registration process has the following states displayed in the cockpit:

-   No status displayed in the *Status* column - the registration token for an SAP system of type SAP SuccessFactors, SAP S/4HANA Cloud, SAP Marketing Cloud or SAP systems from the SAP Customer Experience portfolio has been created but the registration on the respective SAP system side has not been performed or completed yet. For systems with type other than SAP SuccessFactors, SAP S/4HANA Cloud, SAP Marketing Cloud and SAP systems from the SAP Customer Experience portfolio are registered when added to the *Systems* page but no status has been displayed. Only systems that require a registration token to be registered have the status *Registered* when this token has been used.

-   *Registered* - the registration token for systems of type SAP SuccessFactors, SAP S/4HANA Cloud, SAP Marketing Cloud and SAP systems from the SAP Customer Experience portfolio has been used and the automated registration process has been successfully completed. The systems of these types can be assigned to a formation on the *Formations* page in the cockpit. All other system types are registered without a registration token and can be assigned to a formation.
-   *Error while Registering* - the registration has failed.

> ### Note:  
> If a system is in status *Error while Registering*, delete it and register it again.

If the registration error persists, report a case in one of the following components depending on the system type:

-   SAP SuccessFactors - `BC-NEO-EXT-SF`

-   SAP S/4HANA Cloud - `BC-NEO-EXT-S4C`

-   All other system types - `BC-CP-MP`


> ### Note:  
> When registering a system or creating a formation, the data you provide in the given input fields is not encrypted with your customer managed key. The data you enter is only encrypted at rest.



### Procedure

1.  In the cockpit, navigate to your global account, and then choose *System Landscape* \> *Systems*.

2.  On the *Systems* page, choose *Add System*.

    > ### Note:  
    > Before adding your system, make sure it's not already auto-discovered and listed automatically in the *Systems* page. Some of the SAP systems have additional configurations described in dedicated procedures. See:
    > 
    > -   [Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](register-an-sap-s-4hana-cloud-system-in-a-global-account-in-sap-btp-28171b6.md)
    > 
    > -   [Register an SAP Marketing Cloud System in a Global Account in SAP BTP](register-an-sap-marketing-cloud-system-in-a-global-account-in-sap-btp-e9d975a.md)
    > 
    > -   [Register an SAP SuccessFactors System in a Global Account in SAP BTP](register-an-sap-successfactors-system-in-a-global-account-in-sap-btp-e956ba2.md)
    > 
    > -   [Register an SAP Customer Experience System](register-an-sap-customer-experience-system-1582d72.md)

3.  In the *Add System* wizard:

    1.  In the *Type* dropdown list, select the system type.

    2.  Enter a name for the system you want to register.

        > ### Note:  
        > Use only printable ASCII characters.

        > ### Tip:  
        > We recommend that you indicate the type of the system when specifying the system name. For example, <code><i class="varname">&lt;mysystem&gt;</i>-commerce-cloud</code>. This helps you identify the system type when assigning systems to a formation.

    3.  Choose *Add*.

    4.  For systems of type SAP SuccessFactors, SAP S/4HANA Cloud, SAP Marketing Cloud and SAP systems from the SAP Customer Experience portfolio, choose *Get Token*.

        A registration token is generated for this system.

        Systems of type different than SAP SuccessFactors, SAP S/4HANA Cloud and SAP systems from the SAP Customer Experience portfolio don't need a registration token, they are automatically registered when added to the *Systems* page. Their status is empty but you can consider them as registered.

    5.  Copy the registration token. You need the token to complete the integration on the respective SAP solution system side.

    6.  Close the wizard.





### Result

The system has been added as a record to the list on the *Systems* page in the SAP BTP cockpit. For systems of type SAP SuccessFactors, SAP S/4HANA Cloud and SAP systems from the SAP Customer Experience portfolio, a registration token for connecting the corresponding SAP solution with the global account in SAP BTP has been generated. Systems of type other than SAP SuccessFactors, SAP S/4HANA Cloud and SAP systems from the SAP Customer Experience portfolio, are automatically registrated, no additional configurations are required.

> ### Note:  
> Registration tokens have different validity periods that depend on the system type. For more information about token expiry, see the corresponding documentation at the *Related Links* section.



### Next Steps

-   For SAP systems of type SAP SuccessFactors, SAP S/4HANA Cloud, SAP Marketing Cloud and SAP systems from the SAP Customer Experience portfolio, use the registration token to complete the registration on the respective SAP system side. See:

    -   [Trigger the Registration in the SAP S/4HANA Cloud Tenant](trigger-the-registration-in-the-sap-s-4hana-cloud-tenant-cadf8f6.md)

    -   [Trigger the Registration in the SAP Marketing Cloud Tenant](trigger-the-registration-in-the-sap-marketing-cloud-tenant-d7416c3.md)
    -   [Register an SAP SuccessFactors System in a Global Account in SAP BTP](register-an-sap-successfactors-system-in-a-global-account-in-sap-btp-e956ba2.md)
    -   [Register an SAP Customer Experience System](register-an-sap-customer-experience-system-1582d72.md)

-   You can assign the system to a formation on the *Formations* page, as follows:

    -   SAP systems of type *SAP Commerce Cloud*, *SAP Cloud for Customer*, and *SAP Field Service Management* can be assigned to a formation directly before the integration is complete on the respective SAP Customer Experience system side. However, to enable the API access, you first need to complete the integration.

    -   For systems of type *SAP S/4HANA Cloud*, *SAP Marketing Cloud* and *SAP SuccessFactors*, you first need to configure the integration on the respective SAP system side.

    -   For systems of type other than *SAP S/4HANA Cloud*, *SAP Marketing Cloud* and *SAP SuccessFactors* and SAP systems from the SAP Customer Experience portfolio, after adding these systems in the *Systems* list, you can directly include them in a formation.


    See [Automating Integrations Using Formations](automating-integrations-using-formations-68b04fa.md).

-   If you no longer need it, you can deregister or remove the system depending on its status. See [Deregister or Removе a System](deregister-or-remov-a-system-0c6f498.md).




## Registering Third-Party Systems

You add a third-party system to the list in the *System Landscape* \> *Systems* page. At this point you provide all the required details for this system: its type, provider, URL, and system ID. For third-party systems, this completes the registration process and you have your third-party system registered with SAP BTP. Even though the third-party system is registered directly, no status is displayed.

See [Register a Third-Party System](register-a-third-party-system-5481d59.md).



<a name="loio2ffdaff0f1454acdb046876045321c91__section_nvz_2cy_mdc"/>

## Deregistering Systems

Deregistering an SAP or third-party system means that the connectivity between this system and the global account is disabled and extension scenarios cannot be established, while removing a system means that this system is no longer part of the system landscape list. You can deregister or remove a system from the *Actions* column, or from the *System Details* page that you access when selecting the system from the system landscape list.

See [Deregister or Removе a System](deregister-or-remov-a-system-0c6f498.md).



<a name="loio2ffdaff0f1454acdb046876045321c91__section_ghh_m5c_ndc"/>

## Merging Systems

If you have already added these systems manually at a given point in time and you have registered them, the auto-discovered systems might create duplicate entries in the list. To avoid duplicates and streamline the list of systems, you can merge automatically the auto-discovered SAP systems with your manually added systems.

See [Mergе SAP Systems](merg-sap-systems-5592d86.md).

**Related Information**  


[Extending SAP S/4HANA Cloud in the Cloud Foundry and Kyma Environment](extending-sap-s-4hana-cloud-in-the-cloud-foundry-and-kyma-environment-40b9e6c.md "Extend SAP S/4HANA Cloud with extension applications running on SAP BTP using automated integration configuration.")

[Extending SAP Marketing Cloud in the Cloud Foundry and Kyma Environment](extending-sap-marketing-cloud-in-the-cloud-foundry-and-kyma-environment-18bb3d9.md "")

[Extending SAP SuccessFactors in the Cloud Foundry and Kyma Environment](extending-sap-successfactors-in-the-cloud-foundry-and-kyma-environment-9e33934.md "Use SAP BTP to extend SAP SuccessFactors with extension applications running on the cloud platform.")

[Extending SAP Customer Experience Products in the Kyma Environment](extending-sap-customer-experience-products-in-the-kyma-environment-83df31a.md "You can configure the integration between SAP BTP and SAP Customer Experience automatically to extend SAP Customer Experience products with applications running on the cloud platform.")

[Register an SAP Integrated Business Planning System in a Global Account in SAP BTP](register-an-sap-integrated-business-planning-system-in-a-global-account-in-sap-btp-be85ce0.md "To connect an SAP Integrated Business Planning system with a global account in SAP BTP, you need to register the system in the corresponding global account.")

[Register a Third-Party System](register-a-third-party-system-5481d59.md "To connect a third-party systems, for example a Google system, with a global account in SAP BTP, you first need to add this system to the Systems page.")

