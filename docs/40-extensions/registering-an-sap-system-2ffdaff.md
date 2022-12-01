<!-- loio2ffdaff0f1454acdb046876045321c91 -->

# Registering an SAP System

To connect an SAP system with a global account in SAP BTP, you first need to register the system.



<a name="loio2ffdaff0f1454acdb046876045321c91__prereq_l4m_s5b_fhb"/>

## Prerequisites

You are a global account administrator, or you are a system landscape administrator of the global account where you want to register your SAP system. See [Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md).



<a name="loio2ffdaff0f1454acdb046876045321c91__context_ihl_j3h_jlb"/>

## Context

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

Adding a system to the list in the *System Landscape* page is just the first step of the system registration process. When you have only added a system, the system is not yet registered in the SAP BTP global account. That is, the required configuration on the system side has not been performed, and therefore, the newly added system cannot exchange or expose its technical details, metadata, APIs, or events. Only when the registration process is complete and the system is registered with SAP BTP, it can exchange the relevant information and enable the extension scenario.

> ### Note:  
> You cannot migrate the registered SAP systems between global accounts.
> 
> If you want to start using another global account, you will have to register your SAP systems again.

The registration of the newly added systems is based on a registration token. The token is used for the pairing of the system and the corresponding global account. After you add a system, you can get the token in the SAP BTP cockpit. Then, you can use it to configure the integration on the corresponding system side. By using the registration token on the system side and registering the system, the system administrator allows the integration of the system with SAP BTP.

When you add a system, it appears in the system landscape list as a record with empty \(or initialized\) status. The system gets a *Registered* status, only when a token is issued and the registration is complete on the corresponding system side. In general, the *Registered* status means that the communication between the system and SAP BTP has been established. However, depending on the system and its requirements, additional configuration might be needed for the enablement of a fully functional extension scenario. The additional configuration, depending on the system type, is outlined in the corresponding documents listed in the *Related Information* section.

> ### Note:  
> When registering SAP systems of the same type, you can have up to 1000 tokens per global account ready to be used. Tokens that are already used to register an SAP system are not included in this number.
> 
> This means that you cannot have more than 1000 systems in the Systems list of the same type with an empty status and generated token that is not used yet.

The following SAP system types are supported:

-   SAP S/4HANA Cloud \(available for Cloud Foundry and Kyma environment\)

-   SAP Marketing Cloud \(available for Cloud Foundry and Kyma environment\)

-   SAP SuccessFactors \(available for Cloud Foundry and Kyma environment\)

-   SAP Commerce Cloud \(available for Kyma environment\)

-   SAP Cloud for Customer \(available for Kyma environment\)

-   SAP Field Service Management \(available for Kyma environment\)


The registration process has the following states displayed in the cockpit:

-   No status displayed in the *Status* column - the registration token for an SAP system has been created but the registration on the respective SAP system side has not been performed or completed yet.

-   *Registered* - the registration token has been used and the automated registration process has been successfully completed. The system can be assigned to a formation on the *Formations* page in the cockpit.
-   *Error while Registering* - the registration has failed.

> ### Note:  
> You will not be able to deregister or remove a system if its status is *Error while Registering*.

If the registration error persists, report an incident in one of the following components depending on the system type:

-   SAP SuccessFactors - `BC-NEO-EXT-SF`

-   SAP S/4HANA Cloud - `BC-NEO-EXT-S4C`

-   All other system types - `BC-CP-MP`


> ### Note:  
> When registering a system or creating a formation, the data you provide in the given input fields is not encrypted with your customer managed key. The data you enter is only encrypted at rest.



## Procedure

1.  In the cockpit, navigate to your global account, and then choose *System Landscape* \> *Systems* .

2.  On the *Systems* page, choose *Add System*.

3.  In the *Add System* wizard:

    1.  Enter a name for the system you want to register.

        > ### Note:  
        > Use only printable ASCII characters.

        > ### Tip:  
        > We recommend that you indicate the type of the system when specifying the system name. For example, ****<mysystem\>*-commerce-cloud***. This helps you identify the system type when assigning systems to a formation.

    2.  In the *Type* dropdown list, select the system type.

    3.  Choose *Add*.

    4.  Choose *Get Token*.

        The system generates the registration token.

    5.  Copy the registration token. You need the token to complete the integration on the respective SAP solution system side.

    6.  Close the wizard.





<a name="loio2ffdaff0f1454acdb046876045321c91__result_ytq_hrh_jlb"/>

## Results

-   The system has been added as a record to the list on the *Systems* page in the SAP BTP cockpit and a token for connecting the corresponding SAP solution with the global account in SAP BTP has been generated.

    > ### Note:  
    > Registration tokens have different validity periods that depend on the system type. For more information about token expiry, see the corresponding documentation at the *Related Links* section.




<a name="loio2ffdaff0f1454acdb046876045321c91__postreq_e5y_rxz_klb"/>

## Next Steps

-   Use the registration token to complete the registration on the respective SAP system side. See:

    -   [Trigger the Registration in the SAP S/4HANA Cloud Tenant](trigger-the-registration-in-the-sap-s-4hana-cloud-tenant-cadf8f6.md)

    -   [Trigger the Registration in the SAP Marketing Cloud Tenant](trigger-the-registration-in-the-sap-marketing-cloud-tenant-d7416c3.md)
    -   [Register an SAP SuccessFactors System in a Global Account in SAP BTP](register-an-sap-successfactors-system-in-a-global-account-in-sap-btp-e956ba2.md)

-   You can optionally assign the system to a formation on the *Formations* page, as follows:

    -   Systems of type *SAP Commerce Cloud*, *SAP Cloud for Customer*, and *SAP Field Service Management* can be assigned to a formation directly before the integration is complete on the respective SAP Customer Experience \(SAP CX\) system side. However, to enable the API access, you first need to complete the integration.

    -   For systems of type *SAP S/4HANA Cloud* and *SAP SuccessFactors*, you first need to configure the integration on the respective SAP system side.

        See [Including SAP Systems in a Formation](including-sap-systems-in-a-formation-68b04fa.md).


-   If you no longer need it, you can deregister or remove the system depending on its status. See [Deregistering or Removing an SAP System](deregistering-or-removing-an-sap-system-0c6f498.md).


**Related Information**  


[Extending SAP S/4HANA Cloud in the Cloud Foundry and Kyma Environment](extending-sap-s-4hana-cloud-in-the-cloud-foundry-and-kyma-environment-40b9e6c.md "Extend SAP S/4HANA Cloud with extension applications running on the cloud platform using automated integration configuration.")

[Extending SAP Marketing Cloud in the Cloud Foundry and Kyma Environment](extending-sap-marketing-cloud-in-the-cloud-foundry-and-kyma-environment-18bb3d9.md "")

[Extending SAP SuccessFactors in the Cloud Foundry and Kyma Environment](extending-sap-successfactors-in-the-cloud-foundry-and-kyma-environment-9e33934.md "Use SAP BTP to extend SAP SuccessFactors with extension applications running on the cloud platform.")

[Extending SAP Customer Experience Products in the Kyma Environment](extending-sap-customer-experience-products-in-the-kyma-environment-83df31a.md "You can configure the integration between SAP BTP and SAP Customer Experience automatically to extend SAP Customer Experience products with applications running on the cloud platform.")

