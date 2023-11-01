<!-- loiob2a56a8a222940089fd2704a9c26140d -->

# Log in with Single Sign-On

Use the single sign-on parameter \(`btp login --sso`\) to log in to your identity provider through a browser instead of passing username and password on the command line.



<a name="loiob2a56a8a222940089fd2704a9c26140d__prereq_av4_s5p_xnb"/>

## Prerequisites

Login through a browser is only available if you use the default server URL that is proposed by the CLI during login \(`https://cli.btp.cloud.sap/`\). This is the case unless your operator has provided you specifically with a different server URL.



<a name="loiob2a56a8a222940089fd2704a9c26140d__context_xj5_nsd_15b"/>

## Context

If you have a custom identity provider configured in your global account, use `btp login --sso --idp <TENANT>`. See [Log in with a Custom Identity Provider](log-in-with-a-custom-identity-provider-e48e486.md).

> ### Tip:  
> If you like logging in through single sign-on in a browser, you can configure this as the default behavior of `btp login` to save a few keystrokes at login. Use `btp set config --login.sso browser`. See [Change Configuration Settings](change-configuration-settings-dba4eb6.md) .



## Procedure

1.  Enter the following and press [ENTER\] to be prompted for the server URL and the subdomain of your global account:

    ```
    btp login --sso
    ```

    Alternatively, you can pass the server URL and the subdomain of your global account as parameters:

    ```
    btp login --sso --url https://cli.btp.cloud.sap/ --subdomain <my-subdomain>
    ```

    To suppress the automatic browser-opening, you can run the command as follows:

    ```
    btp login --sso manual
    ```

2.  Authenticate directly at your identity provider through your browser.

    If you already have an active session, the identity provider immediately transfers a token to the client, which completes your login. Otherwise, you need to enter your credentials.




<a name="loiob2a56a8a222940089fd2704a9c26140d__result_o34_tcb_pvb"/>

## Results

You’ve successfully logged in. You can return to the command line to work in your global account or - at first login - to select the global account for login.

**Related Information**  


[Log in](log-in-e241b30.md "Log in with the btp CLI is on global account level.")

[Log in with a Custom Identity Provider](log-in-with-a-custom-identity-provider-e48e486.md "")

