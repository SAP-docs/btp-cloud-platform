<!-- loio5481d594718f44c1ad7a63d154c342fd -->

# Registering Third-Party Systems

To connect a third-party systems, for example a Google system, with a global account in SAP BTP, you first need to register this system.



<a name="loio5481d594718f44c1ad7a63d154c342fd__prereq_l4m_s5b_fhb"/>

## Prerequisites

You are a global account administrator, or you are a system landscape administrator of the global account where you want to register your third-party system. See [Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md).



<a name="loio5481d594718f44c1ad7a63d154c342fd__context_ihl_j3h_jlb"/>

## Context

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

You add a third-party system to the list in the *System Landscape* page. At this point you provide all the required details for this system: its type, provider, URL, and system ID.

> ### Note:  
> You cannot migrate the registered third-party systems between global accounts.
> 
> If you want to start using another global account, you will have to register your systems again.

> ### Note:  
> When registering a system or creating a formation, the data you provide in the given input fields is not encrypted with your customer managed key. The data you enter is only encrypted at rest.



<a name="loio5481d594718f44c1ad7a63d154c342fd__steps_qrt_jfd_dxb"/>

## Procedure

1.  In the cockpit, navigate to your global account, and then choose *System Landscape* \> *Systems* .

2.  On the *Systems* page, choose *Add System*.

3.  In the *Add System* wizard:

    1.  Enter a name for the system you want to register.

        > ### Note:  
        > Use only printable ASCII characters.

        > ### Tip:  
        > We recommend that you indicate the type of the system when specifying the system name. For example, ****<mysystem\>*-google-workspace***.

    2.  In the *Type* dropdown list, select *Other System Type*.

    3.  In the *System Type Name* field, enter the type of your system. This is a user-defined type of the system you want to add. For example, *Workspace*.

    4.  In the *Provider* field, enter the provider of your system. For example, *Google*.

    5.  In the *URL* field, enter the URL of your system.

    6.  In the *System ID* field, enter the unique identifier of the added system that is used in its own domain.

    7.  Choose *Add*.





<a name="loio5481d594718f44c1ad7a63d154c342fd__result_ytq_hrh_jlb"/>

## Results

The system has been added as a record to the list on the *Systems* page in the SAP BTP cockpit and the system details view opens.

If you no longer need it, you can remove the system depending on its status. See [Deregistering or Removing a System](deregistering-or-removing-a-system-0c6f498.md).

