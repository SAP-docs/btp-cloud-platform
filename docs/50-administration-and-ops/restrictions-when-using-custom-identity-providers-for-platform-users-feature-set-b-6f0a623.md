<!-- loio6f0a623807b541a0aef41f3d65c7a0fa -->

# Restrictions When Using Custom Identity Providers for Platform Users \[Feature Set B\]

The following is a list of restrictions that apply to the use of custom identity providers with platform users in Feature Set B.



<a name="loio6f0a623807b541a0aef41f3d65c7a0fa__table_n5p_1lm_5lb"/>Supported with Restrictions When Using Custom Identity Providers for Platform Users \[Feature Set B\]


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

Each user is allowed a maximum of 10 parallel sessions, per identity provider. This number takes into account all tools, including the cockpit and CLIs.

> ### Note:  
> When accessing the cockpit, a user is allowed one session in each region. For example, if you access [https://cockpit.eu10.hana.ondemand.com/cockpit/](https://cockpit.eu10.hana.ondemand.com/cockpit/), it counts as the first session and [https://cockpit.eu20.hana.ondemand.com/cockpit/](https://cockpit.eu20.hana.ondemand.com/cockpit/) as the second one.



</td>
</tr>
<tr>
<td valign="top">

Single logout \(SLO\)



</td>
<td valign="top">

For platform users of custom identity providers, logging out from the SAP BTP cockpit terminates any sessions in the Neo subaccount cockpit too. When you trigger a logout from a Neo subaccount cockpit, the session in the SAP BTP cockpit remains active. The Identity Authentication service does not propagate logout requests to OpenID Connect \(OIDC\) applications \(like the SAP BTP cockpit\), but only to other SAML applications \(like the Neo cockpit\).



</td>
</tr>
<tr>
<td valign="top">

Working with custom domains for an Identity Authentication tenant



</td>
<td valign="top">

SAP BTP always uses the default domain of the Identity Authentication tenant, regardless of a potentially configured custom domain. Therefore, when you use this tenant as a platform identity provider:

-   Single sign-on \(SSO\) does not work between applications that use this custom domain and cloud management tools. Exception: if you use the same Identity Authentication tenant for both platform and business users, as custom domain is a tenant setting.

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

The Neo CLI isn't supported with custom platform identity providers.



</td>
</tr>
<tr>
<td valign="top">

 Neo Git service



</td>
<td valign="top">

Logging on with a password to the Neo Git service doesn't work with custom platform identity providers.



</td>
</tr>
<tr>
<td valign="top">

Creating service instances of the SAP Authorization and Trust Management service with the ***apiaccess*** service plan



</td>
<td valign="top">

To create service instances of the SAP Authorization and Trust Management service with the ***apiaccess*** service plan, you must use a user from the default identity provider.

For more information, see [Access UAA Admin APIs](access-uaa-admin-apis-ebc9113.md).



</td>
</tr>
</table>

