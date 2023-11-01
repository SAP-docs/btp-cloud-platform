<!-- loio6f0a623807b541a0aef41f3d65c7a0fa -->

# Restrictions When Using Custom Identity Providers for Platform Users \[Feature Set B\]

The following is a list of restrictions that apply to the use of custom identity providers with platform users in Feature Set B.



## Supported with Restrictions When Using Custom Identity Providers for Platform Users \[Feature Set B\]

****


<table>
<tr>
<th valign="top">

Supported with Restrictions

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Maximum number of parallel sessions per user per identity provider

</td>
<td valign="top">

Each user is allowed a maximum of 10 parallel sessions, per identity provider. This number considers all tools, including the cockpit and CLIs.

> ### Note:  
> When accessing the cockpit, a user is allowed one session in each region. For example, if you access [https://emea.cockpit.btp.cloud.sap](https://emea.cockpit.btp.cloud.sap), it counts as the first session and [https://amer.cockpit.btp.cloud.sap](https://amer.cockpit.btp.cloud.sap) as the second one.



</td>
</tr>
<tr>
<td valign="top">

Single logout \(SLO\)

</td>
<td valign="top">

For platform users of custom identity providers, logging out from the SAP BTP cockpit \(including Neo cockpit\) terminates the session in the used Identity Authentication tenant and sessions of other applications that connect to the same tenant. What is required is that the sessions support this kind of logout. This requirement doesn't apply for other instances of the SAP BTP cockpit except for instances where the user initially logged out from. In this case, sessions remain active.

</td>
</tr>
</table>



<a name="loio6f0a623807b541a0aef41f3d65c7a0fa__section_tzp_msp_byb"/>

## Supported with Restrictions for Neo Subaccounts Before the Changes in the Trust Configuration

The following is a list of restrictions that only apply for Neo subaccounts when using custom identity providers for platform users.

-   All individual Neo subaccounts that have been created before July 2023.

-   Neo subaccounts in global accounts that have custom identity providers for platform users. For these subaccounts, [SAP Note 3330671](https://launchpad.support.sap.com/#/notes/3330671) hasn't been applied yet.



<table>
<tr>
<th valign="top">

Supported with Restrictions

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Working with custom domains for an Identity Authentication tenant

</td>
<td valign="top">

SAP BTP always uses the default domain of the Identity Authentication tenant, regardless of a potentially configured custom domain. Therefore, when you use this tenant as a platform identity provider:

-   Single sign-on \(SSO\) doesn't work between applications that use this custom domain and cloud management tools. Exception: if you use the same Identity Authentication tenant for both platform and business users, as custom domain is a tenant setting.

-   The OpenID Connect \(OIDC\) issuer in the *Name* field of the Identity Authentication tenant must be the default domain \(<origin\>.accounts.ondemand.com\).

    For more information, see [Tenant OpenID Connect Configurations](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/3d6abcc02ec945ad9615773e05814003.html?version=Cloud&q=UserInfo%20endpoint).




</td>
</tr>
<tr>
<td valign="top">

OpenID Connect \(OIDC\) issuer in the *Name* field of the Identity Authentication tenant

</td>
<td valign="top">

> ### Caution:  
> Don't change the *Name* field after configuring trust. Changing the issuer breaks the trust between the systems.



</td>
</tr>
<tr>
<td valign="top">

Neo CLI

</td>
<td valign="top">

No restriction for new Neo subaccounts if this [prerequisite](https://help.sap.com/docs/btp/sap-btp-neo-environment/configuring-platform-identity-provider-feature-set-b) is fulfilled.

For basic authentication, the Neo CLI has limited support for existing Neo subaccounts when using custom identity providers for platform users.

</td>
</tr>
<tr>
<td valign="top">

Neo Git service

</td>
<td valign="top">

Logging on with a password to the Neo Git service doesn't work with custom identity providers for platform users.

</td>
</tr>
<tr>
<td valign="top">

Cloud connector 

</td>
<td valign="top">

Logging on with a password to the Cloud connector doesn't work with custom identity providers for platform users.

</td>
</tr>
<tr>
<td valign="top">

SAP HANA studio 

</td>
<td valign="top">

No restriction for new Neo subaccounts if this [prerequisite](https://help.sap.com/docs/btp/sap-btp-neo-environment/configuring-platform-identity-provider-feature-set-b) is fulfilled.

</td>
</tr>
</table>

