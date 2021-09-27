<!-- loioe1009b4aa486462a8951c4d499ce6d4c -->

# Log On Manually With a Custom Identity Provider

To log on to Cloud Foundry, using a custom identity provider \(IdP\), use the single sign-on option of the CF CLI. During logon, the system provides you with a URL to your custom IdP for you to enter in a web browser. If you’re already logged on to your custom IdP, the system provides a temporary authentication code to complete your logon. If you don't have an active session with your custom IdP, you need to log on to receive the temporary authentication code.



<a name="loioe1009b4aa486462a8951c4d499ce6d4c__prereq_ifq_vn3_jlb"/>

## Prerequisites

You've configured the login screen to display your custom identity provider, see [Log on with a Browser to the Cloud Foundry User Account and Authentication service](Log_on_with_a_Browser_to_the_Cloud_Foundry_User_Account_and_Authentication_service_7eb0943.md).

> ### Restriction:  
> Trial accounts don't support the use of a custom identity provider.



<a name="loioe1009b4aa486462a8951c4d499ce6d4c__steps_jd3_dd3_jlb"/>

## Procedure

1.  Open a command line.

2.  Set the target API endpoint to endpoint of your subaccount.

    ```nocode
    cf api https://api.cf.<region>.hana.ondemand.com
    ```

    > ### Sample Code:  
    > ```nocode
    > cf api https://api.cf.eu10.hana.ondemand.com
    > ```

3.  Log on to the Cloud Foundry environment with single sign-on:

    ```nocode
    cf login --sso
    ```

    The command-line interface displays a login URL and prompts you to enter a temporary authentication code.

4.  Open the URL that is provided on the screen to go to the logon screen.

    Depending on your setup, you can now choose between different accounts, for example the default identity provider \(SAP ID service\) and your custom identity provider.

5.  Choose the account of your identity provider.

    If you don't have an active session yet, you’re prompted to log on to your IdP.

    After you’ve successfully logged on, you receive a temporary authentication code.

6.  Enter the passcode.

    You’ve logged on successfully. You can now choose your org.


**Related Information**  


[Log on with a Browser to the Cloud Foundry User Account and Authentication service](Log_on_with_a_Browser_to_the_Cloud_Foundry_User_Account_and_Authentication_service_7eb0943.md "Platform users of the Cloud Foundry environment have the option to log on with a custom identity provider or the default identity provider.")

