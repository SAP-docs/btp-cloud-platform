<!-- loio1582d723f3814d30beba5fc0daa0bb0d -->

# Register an SAP Customer Experience System

Register an SAP Customer Experience system to connect it with a global account in SAP BTP.



<a name="loio1582d723f3814d30beba5fc0daa0bb0d__prereq_l4m_s5b_fhb"/>

## Prerequisites

-   See [Registering an SAP System](Registering_an_SAP_System_2ffdaff.md).

-   You are an administrator of the global account where you want to register your SAP Customer Experience system.

-   To configure the integration on the SAP Customer Experience system side, you need to be an administrator of the SAP Customer Experience tenant.




## Context

The registration process is based on an integration token that is used for the pairing of the SAP Customer Experience system and the corresponding global account. You create the token in the SAP BTP cockpit, and then use it to configure the integration on the SAP Customer Experience system side.

The registration process has the following states displayed in the cockpit:

-   *Pending* - the integration token for an SAP system has been created but the registration on the respective SAP Customer Experience system side has not been performed or completed. The system can be assigned to a formation on the *Formations* page in the cockpit, but to enable the API access, you first need to configure the integration on the corresponding SAP Customer Experience product side.

-   *Registered* - the integration token has been used and the automated registration process has been successfully completed. The system can be assigned to a formation on the *Formations* page in the cockpit. You can use the corresponding SAP Customer Experience Cloud product APIs.
-   *Error* - the registration has failed.



## Procedure

1.  In the cockpit, navigate to your global account, and then choose *System Landscape* \> *Systems*.

2.  In the *Systems* panel, choose *Register System*.

3.  In the *Register System* dialog box:

    1.  Enter a name for the system you want to register.

        > ### Note:  
        > Use only printable ASCII characters.

    2.  In the *Type* dropdown list, select the system type.

        The following SAP Customer Experience systems are supported:

        -   SAP Commerce Cloud

        -   SAP Field Service Management

        -   SAP Cloud for Customer


    3.  Choose *Register*.


    The cloud platform generates an integration token that you use to configure the integration between your SAP Customer Experience system and the global account in SAP BTP on the respective SAP Customer Experience system side.

4.  Copy the integration token.

5.  Close the dialog box.

    The SAP Customer Experience system appears in the list of registered systems. Its status is *Pending* because the registration process is not yet completed.

6.  \(Optional\) For systems in status *Pending*, you can generate a new token and copy it. To do so, choose the ![](images/ViewIntegrationToken_b8ec588.png) \(Display token\) button.

7.  \(Recommended\) Follow the steps in [Assigning SAP Systems to a Formation](Assigning_SAP_Systems_to_a_Formation_68b04fa.md) before proceeding with step 8.

8.  Configure the integration on the SAP Customer Experience system side. See [Extending SAP Customer Experience Products in the Kyma Environment](Extending_SAP_Customer_Experience_Products_in_the_Kyma_Environment_83df31a.md).

    > ### Note:  
    > The integration token is valid for 10 minutes after it has been generated. When a token is not used within its validity period, it is no longer valid and cannot be used. If the token expires before you have used it, you can generate a new token by choosing the ![](images/ViewIntegrationToken_b8ec588.png) \(Display token\) button. The integration token can be used only once, for registering a single SAP Customer Experience system.

9.  Check the status of the registration process. To do so, in the cockpit navigate to your global account, and in the *Systems* panel, check if the status of the SAP Customer Experience system has changed to *Registered*.

    If you are already in the *Systems* panel, refresh the page to check if the status has changed.




<a name="loio1582d723f3814d30beba5fc0daa0bb0d__result_tsf_ygb_clb"/>

## Results

-   Once you use the integration token to connect your SAP Customer Experience system, all of the exposed services and events are propagated to the Kyma runtime.

-   Once a system is registered, you can deregister it only after removing it from all entitlement configurations and formations it takes part in. If a problem occurs while deregistering the system, you get a status *Deregister Error*. In this case, you have to report an incident.

    > ### Note:  
    > You will not be able to deregister a system, if its status is one of the following:
    > 
    > -   *Error*
    > 
    > -   *Deregistering*
    > 
    > -   *Deregister Error*


