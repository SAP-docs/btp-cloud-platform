<!-- loioe9d975a45c954501bbe59e39dfb468c0 -->

# Register an SAP Marketing Cloud System in a Global Account in SAP BTP

To connect an SAP Marketing Cloud system with a global account in SAP BTP, you need to register the system in the corresponding global account.



<a name="loioe9d975a45c954501bbe59e39dfb468c0__prereq_l4m_s5b_fhb"/>

## Prerequisites

-   See [Registering an SAP System](Registering_an_SAP_System_2ffdaff.md)

-   You are an administrator of the global account where you want to register your SAP Marketing Cloud system.

-   To configure the integration on the SAP Marketing Cloud system side, you need to be an administrator of the SAP Marketing Cloud tenant.




<a name="loioe9d975a45c954501bbe59e39dfb468c0__context_d5k_gxw_2pb"/>

## Context

The registration process is based on an integration token that is used for the pairing of the SAP Marketing Cloud system and the corresponding global account. You create the token in the global account, and then the tenant administrator of the respective SAP Marketing Cloud system uses the token to start the automated registration process on the SAP Marketing Cloud system side.

The registration process has the following states displayed in the SAP BTP cockpit:

-   *Pending* - the integration token for an SAP system has been created but the registration on the respective SAP Marketing Cloud system side has not been performed or completed.

-   *Registered* - the integration token has been used and the automated registration process has been successfully completed.
-   *Error* - the registration has failed.



<a name="loioe9d975a45c954501bbe59e39dfb468c0__steps_iw4_jxw_2pb"/>

## Procedure

1.  In the cockpit, navigate to your global account, and then choose *System Landscape* \> *Systems*.

2.  In the *Systems* panel, choose *Register System*.

3.  In the *Register System* dialog box:

    1.  Enter a name for the system you want to register.

        > ### Note:  
        > Use only printable ASCII characters.

    2.  In the *Type* dropdown list, select the system type.

    3.  Choose *Register*.


    The cloud platform generates an integration token that the tenant administrator of the extended SAP Marketing Cloud system uses when configuring the integration between your SAP Marketing Cloud system and the cloud platform on the respective SAP Marketing Cloud system side.

4.  Copy the integration token and send it to the tenant administrator for the respective SAP Marketing Cloud system. You need it for configuring the integration on the extended SAP Marketing Cloud system side.

    You can also copy the integration token later, once the system appears in the list of registered systems.

    The integration token is valid for 7 days after it has been generated. When a token is not used within its validity period, it is no longer valid and cannot be used for registering an SAP Marketing Cloud system. If the validity of the token expires before you use it to configure the integration on the SAP Marketing Cloud system side and complete the registration, a new token is issued. You can then copy it and use it to complete the registration.

    > ### Note:  
    > An integration token can be used only once, for registering a single SAP Marketing Cloud system.

5.  Close the dialog box.

    The SAP Marketing Cloud system appears in the list of registered systems. Its status is *Pending* because the registration process is not yet completed.

6.  \(Optional\) For systems in status *Pending*, you can view and copy the integration token. To do so, choose the ![](images/ViewIntegrationToken_b8ec588.png) \(Display token\) button.

7.  Start the automated registration process on the SAP Marketing Cloud system side. To do so, proceed as described in as described in [Trigger the Registration in the SAP Marketing Cloud Tenant](Trigger_the_Registration_in_the_SAP_Marketing_Cloud_Tenant_d7416c3.md).

    > ### Note:  
    > You can register a system with the same name only once per global account. Once you have started a registration process for a system with a specified name you can no longer register a system with the same name and connect it with the same global account, unless you delete the corresponding extension in the *Maintain Extensions on SAP BTP* in the SAP Marketing Cloud tenant. If the registration process fails, you need to delete the failed extension from the SAP Marketing Cloud tenant and create a new integration token in the cockpit for the corresponding system to be able to start the automated registration process again.

8.  Check the status of the registration process. To do so, in the cockpit navigate to your global account, and on the *Systems* page, check if the status of the SAP Marketing Cloud system has changed to *Registered*.

    If you are already on the *Systems* page, refresh the page to check if the status has changed.

    Once a system is registered, you can deregister it only after removing it from all entitlement configurations and formations it takes part in. If a problem occurs while deregistering the system, you get a status *Deregister Error*. In this case, you have to report an incident.

    > ### Note:  
    > You will not be able to deregister a system, if its status is one of the following:
    > 
    > -   *Error*
    > 
    > -   *Deregistering*
    > 
    > -   *Deregister Error*




<a name="loioe9d975a45c954501bbe59e39dfb468c0__postreq_a24_pnx_2pb"/>

## Next Steps

[Trigger the Registration in the SAP Marketing Cloud Tenant](Trigger_the_Registration_in_the_SAP_Marketing_Cloud_Tenant_d7416c3.md)

