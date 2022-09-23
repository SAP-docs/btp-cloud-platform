<!-- loio5ec1e970eb0d417c969f1693da31388f -->

# Single Sign-On Configuration JSON File

Use the single sign-on \(SSO\) configuration JSON file to define the assertion consumer services in SAP SuccessFactors for the subaccount in SAP BTP and for each extension application you have deployed in SAP BTP that is extending the SAP SuccessFactors system functionality.



> ### Note:  
> The content of the JSON file must be up to 5120 characters without spaces.


<table>
<tr>
<th valign="top">

Parameter



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

`systemName`



</td>
<td valign="top">

The name of the system you have registered in the global account in SAP BTP

**Rules/Guidelines**

The name must be the same as the one defined during the system registration in the global account. See [Register an SAP SuccessFactors System in a Global Account in SAP BTP](register-an-sap-successfactors-system-in-a-global-account-in-sap-btp-e956ba2.md).

> ### Note:  
> The system must be in status *Registered*.



</td>
</tr>
<tr>
<td valign="top">

`logoutURLs`



</td>
<td valign="top">

\(Optional\) This is a list of the logout URLs. A logout URL is the absolute URL that corresponds to the URL of the application router with the appended value of the `logoutEndpoint` property. See [logout](../30-development/logout-2296b4d.md).

> ### Note:  
> Make sure that the value of the `logoutMethod` property is set to ***GET*** in the *xs-app.json* file.

> ### Note:  
> The `SameSite` attribute of the `Set-Cookie` HTTP response header needs to be set to `None` so that the cookies are sent in all responses to both first-party and cross-origin requests. You also need to set the cookie `Secure` attribute, because it requires a secure context/HTTPS. See [Environment Variables](../30-development/environment-variables-ba52705.md).

> ### Note:  
> If you don't specify the `logoutURLs` parameter, only an assertion consumer service for the subaccount in SAP BTP will be created.



</td>
</tr>
</table>

> ### Sample Code:  
> ```
> {
>     "systemName": "MY_SYSTEM",
>     "logoutURLs": ["https://my-first-site.com/logout", "https://my-second-site.com/logout"]
> }
> ```

