<!-- loioe48e486f70d543e399db40354fdc2ac3 -->

# Log in with a Custom Identity Provider



## Context

If trust is configured between your global account and a custom identity provider, you need to use the `--idp` parameter to log in through this identity provider. As value, you provide its tenant ID. To retrieve the required value, you can use `btp list security/trust` and check the *Tenant* column. Or you can use the Global Account view of the cockpit under *Security* → *Trust Configuration* → *Custom Platform Identity Providers* and use the value from the *BTP CLI* column.

> ### Note:  
> To work with users from a custom identity provider, you need to specify the `--of-idp` parameter by providing the origin key of the custom identity provider. This is applicable to the following commands: `btp list security/user`, `btp get security/user`, `btp delete security/user`, `btp assign security/role-collection`, `btp unassign security/role-collection`, and you find this origin key in the cockpit under *Security*.

To learn how to configure trust to a custom identity provider, see [Establish Trust and Federation of Custom Identity Providers for Platform Users](establish-trust-and-federation-of-custom-identity-providers-for-platform-users-c368984.md) or the command help of [btp create security/trust](https://help.sap.com/docs/BTP/btp-cli/btp-create-security-trust.html).

> ### Restriction:  
> Keep in mind that each user is allowed a maximum of 10 parallel sessions per identity provider. This number takes into account all tools, including the cockpit and CLIs.
> 
> For more information, see [Restrictions When Using Custom Identity Providers for Platform Users](restrictions-when-using-custom-identity-providers-for-platform-users-6f0a623.md).



## Procedure

1.  To make use of single sign-on, log in with:

    ```
    btp login --sso --idp <TENANT>
    ```

2.  To provide user and password on the command line, log in with:

    ```
    btp login --idp <TENANT>
    ```

    You will be promped for all required login information.


**Related Information**  


[Establish Trust and Federation of Custom Identity Providers for Platform Users](establish-trust-and-federation-of-custom-identity-providers-for-platform-users-c368984.md "You want to use a custom identity provider for the platform users of SAP BTP in different environments and at the different account levels: global account, directory, and subaccount. By default, platform users in multi-environment subaccounts are users in the default identity provider.")

[Trust and Federation with Identity Providers](trust-and-federation-with-identity-providers-cb1bc8f.md "")

[Log in](log-in-e241b30.md "Log in with the btp CLI is on global account level.")

