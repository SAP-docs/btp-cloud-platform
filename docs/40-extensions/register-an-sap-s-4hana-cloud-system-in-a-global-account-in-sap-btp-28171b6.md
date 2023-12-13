<!-- loio28171b629f3549af8c1d66d7c8de5e18 -->

# Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP

To connect an SAP S/4HANA Cloud, public edition system with a global account in SAP BTP, you need to register the system in the corresponding global account.



<a name="loio28171b629f3549af8c1d66d7c8de5e18__prereq_l4m_s5b_fhb"/>

## Prerequisites

-   See [Registering an SAP System](registering-an-sap-system-2ffdaff.md).

-   You are an administrator of the global account where you want to register your SAP S/4HANA Cloud system.

-   To configure the integration on the SAP S/4HANA Cloud system side, you need to be an administrator of the SAP S/4HANA Cloud tenant.




## Context

> ### Note:  
> This documentation refers to SAP S/4HANA Cloud, public edition. See [Introduction to the Universe of SAP S/4HANA Cloud, public edition](https://help.sap.com/docs/SAP_S4HANA_CLOUD/f77dde055ecb4541b57787d362c46a36/2962fce53eef47b4b3a8e6c945adafbe.html).

The registration process is based on a registration token that is used for the pairing of the SAP S/4HANA Cloud system and the corresponding global account. You create the token in the global account, and then the tenant administrator of the respective SAP S/4HANA Cloud system uses the token to start the automated registration process on the SAP S/4HANA Cloud system side.

> ### Note:  
> When registering SAP S/4HANA Cloud systems, you can have up to 1000 tokens per global account ready to be used. Tokens that are already used to register an SAP S/4HANA Cloud system are not included in this number.
> 
> This means that you cannot have more than 1000 systems in the *Systems* list of type SAP S/4HANA Cloud with an empty status and generated token that is not used yet.

> ### Note:  
> You cannot migrate the registered SAP S/4HANA Cloud systems between global accounts.
> 
> If you want to start using another global account, you will have to register your SAP S/4HANA Cloud systems again.

The registration process has the following states displayed in the cockpit:

-   No status displayed in the *Status* column - the registration token for an SAP system has been created but the registration on the respective SAP solution system side has not been performed or completed.

-   *Registered* - the registration token has been used and the automated registration process has been successfully completed. The system can be assigned to a formation on the *Formations* page in the cockpit.
-   *Error while Registering* - the registration has failed.
-   *Deregistering* - а deregistration process has started in the SAP BTP cockpit. As a result, the connection between the SAP solution system and the global account in SAP BTP is removed. The system remains in the list and you can register it again later on.

    Once a system is registered, you can deregister it only after removing it from all entitlement configurations and formations it takes part in.

    > ### Note:  
    > You will not be able to deregister a system if its status is one of the following:
    > 
    > -   *Error while Registering*
    > 
    > -   *Deregistering*
    > 
    > -   *Error while Deregistering*

-   *Error while Deregistering* - the deregistration has failed. If the problem persists, you have to report an incident.
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
    > -   *Error while Removing*
    > 
    > -   *Error while Registering*
    > 
    > -   *Error while Deregistering*

-   *Error while Removing* - the system removal has failed. If the problem persists, you have to report an incident.

> ### Note:  
> When registering a system or creating a formation, the data you provide in the given input fields is not encrypted with your customer managed key. The data you enter is only encrypted at rest.



## Procedure

1.  In the cockpit, navigate to your global account, and then choose *System Landscape* \> *Systems*.

2.  On the *Systems* page, choose *Add System*.

    1.  Enter a name for the system you want to register.

        > ### Note:  
        > Use only printable ASCII characters.

        > ### Tip:  
        > We recommend that you indicate the type of the system when specifying the system name. For example, <code><i class="varname">&lt;mysystem&gt;</i>-S/4HANA-cloud</code>. This helps you identify the system type when assigning systems to a formation.

    2.  In the *Type* dropdown list, select *SAP S/4HANA Cloud*.

    3.  Choose *Add*.

    4.  In the *Communication Scenario Groups* dropdown menu, select one of the following options:

        -   *All Communication Scenarios*: to create any of the communication scenarios in SAP S/4HANA Cloud.

        -   *Eventing Between SAP Cloud Systems*: to allow the automatic enablement of the `SAP_COM_0892` communication scenario in SAP S/4HANA Cloud.

        -   *Integration with SAP Ariba Buying*: to allow the automatic enablement of the `SAP_COM_0545` and `SAP_COM_0A00` communication scenarios in SAP S/4HANA Cloud.

        -   *Integration with SAP Start*: to allow the automatic enablement of the `SAP_COM_0647` communication scenario in SAP S/4HANA Cloud.


    5.  Choose *Get Token*.

        The system generates the registration token.

    6.  Copy the registration token and send it to the tenant administrator for the respective SAP S/4HANA Cloud system. You need it for configuring the integration on the extended SAP S/4HANA Cloud system side.

        You can also get the registration token later, once the system appears in the list on the *Systems* page.

        The registration token is valid for 7 days after it has been generated. When a token is not used within its validity period, it is no longer valid and cannot be used for registering an SAP S/4HANA Cloud system. If the validity of the token expires before you use it to configure the integration on the SAP S/4HANA Cloud system side and complete the registration, you need to get a new token. You can then copy it and use it to complete the registration.

        > ### Note:  
        > A registration token can be used only once, for registering a single SAP S/4HANA Cloud system.

    7.  Close the wizard.

        The SAP S/4HANA Cloud system appears in the list of systems on the *Systems* page. Its *Status* field is empty because the registration process is not yet completed.


3.  Start the automated registration process on the SAP S/4HANA Cloud system side. To do so, proceed as described in as described in [Trigger the Registration in the SAP S/4HANA Cloud Tenant](trigger-the-registration-in-the-sap-s-4hana-cloud-tenant-cadf8f6.md).

    > ### Note:  
    > You can register a system with the same name only once per global account. Once you have started a registration process for a system with a specified name you can no longer register a system with the same name and connect it with the same global account, unless you delete the corresponding extension in the *Maintain Extensions on SAP BTP* in the SAP S/4HANA Cloud tenant. If the registration process fails, you need to delete the failed extension from the SAP S/4HANA Cloud tenant and create a new integration token in the cockpit for the corresponding system to be able to start the automated registration process again.

4.  Check the status of the registration process. To do so, in the cockpit navigate to your global account, and on the *Systems* page, check if the status of the SAP S/4HANA Cloud system has changed to *Registered*.

    If you are already on the *Systems* page, refresh the page to check if the status has changed.




<a name="loio28171b629f3549af8c1d66d7c8de5e18__postreq_ncv_ypf_pmb"/>

## Next Steps

[Trigger the Registration in the SAP S/4HANA Cloud Tenant](trigger-the-registration-in-the-sap-s-4hana-cloud-tenant-cadf8f6.md)

**Related Information**  


[Registering an SAP System](registering-an-sap-system-2ffdaff.md "To connect an SAP system with a global account in SAP BTP, you first need to register the system.")

[Deregistering or Removing a System](deregistering-or-removing-a-system-0c6f498.md "When you no longer need the system to be paired with your global account, you can deregister or remove it depending on its status.")

