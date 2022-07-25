<!-- loioe48e486f70d543e399db40354fdc2ac3 -->

# Log in with a Custom Identity Provider



## Context

If trust is configured between your global account and a custom identity provider, you need to use the `--idp` parameter to log in through this identity provider. As value, you provide its tenant ID. You find the correct value in the cockpit under*Security* → *Trust Configuration* → *Custom Platform Identity Providers* in the *btp CLI* column.

> ### Note:  
> To work with users from a custom identity provider, you need to specify the `--of-idp` parameter by providing the origin key of the custom identity provider. This is applicable to the following commands: `btp list security/user`, `btp get security/user`, `btp delete security/user`, `btp assign security/role-collection`, `btp unassign security/role-collection`, and you find this origin key in the cockpit under *Security*.

For more information about using a custom identiy provider, see [Establish Trust and Federation of Custom Identity Providers for Platform Users \[Feature Set B\]](establish-trust-and-federation-of-custom-identity-providers-for-platform-users-feature-c368984.md).



## Procedure

1.  To make use of single sign-on, log in with:

    `btp login --sso --idp <TENANT>`

2.  To provide user and password on the command line, log in with:

    `btp login --idp <TENANT>`

    You will be promped for all required login information.


**Related Information**  


[Establish Trust and Federation of Custom Identity Providers for Platform Users \[Feature Set B\]](establish-trust-and-federation-of-custom-identity-providers-for-platform-users-feature-c368984.md "You want to use a custom identity provider for the platform users of SAP BTP in different environments and at the different account levels: global account, directory, and subaccount. By default, platform users in multi-environment subaccounts are users in the default identity provider.")

[Trust and Federation with Identity Providers](trust-and-federation-with-identity-providers-cb1bc8f.md "When setting up accounts you need to assign users. While we provide you with your first users to get you started, your organization has identity providers that you want to integrate.")

[Log in](log-in-e241b30.md "Log in with the btp CLI is on global account level.")

