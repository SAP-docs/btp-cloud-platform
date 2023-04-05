<!-- loio7a37d66c2e7d401db4980db0cd74aa6b -->

# Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface

Use the Cloud Foundry Command Line Interface \(cf CLI\) to log on to the Cloud Foundry space.



<a name="loio7a37d66c2e7d401db4980db0cd74aa6b__prereq_dxb_jzc_wbb"/>

## Prerequisites

-   The Cloud Foundry environment is enabled. You can enable it in the Cloud Platform Cockpit. For more information, see [Create a Subaccount](create-a-subaccount-05280a1.md).

-   \(Enterprise accounts only\) You have created at least one subaccount and enabled the Cloud Foundry environment in this subaccount. For more information, see [Create a Subaccount](create-a-subaccount-05280a1.md).

    > ### Note:  
    > In a Cloud Foundry trial account, the Cloud Foundry environment has been activated for you automatically and a first space "dev" has been created for you.

-   Download and install the cf CLI and log on to Cloud Foundry. For more information, see [Download and Install the Cloud Foundry Command Line Interface](download-and-install-the-cloud-foundry-command-line-interface-4ef907a.md).




<a name="loio7a37d66c2e7d401db4980db0cd74aa6b__steps_k1g_2cc_nbb"/>

## Procedure

1.  Open a command line.

2.  Set the target API endpoint to the cloud controller.

    > ### Note:  
    > There is no specific endpoint for trial accounts. Both enterprise and trial accounts use the same API endpoints.

    ```
    cf api https://api.cf.eu10.hana.ondemand.com
    ```

     

    For more information, see [Regions and API Endpoints Available for the Cloud Foundry Environment](../10-concepts/regions-and-api-endpoints-available-for-the-cloud-foundry-environment-f344a57.md).

3.  Log on to the Cloud Foundry environment:

    ```
    cf login
    ```

    > ### Note:  
    > -   To log on with SAP Universal ID, use the option `--sso`. You need a browser in the logon process.
    > 
    >     For more information, see [Log On Manually With a Custom Identity Provider](log-on-manually-with-a-custom-identity-provider-e1009b4.md).
    > 
    >     Otherwise log on with the password associated with your account \(S-user or P-user\) in the default identity provider, SAP ID service.
    > 
    >     If you've forgotten this password and this user is associated with your SAP Universal ID user, reset your password.
    > 
    >     For more information, see SAP Note [3085908](https://launchpad.support.sap.com/#/notes/3085908).
    > 
    > -   To log on with a specific identity provider, use the option `--origin`.
    > 
    >     For more information, see [Log On as a Technical User With a Custom Identity Provider](log-on-as-a-technical-user-with-a-custom-identity-provider-98ec56a.md).

4.  When prompted, enter your user credentials \(email and password\). 

5.  To view the help for the CLI, execute <code><b><i>cf help</i></b></code>, which lists the most common CLI commands with a short description, or ***cf help -a***, which lists all commands. To get help for a specific command, execute <code><b><i>cf help <i class="varname">&lt;command&gt;</i></i></b></code>.


