<!-- loiob8c0aac0e86944cf984b672dea2f38d0 -->

# Using Multiple Identity Providers from the Same Subaccount

You need to use multiple identity providers for different groups of business users. You want to guide business users to the right identity provider for logon.

Usually there's a single identity provider, which is needed for most users.

Additional identity providers are only needed in exceptional cases.

**Basic Considerations Before You Provide a Logon Link for Business Users**


<table>
<tr>
<th valign="top">

Recommendation

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

\(Preferred\)

Try to avoid multiple trust configurations at all.

</td>
<td valign="top">

Hide the default identity provider and connect a single SAP Cloud Identity Services tenant.

Connect further identity providers as corporate identity providers in the SAP Cloud Identity Services tenant and use conditional authentication rules in SAP Cloud Identity Services.

</td>
</tr>
<tr>
<td valign="top">

\(Feasible\)

If multiple trusts are really needed in the subaccount, avoid that business users must pick a specific trust by giving them dedicated application URLs, which choose the right identity provider \(only supported by some applications\).

</td>
<td valign="top">

Some applications can be accessed using a URL that includes a query parameter to define the trust configuration for user login, instead of asking the user to choose one.

> ### Example:  
> `https://application.cfapps.eu10.hana.ondemand.com/sap_idp=some-origin-key`

Options

1.  Make sure all users access applications with such URLs.

2.  Choose one standard trust configuration as the one to be used when applications are accessed without such a query parameter. Only use the parameter when any other trust configuration should be used. To achieve this, disable *Available for User Logon* for all trust configurations other than the one you want to use as standard trust configuration.

    For more information, see [Provide Logon Link to Identity Provider for Business Users](provide-logon-link-to-identity-provider-for-business-users-8f8677c.md).


If your custom applications use application router, you can enable support for the parameter by following the application router documentation. See [Dynamic Identity Provider Configuration](https://www.npmjs.com/package/@sap/approuter#dynamic-identity-provider-configuration) or [routes](../30-development/routes-666eb55.md).

> ### Note:  
> For SaaS applications, check the application documentation to find out whether or not they support the parameter.



</td>
</tr>
<tr>
<td valign="top">

\(Exceptional\)

If business users must really choose the identity provider. Make sure the respective link texts on the login page makes sense to them, so that they can easily choose the right one.

</td>
<td valign="top">

Review the link texts of all trust configurations, where *Available for User Logon* is enabled, so that business users understand which one to choose.

For more information, see [Rename the Logon Link Text for Custom Identity Providers](rename-the-logon-link-text-for-custom-identity-providers-f0e6259.md).

</td>
</tr>
</table>

