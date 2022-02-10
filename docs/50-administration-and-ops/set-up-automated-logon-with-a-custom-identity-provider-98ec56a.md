<!-- loio98ec56a6dd4347b6ad466aaab19ded02 -->

# Set Up Automated Logon with a Custom Identity Provider

To log on to Cloud Foundry, using a custom identity provider \(IdP\), use the `--origin` option of the Cloud Foundry command-line interface \(cf CLI\).



<a name="loio98ec56a6dd4347b6ad466aaab19ded02__prereq_ifq_vn3_jlb"/>

## Prerequisites

Users exist directly in your tenant of the SAP Cloud Identity Services - Identity Authentication and not in a corporate identity provider, such as a Microsoft Active Directory.

> ### Restriction:  
> Trial accounts don't support the use of a custom identity provider.



## Context

We recommend this method of logging on if you want to use an automated script and can't open a browser during the logon process.



## Procedure

1.  Set up a script with the following code:

    ```nocode
    cf api https://api.cf.<region>.hana.ondemand.com
    cf login --origin <origin> -u <user> -p <password>
    
    ```

    > ### Sample Code:  
    > ```nocode
    > cf api https://api.cf.eu10.hana.ondemand.com
    > cf login --origin sap.ids -u julie.armstrong@sap.com -p mysecurepassword
    > 
    > ```

    -   Find the <code><i class="varname">&lt;region&gt;</i></code> value, that applies to you in the section [Regions](../10-concepts/regions-350356d.md).

    -   Find the <code><i class="varname">&lt;origin&gt;</i></code> value for the user that you want to use in the cockpit.

        1.  Navigate to the subaccount of your user.

        2.  Choose *Members*.

        3.  Find the <code><i class="varname">&lt;origin&gt;</i></code> value of your user in the table.


    -   If two-factor authentication is enabled, concatenate your password and the passcode in a single string.



