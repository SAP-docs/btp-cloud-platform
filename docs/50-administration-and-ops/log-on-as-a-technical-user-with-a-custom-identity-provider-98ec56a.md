<!-- loio98ec56a6dd4347b6ad466aaab19ded02 -->

# Log On as a Technical User With a Custom Identity Provider

To log on to Cloud Foundry, using a custom identity provider, use the `--origin` option of the Cloud Foundry command-line interface \(cf CLI\).



## Prerequisites

The users exist:

-   Directly in your tenant of the SAP Cloud Identity Services.

-   In a corporate identity provider with SAP Cloud Identity Services working as a proxy.

    -   Trust to your SAP Cloud Identity Services tenant must be configured with OIDC and not SAML.

    -   Your corporate identity provider must support the password grant flow.


    For more information, see [Configure Trust with OpenID Connect Corporate Identity Provider](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/8ff83a12bbb8491c9558d635d6bbb287.html?version=Cloud) in the documentation for SAP Cloud Identity Services.




## Context

We recommend this method of logging on if you want to use an automated script and can't open a browser during the logon process.



## Procedure

Set up a script with the following code:

```
cf api https://api.cf.<region>.hana.ondemand.com
cf login --origin <origin> -u <user> -p <password>

```

> ### Sample Code:  
> ```
> cf api https://api.cf.eu10.hana.ondemand.com
> cf login --origin sap.ids -u julie.armstrong@sap.com -p mysecurepassword
> 
> ```

-   Find the <code><i class="varname">&lt;region&gt;</i></code> value, that applies to you in the section [Regions](../10-concepts/regions-350356d.md).

-   Find the <code><i class="varname">&lt;origin&gt;</i></code> value for the user that you want to use in the cockpit.

    1.  Navigate to the subaccount of your user.

    2.  Choose *Cloud Foundry* \> *Org Members*.

    3.  Find the <code><i class="varname">&lt;origin&gt;</i></code> value of your user in the table.



