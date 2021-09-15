<!-- loiod477618e861c48d2976e03f9b6a3cfe8 -->

# Log On with a Custom Identity Provider to the Cloud Foundry Environment Using the Cloud Foundry Command-Line Interface

Learn how to use different methods to log on to Cloud Foundry using a custom identity provider \(IdP\).



<a name="loiod477618e861c48d2976e03f9b6a3cfe8__prereq_ifq_vn3_jlb"/>

## Prerequisites

-   You’ve created at least one subaccount and enabled the Cloud Foundry environment in this subaccount. For more information, see [Create a Subaccount](Create_a_Subaccount_05280a1.md).

-   You've downloaded and installed the Cloud Foundry command-line interface \(cf CLI\).

    For more information, see [Download and Install the Cloud Foundry Command Line Interface](Download_and_Install_the_Cloud_Foundry_Command_Line_Interface_4ef907a.md).

-   Your administrator has configured your Cloud Foundry environment to use a custom identity provider.

    For more information, see [Establish Trust and Federation of Custom Identity Providers for Platform Users in Multi-Environment Subaccounts \[Feature Set A\]](Establish_Trust_and_Federation_of_Custom_Identity_Providers_for_Platform_Users_in_Multi-Environment_Subaccounts_Feature_Set_A_8600afb.md).

-   You've configured the login screen to display your custom identity provider, see [Log on with a Browser to the Cloud Foundry User Account and Authentication service](Log_on_with_a_Browser_to_the_Cloud_Foundry_User_Account_and_Authentication_service_7eb0943.md) \(relevant for the manual login process\).


> ### Restriction:  
> Trial accounts don't support the use of a custom identity provider.



<a name="loiod477618e861c48d2976e03f9b6a3cfe8__context_cxm_sqx_1mb"/>

## Context

The cf CLI provides different options to log on using a custom IdP. One scenario is recommended for an interactive logon because you must switch from the CLI to the browser to log on. The other scenario is focused on automation scenarios where switching between the CLI and a browser isn’t possible.



<a name="loiod477618e861c48d2976e03f9b6a3cfe8__steps_jd3_dd3_jlb"/>

## Procedure

1.  Decide which scenario applies to you according to this table.


    <table>
    <tr>
    <th>

    Scenario


    
    </th>
    <th>

    See


    
    </th>
    </tr>
    <tr>
    <td>

    **You can open a browser during the logon process.**


    
    </td>
    <td>

     [Log On Manually With a Custom Identity Provider](Log_On_Manually_With_a_Custom_Identity_Provider_e1009b4.md).


    
    </td>
    </tr>
    <tr>
    <td>

    **     The logon process is automated, for example with a script or there’s no possibility to open a browser during logon.
    
         > ### Restriction:  
        > This scenario is only supported if the users exist directly in your tenant of the SAP Cloud Identity Services - Identity Authentication and not in a corporate identity provider.
    
     **


    
    </td>
    <td>

     [Set Up Automated Logon with a Custom Identity Provider](Set_Up_Automated_Logon_with_a_Custom_Identity_Provider_98ec56a.md) 


    
    </td>
    </tr>
    </table>
    

-   **[Log On Manually With a Custom Identity Provider](Log_On_Manually_With_a_Custom_Identity_Provider_e1009b4.md "To log on to Cloud
                                Foundry, using a custom identity provider
		(IdP), use the single sign-on option of the CF CLI. During logon, the system provides you with a URL to your custom IdP for you to enter in a
		web browser. If you’re already logged on to your custom IdP, the system provides a temporary authentication code to complete your logon. If
		you don't have an active session with your custom IdP, you need to log on to receive the temporary authentication code.")**  
To log on to Cloud Foundry, using a custom identity provider \(IdP\), use the single sign-on option of the CF CLI. During logon, the system provides you with a URL to your custom IdP for you to enter in a web browser. If you’re already logged on to your custom IdP, the system provides a temporary authentication code to complete your logon. If you don't have an active session with your custom IdP, you need to log on to receive the temporary authentication code.
-   **[Set Up Automated Logon with a Custom Identity Provider](Set_Up_Automated_Logon_with_a_Custom_Identity_Provider_98ec56a.md "To log on to Cloud
                                Foundry, using a custom identity provider
		(IdP), use the --origin option of the Cloud
                                Foundry
		command-line interface (cf CLI).")**  
To log on to Cloud Foundry, using a custom identity provider \(IdP\), use the `--origin` option of the Cloud Foundry command-line interface \(cf CLI\).

**Related Information**  


[Log on with a Browser to the Cloud Foundry User Account and Authentication service](Log_on_with_a_Browser_to_the_Cloud_Foundry_User_Account_and_Authentication_service_7eb0943.md "Platform users of the Cloud Foundry environment have the option to log on with a custom identity provider or the default identity provider.")

