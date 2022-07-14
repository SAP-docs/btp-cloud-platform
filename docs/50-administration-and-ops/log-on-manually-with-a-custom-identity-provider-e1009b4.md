<!-- loioe1009b4aa486462a8951c4d499ce6d4c -->

# Log On Manually With a Custom Identity Provider

To log on to Cloud Foundry, using a custom identity provider identity provider, use the single sign-on option of the CF CLI.



<a name="loioe1009b4aa486462a8951c4d499ce6d4c__prereq_ifq_vn3_jlb"/>

## Prerequisites

-   You've configured the login screen to display your custom identity provider.

    For more information, see [Log on with a Browser to the Cloud Foundry CLI and Service Dashboards](log-on-with-a-browser-to-the-cloud-foundry-cli-and-service-dashboards-7eb0943.md).

-   You know the origin key of the identity provider.

    For more information, see [Establish Trust and Federation of Custom Identity Providers for Platform Users in Multi-Environment Subaccounts \[Feature Set A\]](establish-trust-and-federation-of-custom-identity-providers-for-platform-users-in-multi-8600afb.md).




<a name="loioe1009b4aa486462a8951c4d499ce6d4c__context_znm_kz1_d5b"/>

## Context

During logon, the system provides you with a URL to your custom identity provider for you to enter in a web browser. If you’re already logged on to your custom identity provider, the system provides a temporary authentication code to complete your logon. If you don't have an active session with your custom IdP, you need to log on to receive the temporary authentication code.



<a name="loioe1009b4aa486462a8951c4d499ce6d4c__steps_jd3_dd3_jlb"/>

## Procedure

1.  Open a command line.

2.  Set the target API endpoint to endpoint of your subaccount.

    ```
    cf api https://api.cf.<region>.hana.ondemand.com
    ```

    > ### Sample Code:  
    > ```
    > cf api https://api.cf.eu10.hana.ondemand.com
    > ```

3.  Log on to the Cloud Foundry environment with single sign-on:

    ```
    cf login --sso
    ```

    The command-line interface displays a login URL and prompts you to enter a temporary authentication code.

4.  Open the URL that is provided on the screen to go to the logon screen.

    If this is the first time you're loging on or your browser cache has been cleaned of cookies, you're prompted to provide the origin key of your custom identity provider or choose the default identity provider.

    Otherwise the sign in page lists your accounts on custom identity providers with which you previously logged on.

5.  Choose the account of your identity provider.

    If you don't have an active session yet, you’re prompted to log on to your IdP.

    After you’ve successfully logged on, you receive a temporary authentication code.

6.  Enter the passcode.

    You’ve logged on successfully. You can now choose your org.


**Related Information**  


[Log on with a Browser to the Cloud Foundry CLI and Service Dashboards](log-on-with-a-browser-to-the-cloud-foundry-cli-and-service-dashboards-7eb0943.md "Platform users of the Cloud Foundry environment have the option to log on with a custom identity provider or the default identity provider.")

