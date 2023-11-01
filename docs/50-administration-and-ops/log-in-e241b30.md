<!-- loioe241b30195ff4d009dba3076e0ae8d27 -->

# Log in

Log in with the btp CLI is on global account level.



<a name="loioe241b30195ff4d009dba3076e0ae8d27__prereq_jwk_x1v_qhb"/>

## Prerequisites

-   Your global account must be on feature set B. See [Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md).

-   You need to pass the CLI server URL. Usually, it is proposed during login and you can confirm with [ENTER\]: `https://cli.btp.cloud.sap/`.

    Note that in clients up until version 2.49.0, the old server URL `https://cpcli.cf.eu10.hana.ondemand.com` is proposed. For the time being, you can use either one, but we recommend to switch to `https://cli.btp.cloud.sap/`. If you are in a private cloud and your operator has provided you with a different server URL, you'll have to enter that one.

-   Your user is assigned to the `Global Account Viewer` or the `Global Account Administrator` role collection. See [Role Collections and Roles in Global Accounts, Directories, and Subaccounts \[Feature Set B\]](../10-concepts/role-collections-and-roles-in-global-accounts-directories-and-subaccounts-feature-set-b-0039cf0.md).

-   To log on with SAP Universal ID, you need to log on with the single sign-on parameter \(`btp login --sso`\). If you don't want to use single sign-on, log on with the password associated with your account \(S-user or P-user\) in the default identity provider, SAP ID service. If you've forgotten this password and this user is associated with your SAP Universal ID user, reset your password.

    For more information, see SAP Note [3085908](https://me.sap.com/notes/3085908) and [Log in with Single Sign-On](log-in-with-single-sign-on-b2a56a8.md).




<a name="loioe241b30195ff4d009dba3076e0ae8d27__context_nwm_mqd_fmb"/>

## Context

When you log in to your global account with the btp CLI, a token is created and stored on your computer that allows to close and reopen the command line without losing your login. With each command call, this token is renewed and valid for 24 hours. So, if you take a longer break from working with the btp CLI, you’ll have to log in again. If you want to end your login earlier, you can use `btp logout`.



### Login with single sign-on

We recommend using single sign-on and authenticating directly at your identity provider through a web browser:

```
btp login --sso
```

See [Log in with Single Sign-On](log-in-with-single-sign-on-b2a56a8.md).



### Login with a custom identity provider

To login with a custom identity provider, use:

```
btp login --sso --idp <TENANT>
```



See [Log in with a Custom Identity Provider](log-in-with-a-custom-identity-provider-e48e486.md).



## Procedure

To log in manually, use `btp login`. The btp CLI prompts for all login information, but optionally, you can provide the required information as parameters.

Usage: `btp [OPTIONS] login [PARAMS]`

**Parameters**


<table>
<tr>
<td valign="top">

`--sso`

</td>
<td valign="top">

Opens a browser for single sign-on at the identity provider. The btp CLI doesn't prompt for this parameter. If you use SAP Universal ID, you need to use this parameter.

To suppress automatic browser opening, use `--sso manual`. To use a custom identity provider, you need to add the `--idp` parameter.

</td>
</tr>
<tr>
<td valign="top">

`--idp` *<TENANT\>*

</td>
<td valign="top">

This parameter is only needed to work with a custom identity provider. The CLI doesn't prompt for it.

If trust is configured between your global account and a custom identity provider, use this parameter to log in through this identity provider by providing its tenant ID. You find the correct value in the cockpit under *Security* → *Trust Configuration* → *Custom Platform Identity Providers* 

> ### Note:  
> To work with users from a custom identity provider, you need to specify the `--of-idp` parameter by providing the origin key of the custom identity provider. This is applicable to the following commands: `btp list security/user`, `btp get security/user`, `btp delete security/user`, `btp assign security/role-collection`, `btp unassign security/role-collection`, and you find this origin key in the cockpit under *Security*.

For more information about using a custom identity provider, see [Establish Trust and Federation of Custom Identity Providers for Platform Users \[Feature Set B\]](establish-trust-and-federation-of-custom-identity-providers-for-platform-users-feature-c368984.md).

</td>
</tr>
<tr>
<td valign="top">

`--url` *<URL\>*

</td>
<td valign="top">

The client proposes this CLI server URL: `https://cli.btp.cloud.sap/`, which you can confirm by pressing [ENTER\]. If your operator has provided you with a different server URL, you can specify it here. Note that when you enter a new server URL for the first time, you’re asked to confirm that you trust it.

</td>
</tr>
<tr>
<td valign="top">

`--user` *<USER\>*

</td>
<td valign="top">

Your user name, usually an email address.

</td>
</tr>
<tr>
<td valign="top">

`--password` *<PASSWORD\>*

</td>
<td valign="top">

Your password. If you have enabled Two-Factor-Authentication, append your token to your password.

> ### Tip:  
> We don’t recommend to provide the password with this parameter, as it appears in plain text and may be recorded in your shell history. Rather, enter it when you’re prompted.



</td>
</tr>
<tr>
<td valign="top">

`--subdomain` *<GLOBALACCOUNT\>*

</td>
<td valign="top">

In the interactive login, after successful authentication, the btp CLI will offer all of your global accounts so you can select the one to log in to.

You can also provide the global account as a parameter by specifying its subdomain. You should have obtained the subdomain from your operator; but you can also find it in the cockpit in the global account view.

![](images/cli_subdomain_dc4961c.png)

> ### Note:  
> If you don't find the subdomain of the global account in your cockpit, your global account is probably not on SAP BTP feature set B, which means you cannot access it with the btp CLI. See [Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md).



</td>
</tr>
</table>

```
btp login
```

If you've logged in before, the server URL, the subdomain, and the user from the last login are suggested. You can then press [Enter\] to confirm, or type in different values.

```
CLI server URL [https://cpcli.cf.eu10.hana.ondemand.com]>
Subdomain [my-global-account]>
User [name@example.com]>
```



<a name="loioe241b30195ff4d009dba3076e0ae8d27__result_yvj_3hy_m3b"/>

## Results

Upon successful login, the btp CLI creates a folder \(`btp`\) and a configuration file \(`config.json`\) in the default location of your user data directory:

-   Microsoft Windows: <code>C:\Users\<i class="varname">&lt;username&gt;</i>\AppData\Roaming\SAP\btp\config.json</code>

-   Apple macOS ; `~/Library/Application Support/.btp/config.json`

-   Linux: `~/.config/.btp/config.json`


To change this location, use the `--config` option or the environmnet variable. See [Specify the Location of the Configuration File](specify-the-location-of-the-configuration-file-e57288d.md).

> ### Tip:  
> You’ve logged in to the global account and all commands are executed in this global account, unless you provide a subaccount or directory ID with the command. To change this default context for subsequent commands, you can target a subaccount or directory, or even a different global account by using `btp target`. See [Set a Target for Subsequent Commands with btp target](set-a-target-for-subsequent-commands-with-btp-target-720645a.md).

**Related Information**  


[btp CLI Command Reference](https://help.sap.com/docs/BTP/btp-cli/intro.html)

