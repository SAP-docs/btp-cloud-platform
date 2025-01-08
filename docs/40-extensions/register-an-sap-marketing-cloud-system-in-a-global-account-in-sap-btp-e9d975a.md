<!-- loioe9d975a45c954501bbe59e39dfb468c0 -->

# Register an SAP Marketing Cloud System in a Global Account in SAP BTP

To connect an SAP Marketing Cloud system with a global account in SAP BTP, you need to register the system in the corresponding global account.



<a name="loioe9d975a45c954501bbe59e39dfb468c0__prereq_l4m_s5b_fhb"/>

## Prerequisites

-   See [Registering and Deregistering Systems](registering-and-deregistering-systems-2ffdaff.md)

-   You are an administrator of the global account where you want to register your SAP Marketing Cloud system.

-   To configure the integration on the SAP Marketing Cloud system side, you need to be an administrator of the SAP Marketing Cloud tenant.




<a name="loioe9d975a45c954501bbe59e39dfb468c0__context_d5k_gxw_2pb"/>

## Context

The registration process is based on a registration token that is used for the pairing of the SAP Marketing Cloud system and the corresponding global account. You create the token in the global account, and then the tenant administrator of the respective SAP Marketing Cloud system uses the token to start the automated registration process on the SAP Marketing Cloud system side.

> ### Note:  
> When registering SAP Marketing Cloud systems, you can have up to 1000 tokens per global account ready to be used. Tokens that are already used to register an SAP Marketing Cloud system are not included in this number.
> 
> This means that you cannot have more than 1000 systems in the *Systems* page of type SAP Marketing Cloud with an empty status and generated token that is not used yet.

The registration process has the following states displayed in the cockpit:

-   No status displayed in the *Status* column - the registration token for an SAP system has been created but the registration on the respective SAP solution system side has not been performed or completed.

-   *Registered* - the registration token has been used and the automated registration process has been successfully completed. The system can be assigned to a formation on the *Formations* page in the cockpit.
-   *Error while Registering* - the registration has failed. Remove the system and then add it to the *Systems* list and try to register it again
-   *Deregistering* - а deregistration process has started in the SAP BTP cockpit. As a result, the connection between the SAP solution system and the global account in SAP BTP is removed. The system remains in the list and you can register it again later on.

    Once a system is registered, you can deregister it only after removing it from all entitlement configurations and formations it takes part in.

    > ### Note:  
    > You will not be able to deregister a system if its status is one of the following:
    > 
    > -   *Error while Registering*
    > 
    > -   *Deregistering*

-   *Error while Deregistering* - the deregistration has failed. Try to deregister the system again. If the problem persists, you have to report a case in the `BC-NEO-EXT-S4C` component..
-   *Removing* - a system removal process has started in the SAP BTP cockpit. As a result, the link between the SAP solution and SAP BTP is destroyed and the system is removed from the list. To register the system again, first you must add it to the list anew, and then initiate the registration procedure.

    Once a system is registered, you can only remove it if you first deregister it.

    > ### Note:  
    > You will not be able to remove a system if its status is one of the following:
    > 
    > -   *Registered*
    > 
    >     You first need to deregister the system.
    > 
    > -   *Deregistering*
    > 
    > -   *Error while Deregistering*

-   *Error while Removing* - the system removal has failed. Try to deregister the system again. If the problem persists, you have to report a case in the `BC-NEO-EXT-S4C` component.

> ### Note:  
> When registering a system or creating a formation, the data you provide in the given input fields is not encrypted with your customer managed key. The data you enter is only encrypted at rest.

> ### Note:  
> You cannot migrate the registered SAP Marketing Cloud systems between global accounts.
> 
> If you want to start using another global account, you will have to register your SAP Marketing Cloud systems again.



<a name="loioe9d975a45c954501bbe59e39dfb468c0__steps_iw4_jxw_2pb"/>

## Procedure

1.  In the cockpit, navigate to your global account, and then choose *System Landscape* \> *Systems*.

2.  On the *Systems* page, choose *Add System*.

    1.  In the *Type* dropdown list, select *SAP Marketing Cloud*.

    2.  Enter a name for the system you want to register.

        > ### Note:  
        > Use only printable ASCII characters.

        > ### Tip:  
        > We recommend that you indicate the type of the system when specifying the system name. For example, <code><i class="varname">&lt;mysystem&gt;</i>-S/4HANA-cloud</code>. This helps you identify the system type when assigning systems to a formation.

    3.  Choose *Add*.

    4.  In the *Communication Scenario Groups* dropdown menu, select *All Communication Scenarios* to create any of the communication scenarios in SAP Marketing Cloud.

    5.  Choose *Get Token*.

        The system generates the registration token.

    6.  Copy the registration token and send it to the tenant administrator for the respective SAP Marketing Cloud system. You need it for configuring the integration on the extended SAP Marketing Cloud system side.

        You can also get the registration token later, once the system appears in the list on the *Systems* page.

        The registration token is valid for 7 days after it has been generated. When a token is not used within its validity period, it is no longer valid and cannot be used for registering an SAP Marketing Cloud system. If the validity of the token expires before you use it to configure the integration on the SAP Marketing Cloud system side and complete the registration, you need to get a new token. You can then copy it and use it to complete the registration.

        > ### Note:  
        > A registration token can be used only once, for registering a single SAP Marketing Cloud system.

    7.  Close the wizard.

        The SAP Marketing Cloud system appears in the list of systems on the *Systems* page. Its *Status* field is empty because the registration process is not yet completed.


3.  Start the automated registration process on the SAP Marketing Cloud system side. To do so, proceed as described in as described in [Trigger the Registration in the SAP Marketing Cloud Tenant](trigger-the-registration-in-the-sap-marketing-cloud-tenant-d7416c3.md).

    > ### Note:  
    > You can register a system with the same name only once per global account. Once you have started a registration process for a system with a specified name you can no longer register a system with the same name and connect it with the same global account.

4.  Check the status of the registration process. To do so, in the cockpit navigate to your global account, and on the *Systems* page, check if the status of the SAP Marketing Cloud system has changed to *Registered*.

    If you are already on the *Systems* page, refresh the page to check if the status has changed.




<a name="loioe9d975a45c954501bbe59e39dfb468c0__postreq_a24_pnx_2pb"/>

## Next Steps

[Trigger the Registration in the SAP Marketing Cloud Tenant](trigger-the-registration-in-the-sap-marketing-cloud-tenant-d7416c3.md)

**Related Information**  


[Registering and Deregistering Systems](registering-and-deregistering-systems-2ffdaff.md "To connect an SAP system with a global account in SAP BTP, you need to register the system. You can also add and work with a third-party systems.")

[Deregister or Removе a System](deregister-or-remov-a-system-0c6f498.md "When you no longer need the system to be paired with your global account, you can deregister or remove it depending on its status.")

