<!-- loio2ffdaff0f1454acdb046876045321c91 -->

# Registering an SAP System

To connect an SAP solution system with a global account in SAP BTP, you first need to register the system.



<a name="loio2ffdaff0f1454acdb046876045321c91__prereq_l4m_s5b_fhb"/>

## Prerequisites

You are a global account administrator, or you are a system landscape administrator of the global account where you want to register your SAP system. See [Working with Role Collections](../50-administration-and-ops/Working_with_Role_Collections_393ea0b.md)



<a name="loio2ffdaff0f1454acdb046876045321c91__context_ihl_j3h_jlb"/>

## Context

The registration process is based on an integration token that is used for the pairing of the system and the corresponding global account. You create the token in the SAP BTP cockpit, and then use it to configure the integration on the corresponding SAP solution side.

The following SAP system types are supported:

-   SAP S/4HANA Cloud \(available for Cloud Foundry and Kyma environment\)

-   SAP Marketing Cloud \(available for Cloud Foundry and Kyma environment\)

-   SAP SuccessFactors \(available for Cloud Foundry and Kyma environment\)

-   SAP Commerce Cloud \(available for Kyma environment\)

-   SAP Cloud for Customer \(available for Kyma environment\)

-   SAP Field Service Management \(available for Kyma environment\)


The registration process has the following states displayed in the cockpit:

-   *Pending* - the integration token for an SAP system has been created but the registration on the respective SAP solution system side has not been performed or completed.

-   *Registered* - the integration token has been used and the automated registration process has been successfully completed. The system can be assigned to a formation on the *Formations* page in the cockpit.
-   *Error* - the registration has failed.



## Procedure

1.  In the cockpit, navigate to your global account, and then choose *System Landscape* \> *Systems* from the left hand-side navigation.

2.  In the *Systems* panel, choose *Register System*.

3.  In the *Register System* dialog box:

    1.  Enter a name for the system you want to register.

        > ### Note:  
        > Use only printable ASCII characters.

        > ### Tip:  
        > We recommend that you indicate the type of the system when specifying the system name. For example, ****<mysystem\>*-commerce-cloud***. This helps you identify the system type when assigning systems to a formation.

    2.  In the *Type* dropdown list, select the system type.

    3.  Choose *Register*.




<a name="loio2ffdaff0f1454acdb046876045321c91__result_ytq_hrh_jlb"/>

## Results

-   Once you register a system, cloud platform generates an integration token that you use to complete the integration on the respective SAP solution system side.

-   Once a system is registered, you can deregister it only after removing it from all entitlement configurations and formations it takes part in. If a problem occurs while deregistering the system, you get a status *Deregister Error*. In this case, you have to report an incident.

    > ### Note:  
    > You will not be able to deregister a system, if its status is one of the following:
    > 
    > -   *Error*
    > 
    > -   *Deregistering*
    > 
    > -   *Deregister Error*




<a name="loio2ffdaff0f1454acdb046876045321c91__postreq_e5y_rxz_klb"/>

## Next Steps

1.  Copy the integration token and use it to configure the integration on the respective SAP system side.

2.  In the cockpit, assign the system to a formation on the *Formations* page, as follows:

    -   Systems of type *SAP Commerce Cloud*, *SAP Cloud for Customer*, and *SAP Field Service Management* can be assigned to a formation directly before the integration is complete on the respective SAP Customer Experience \(SAP CX\) system side. However, to enable the API access, you first need to complete the integration.

    -   For systems of type *SAP S/4HANA Cloud* and *SAP SuccessFactors*, you first need to configure the integration on the respective SAP system side.

    For more information, see: [Assigning SAP Systems to a Formation](Assigning_SAP_Systems_to_a_Formation_68b04fa.md).


**Related Information**  


[Extending SAP S/4HANA Cloud in the Cloud Foundry and Kyma Environment](Extending_SAP_S4HANA_Cloud_in_the_Cloud_Foundry_and_Kyma_Environment_40b9e6c.md "Extend SAP S/4HANA Cloud with extension applications running on the cloud platform using automated integration configuration.")

[Extending SAP SuccessFactors in the Cloud Foundry and Kyma Environment](Extending_SAP_SuccessFactors_in_the_Cloud_Foundry_and_Kyma_Environment_9e33934.md "Use SAP BTP to extend SAP SuccessFactors with extension applications running on the cloud platform.")

[Extending SAP Customer Experience Products in the Kyma Environment](Extending_SAP_Customer_Experience_Products_in_the_Kyma_Environment_83df31a.md "You can configure the integration between SAP BTP and SAP Customer Experience automatically to extend SAP Customer Experience products with applications running on the cloud platform.")

