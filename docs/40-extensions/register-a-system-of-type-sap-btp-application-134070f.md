<!-- loio134070ff2a6045ce84f534a7eeecdf14 -->

# Register a System of Type SAP BTP Application



<a name="loio134070ff2a6045ce84f534a7eeecdf14__prereq_l4m_s5b_fhb"/>

## Prerequisites

You are a global account administrator, or you are a system landscape administrator of the global account where you want to add your *SAP BTP Application* system. See [Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md).



## Context

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

You can connect an application you've developed and deployed in SAP BTP with a global account in SAP BTP. To do that, you add a system representing your application to the list in the *System Landscape* \> *Systems* page. The system type you use is *SAP BTP Application*. You also have to provide the namespace which is unique for this system. A unique system ID is automatically assigned to any system of type *SAP BTP Application*. For systems of type SAP BTP Application, this completes the registration process and you have your system registered with SAP BTP. Even though the system of type SAP BTP Application is registered directly, no status is displayed.

When you have a systems of your application listed in the *Systems* page, you can include it in different formations depending on your needs.



<a name="loio134070ff2a6045ce84f534a7eeecdf14__steps_qrt_jfd_dxb"/>

## Procedure

1.  In the cockpit, navigate to your global account, and then choose *System Landscape* \> *Systems* .

2.  On the *Systems* page, choose *Add System*.

3.  In the *Add System* wizard:

    1.  In the *Type* dropdown list, select *SAP BTP Application*.

    2.  Enter a name for the system you want to register.

        > ### Note:  
        > Use only printable ASCII characters.

    3.  In the *System ID* field, there is an automatically assigned ID which is unique for this system.

    4.  In the *System Namespace*, enter a unique technical identifier to avoid global ID and name conflicts. It covers vendor, system \(application or service\), authority namespaces and optionally further sub-context namespaces.

    5.  Choose *Add*.



**Related Information**  


[Declaring System APIs and Events as Dependencies for Business Scenarios](declaring-system-apis-and-events-as-dependencies-for-business-scenarios-e8542d8.md#loioe8542d805f5e430fba469c8ebe8e76f4 "")

