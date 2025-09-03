<!-- loiobe85ce07823844848183a63c1bb15d17 -->

# Register an SAP Integrated Business Planning System in a Global Account in SAP BTP

To connect an SAP Integrated Business Planning system with a global account in SAP BTP, you need to register the system in the corresponding global account.



<a name="loiobe85ce07823844848183a63c1bb15d17__prereq_l4m_s5b_fhb"/>

## Prerequisites

-   See [Adding, Registering and Deregistering Systems](adding-registering-and-deregistering-systems-2ffdaff.md)

-   You are an administrator of the global account where you want to register your SAP Integrated Business Planning system.

-   To configure the integration on the SAP Integrated Business Planning system side, you need to be an administrator of the SAP Integrated Business Planning tenant.




<a name="loiobe85ce07823844848183a63c1bb15d17__context_d5k_gxw_2pb"/>

## Context

The registration process is based on a registration token that is used for the pairing of the SAP Integrated Business Planning system and the corresponding global account. You create the token in the global account, and then the tenant administrator of the respective SAP Integrated Business Planning system uses the token to start the automated registration process on the SAP Integrated Business Planning system side.

> ### Note:  
> When registering SAP Integrated Business Planning systems, you can have up to 1000 tokens per global account ready to be used. Tokens that are already used to register an SAP Integrated Business Planning system are not included in this number.
> 
> This means that you cannot have more than 1000 systems in the *Systems* page of type SAP Integrated Business Planning with an empty status and generated token that is not used yet.

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

-   *Error while Deregistering* - the deregistration has failed. Try to deregister the system again. If the problem persists, report a case in the `BC-NEO-EXT-S4C` component..
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

-   *Error while Removing* - the system removal has failed. Try to remove the system again. If the problem persists, report a case in the `BC-NEO-EXT-S4C` component.

> ### Note:  
> When registering a system or creating a formation, the data you provide in the given input fields is not encrypted with your customer managed key. The data you enter is only encrypted at rest.

> ### Note:  
> You cannot migrate the registered SAP Integrated Business Planning systems between global accounts.
> 
> If you want to start using another global account, you will have to register your SAP Integrated Business Planning systems again.

> ### Note:  
> You can have the same SAP Integrated Business Planning system registered in two global accounts:
> 
> -   If the two global accounts belong to the same Customer ID, then the SAP Integrated Business Planning system will be auto discovered in both global accounts.
> 
>     In this case, if you register the SAP Integrated Business Planning system in one of the global accounts, it will appear registered in the other global account as well. If the communications scenario group with which the SAP Integrated Business Planning system has been registered in the first global account works for the use case in the second global account, then you can use the same system in a formation in the second global account as well.
> 
>     If the use case in the second global account requires a different communication scenario group, you have to add the SAP Integrated Business Planning system manually in this global account and register it with the necessary communication scenario group.
> 
> -   If the two global accounts belong to different Customer IDs, the SAP Integrated Business Planning system will be auto discovered in one of the global account and need to be added manually in the other. Then, you register the system for each of the global accounts.



<a name="loiobe85ce07823844848183a63c1bb15d17__steps_iw4_jxw_2pb"/>

## Procedure

1.  In the cockpit, navigate to your global account, and then choose *System Landscape* \> *Systems*.

2.  On the *Systems* page, choose *Add System*.

    1.  In the *Type* dropdown list, select *SAP Integrated Business Planning*.

    2.  Enter a name for the system you want to register.

        > ### Note:  
        > Use only printable ASCII characters.

        > ### Tip:  
        > We recommend that you indicate the type of the system when specifying the system name. For example, <code><i class="varname">&lt;mysystem&gt;</i>-S/4HANA-cloud</code>. This helps you identify the system type when assigning systems to a formation.

    3.  Choose *Add*.

    4.  In the *Communication Scenario Groups* dropdown menu, select *All Communication Scenarios* to create any of the communication scenarios in SAP Integrated Business Planning.

    5.  Choose *Get Token*.

        The system generates the registration token.

    6.  Copy the registration token and send it to the tenant administrator for the respective SAP Integrated Business Planning system. You need it for configuring the integration on the extended SAP Integrated Business Planning system side.

        You can also get the registration token later, once the system appears in the list on the *Systems* page.

        The registration token is valid for 7 days after it has been generated. When a token is not used within its validity period, it is no longer valid and cannot be used for registering an SAP Integrated Business Planning system. If the validity of the token expires before you use it to configure the integration on the SAP Integrated Business Planning system side and complete the registration, you need to get a new token. You can then copy it and use it to complete the registration.

        > ### Note:  
        > A registration token can be used only once, for registering a single SAP Integrated Business Planning system.

    7.  Close the wizard.

        The SAP Integrated Business Planning system appears in the list of systems on the *Systems* page. Its *Status* field is empty because the registration process is not yet completed.


3.  Start the automated registration process on the SAP Integrated Business Planning system side. To do so, proceed as described in as described in [Trigger the Registration in the SAP Integrated Business Planning Tenant](trigger-the-registration-in-the-sap-integrated-business-planning-tenant-b06370b.md).

    > ### Note:  
    > You can register a system with the same name only once per global account. Once you have started a registration process for a system with a specified name you can no longer register a system with the same name and connect it with the same global account.

4.  Check the status of the registration process. To do so, in the cockpit navigate to your global account, and on the *Systems* page, check if the status of the SAP Integrated Business Planning system has changed to *Registered*.

    If you are already on the *Systems* page, refresh the page to check if the status has changed.




<a name="loiobe85ce07823844848183a63c1bb15d17__postreq_a24_pnx_2pb"/>

## Next Steps

[Trigger the Registration in the SAP Integrated Business Planning Tenant](trigger-the-registration-in-the-sap-integrated-business-planning-tenant-b06370b.md)

