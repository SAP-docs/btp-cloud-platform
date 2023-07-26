<!-- loiod477618e861c48d2976e03f9b6a3cfe8 -->

# Log On with a Custom Identity Provider to the Cloud Foundry Environment Using the Cloud Foundry Command-Line Interface

Learn how to use different methods to log on to Cloud Foundry using a custom identity provider \(IdP\).



<a name="loiod477618e861c48d2976e03f9b6a3cfe8__prereq_ifq_vn3_jlb"/>

## Prerequisites

-   You’ve created at least one subaccount and enabled the Cloud Foundry environment in this subaccount. For more information, see [Create a Subaccount](create-a-subaccount-05280a1.md).

-   You've downloaded and installed the Cloud Foundry command-line interface \(cf CLI\).

    For more information, see [Download and Install the Cloud Foundry Command Line Interface](download-and-install-the-cloud-foundry-command-line-interface-4ef907a.md).

-   Your administrator has configured your Cloud Foundry environment to use a custom identity provider.

    For more information, see [Establish Trust and Federation of Custom Identity Providers for Platform Users in Multi-Environment Subaccounts \[Feature Set A\]](establish-trust-and-federation-of-custom-identity-providers-for-platform-users-in-multi-8600afb.md) and [Establish Trust and Federation of Custom Identity Providers for Platform Users \[Feature Set B\]](establish-trust-and-federation-of-custom-identity-providers-for-platform-users-feature-c368984.md).

-   You've configured the login screen to display your custom identity provider, see [Log on with a Browser to the Cloud Foundry CLI and Service Dashboards](log-on-with-a-browser-to-the-cloud-foundry-cli-and-service-dashboards-7eb0943.md) \(relevant for the manual login process\).




<a name="loiod477618e861c48d2976e03f9b6a3cfe8__context_cxm_sqx_1mb"/>

## Context

The cf CLI provides different options to log on using a custom IdP. One scenario is recommended for an interactive logon because you must switch from the CLI to the browser to log on. This scenario supports multifactor authentication and other passwordless authentication methods, as well as single sign-on. The other scenario focuses on automation scenarios where switching between the CLI and a browser isn’t possible.



<a name="loiod477618e861c48d2976e03f9b6a3cfe8__steps_jd3_dd3_jlb"/>

## Procedure

Decide which scenario applies to you according to this table.


<table>
<tr>
<th valign="top">

Scenario



</th>
<th valign="top">

See



</th>
</tr>
<tr>
<td valign="top">

You can open a browser during the logon process.



</td>
<td valign="top">

[Log On Manually With a Custom Identity Provider](log-on-manually-with-a-custom-identity-provider-e1009b4.md).



</td>
</tr>
<tr>
<td valign="top">

The logon process is automated, for example with a script or there’s no possibility to open a browser during logon.

> ### Restriction:  
> This scenario is only supported if the users exist directly in your tenant of the SAP Cloud Identity Services - Identity Authentication and not in a corporate identity provider.



</td>
<td valign="top">

[Log On as a Technical User With a Custom Identity Provider](log-on-as-a-technical-user-with-a-custom-identity-provider-98ec56a.md) 



</td>
</tr>
</table>

**Related Information**  


[Log on with a Browser to the Cloud Foundry CLI and Service Dashboards](log-on-with-a-browser-to-the-cloud-foundry-cli-and-service-dashboards-7eb0943.md "Platform users of the Cloud Foundry environment have the option to log on with a custom identity provider or the default identity provider.")

