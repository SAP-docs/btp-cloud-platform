<!-- loiob2a56a8a222940089fd2704a9c26140d -->

# Log in with Single Sign-On

Use the single sign-on parameter \(`btp login --sso`\) to log in to your identity provider through a browser instead of passing username and password on the command line.



<a name="loiob2a56a8a222940089fd2704a9c26140d__prereq_av4_s5p_xnb"/>

## Prerequisites

Login through a browser is only available if you use the default server URL that is proposed by the CLI during login \(`https://cpcli.cf.eu10.hana.ondemand.com`\). This is the case unless your operator has provided you specifically with a different server URL.



## Procedure

1.  Enter the following and press [ENTER\] to be prompted for the server URL and the subdomain of your global account:

    ```
    btp login --sso
    ```

    Alternatively, you can pass the server URL and the subdomain of your global account as parameters:

    ```
    btp login --sso --url https://cpcli.cf.eu10.hana.ondemand.com --subdomain <my-subdomain>
    ```

    To suppress the automatic browser-opening, you can run the command as follows:

    ```
    btp login --sso manual
    ```

2.  Authenticate directly at SAP ID service through your browser.

    If you already have an active session, the identity provider immediately transfers a token to the client, which completes your login. Otherwise, you need to enter your credentials.

    You’ve successfully logged in. You can return to the command line to work in your global account.


**Related Information**  


[Log in](log-in-e241b30.md "Log in with the btp CLI is on global account level.")

