<!-- loiof216895c59c5460f8ac8b30e78a33e46 -->

# Register a Microsoft 365 Copilot for Joule System



<a name="loiof216895c59c5460f8ac8b30e78a33e46__prereq_l4m_s5b_fhb"/>

## Prerequisites

You are a global account administrator, or you are a system landscape administrator of the global account where you want to add a system of type Microsoft 365 Copilot for Joule. See [Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md).



## Context

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

You can integrate Microsoft 365 Copilot with Joule so that your users have conversational interactions that include content about integrated SAP systems. To do that, you have to add a system of type *Microsoft 365 Copilot for Joule* in a formation of type *Integration with Joule*. See [Integrating Joule with Microsoft 365 Copilot](https://help.sap.com/docs/joule/integrating-joule-with-sap/integrating-joule-with-microsoft-365-copilot?version=CLOUD&locale=en-US).



<a name="loiof216895c59c5460f8ac8b30e78a33e46__steps_qrt_jfd_dxb"/>

## Procedure

1.  In the cockpit, navigate to your global account, and then choose *System Landscape* \> *Systems* .

2.  On the *Systems* page, choose *Add System*.

3.  In the *Add System* wizard:

    1.  In the *Type* dropdown list, select *Microsoft 365 Copilot for Joule*.

    2.  Enter a name for the system you want to register.

        > ### Note:  
        > Use only printable ASCII characters.

        > ### Tip:  
        > We recommend that you indicate the type of the system when specifying the system name.

    3.  In the *System ID* field, enter the ID which corresponds to the Microsoft Entra Tenant ID. To see how to get this ID, see section **Get the Tenant ID of Your Microsoft Entra ID Tenant** of the [Configuring SAP Cloud Identity Services and Microsoft Entra ID for Joule](https://community.sap.com/t5/technology-blog-posts-by-sap/configuring-sap-cloud-identity-services-and-microsoft-entra-id-for-joule/ba-p/14105743) blog post.

    4.  Choose *Add*.





<a name="loiof216895c59c5460f8ac8b30e78a33e46__result_ytq_hrh_jlb"/>

## Results

The system has been added as a record to the list on the *Systems* page in the SAP BTP cockpit and you have added the respective APIs or events.

If you no longer need it, you can remove the system. See [Deregister or Removе a System](deregister-or-remov-a-system-0c6f498.md).



<a name="loiof216895c59c5460f8ac8b30e78a33e46__postreq_uch_5k1_cgc"/>

## Next Steps

Create a new *Integration with Joule* formation or use an already existing one and include in the system in this formation. See [Enabling Joule](enabling-joule-e208f1f.md).

