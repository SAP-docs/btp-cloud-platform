<!-- loio1582d723f3814d30beba5fc0daa0bb0d -->

# Register an SAP Customer Experience System

Register an SAP Customer Experience system to connect it with a global account in SAP BTP.



<a name="loio1582d723f3814d30beba5fc0daa0bb0d__prereq_l4m_s5b_fhb"/>

## Prerequisites

-   See [Adding, Registering and Deregistering Systems](adding-registering-and-deregistering-systems-2ffdaff.md).

-   You are an administrator of the global account where you want to register your SAP Customer Experience system.

-   To configure the integration on the SAP Customer Experience system side, you need to be an administrator of the SAP Customer Experience tenant.




## Context

The registration process is based on a registration token that is used for the pairing of the SAP Customer Experience system and the corresponding global account. You create the token in the global account, and then the tenant administrator of the respective SAP Customer Experience system uses the token to start the automated registration process on the SAP Customer Experience system side.

The registration process has the following states displayed in the cockpit:

-   No status displayed in the *Status* column - the registration token for an SAP system has been created but the registration on the respective SAP solution system side has not been performed or completed.

-   *Registered* - the registration token has been used and the automated registration process has been successfully completed. The system can be assigned to a formation on the *Formations* page in the cockpit.
-   *Error while Registering* - the registration has failed. Remove the system and then add it to the *Systems* list and try to register it again
-   *Deregistering* - а deregistration process has started in the SAP BTP cockpit. As a result, the connection between the SAP solution system and the global account in SAP BTP is removed. The system remains in the list and you can register it again later on.

    Once a system is registered, you can deregister it only after removing it from all entitlement configurations and formations it takes part in.

-   *Error while Deregistering* - the deregistration has failed. Try to deregister the system again. If the problem persists, report a case in the `BC-CP-MP` component.
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
    > 
    >     Try to deregister the system again.

-   *Error while Removing* - the system removal has failed. Try to remove the system again. If the problem persists, report a case in the `BC-CP-MP` component.

> ### Note:  
> When registering a system or creating a formation, the data you provide in the given input fields is not encrypted with your customer managed key. The data you enter is only encrypted at rest.



## Procedure

1.  In the cockpit, navigate to your global account, and then choose *System Landscape* \> *Systems*.

2.  On the *Systems* page, choose *Add System*.

    1.  In the *Type* dropdown list, select the system type.

        The following SAP Customer Experience systems are supported:

        -   SAP Commerce Cloud

        -   SAP Field Service Management

        -   SAP Cloud for Customer


    2.  Enter a name for the system you want to register.

        > ### Note:  
        > Use only printable ASCII characters.

        > ### Tip:  
        > We recommend that you indicate the type of the system when specifying the system name. For example, <code><i class="varname">&lt;mysystem&gt;</i>-S/4HANA-cloud</code>. This helps you identify the system type when assigning systems to a formation.

    3.  Choose *Add*.

    4.  Choose *Get Token*.

        The system generates the registration token.

    5.  Copy the registration token and send it to the tenant administrator for the respective SAP Customer Experience system. You need it for configuring the integration on the extended SAP Customer Experience system side.

        You can also get the registration token later, once the system appears in the list on the *Systems* page.

        The integration token is valid for 10 minutes after it has been generated. When a token is not used within its validity period, it is no longer valid and cannot be used for registering a system. If the validity of the token expires before you use it to configure the integration on the SAP Customer Experience system side and complete the registration, you need to get a new token. You can then copy it and use it to complete the registration.

        > ### Note:  
        > A registration token can be used only once, for registering a single SAP Customer Experience system.

    6.  Close the wizard.

        The SAP Customer Experience system appears in the list of systems on the *Systems* page. Its *Status* field is empty because the registration process is not yet completed.


3.  \(Recommended\) Follow the steps in [Automating Integrations Using Formations](automating-integrations-using-formations-68b04fa.md) before proceeding with the registration on the SAP Customer Experience side.

4.  Configure the integration on the SAP Customer Experience system side. See [Extending SAP Customer Experience Products in the Kyma Environment](extending-sap-customer-experience-products-in-the-kyma-environment-83df31a.md).

5.  Check the status of the registration process. To do so, in the cockpit navigate to your global account, and in the *Systems* panel, check if the status of the SAP Customer Experience system has changed to *Registered*.

    If you are already in the *Systems* panel, refresh the page to check if the status has changed.




<a name="loio1582d723f3814d30beba5fc0daa0bb0d__result_tsf_ygb_clb"/>

## Results

Once you use the integration token to connect your SAP Customer Experience system, all of the exposed services and events are propagated to the Kyma runtime.

**Related Information**  


[Adding, Registering and Deregistering Systems](adding-registering-and-deregistering-systems-2ffdaff.md "To connect an SAP system with a global account in SAP BTP, you need to register the system. You can also add and work with a third-party systems.")

[Deregister or Removе a System](deregister-or-remov-a-system-0c6f498.md "When you no longer need the system to be paired with your global account, you can deregister or remove it depending on its status.")

