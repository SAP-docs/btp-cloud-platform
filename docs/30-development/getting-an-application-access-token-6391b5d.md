<!-- loio6391b5dfe4704c6c8b71a32126828e9c -->

# Getting an Application Access Token

Use this API to get the application access token from the SAP Software-as-a-Service Provisioning service instance.



<a name="loio6391b5dfe4704c6c8b71a32126828e9c__section_uzn_2kq_p4b"/>

## Prerequisites

You've registered your multitenant application to the SAP SaaS Provisioning service.

For more information, see [Register the Multitenant Application to the SAP SaaS Provisioning Service](register-the-multitenant-application-to-the-sap-saas-provisioning-service-3971151.md).



## Obtaining API Request Parameters

To get the token, you call the API with the parameters obtained from the service binding object you created during the registration of your multitenant application to the SAP SaaS Provisioning service.

Use the following cf CLI command to get the service binding object:

```
cf env <APP_NAME>
```

See the step 3 in the [Register the Multitenant Application to the SAP SaaS Provisioning Service](register-the-multitenant-application-to-the-sap-saas-provisioning-service-3971151.md) to find the *<APP\_NAME\>*.

The example of the binding object you get after executing the cf CLI command, with the needed values for the API \(`clientid`, `clientsecret`, and `url`\) marked in bold:

> ### Sample Code:  
> ```
> "saas-registry": [
> {
> "credentials": {
> "apiurl": "https://api.authenticat********avlab.ondemand.com",
> "appName": "sample-saas-ap********-45",
> "appUrls": "{\"getDependencies\":\"http**********.cf.stag**":0}",
> "clientid": "sb-sample-saas-*********************-broker!b4",
> "clientsecret": "riH*************0=",
> "description": "Sample multitenant application",
> "display_name": "Sample multitenant application",
> "identityzone": "cfs******44",
> "saas_registry_url": "https://saa********ab.ondemand.com",
> "sburl": "https://internal-xsu********ndemand.com",
> "subaccountid": "3358efc9-*********10b456",
> "tenantid": "34584*******711",
> "url": "https://cfs-3035-7**********avlab.ondemand.com",
> "xsappname": "sample-saa******istry-broker!b4",
> "zoneid": "34584*******f499711"
> },
> "instance_name": "saas-app-saas-registry",
> "label": "saas-registry",
> "name": "saas-app-saas-registry",
> "plan": "application",
> }
> ]
> ```

The token you get after executing the API is a JSON Web Token \(JWT\).

For more information, see [JSON Web Token \(JWT\)](https://jwt.io/).

You use this token to manage the SAP SaaS Provisioning service APIs.



## **Request**

**URI:** <code><i class="varname">&lt;THE URL OBTAINED FROM THE BINDING OBJECT "URL" FIELD&gt;</i>/oauth/token</code>

**HTTP Method:** *POST*



### Request Headers


<table>
<tr>
<th valign="top">

Header

</th>
<th valign="top">

Required

</th>
<th valign="top">

Values

</th>
</tr>
<tr>
<td valign="top">

`Content-Type`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

*<application/x-www-form-urlencoded\>*

</td>
</tr>
<tr>
<td valign="top">

`Authorization`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Basic *<encodedString\>* where *<encodedString\>* is the result of base64 encoding the OAuth client's values as `clientId`:`clientSecret` that you obtained from the binding object as described in the previous section.

For more information about the base64 encoding, see [Base64](https://www.base64encode.org/)

</td>
</tr>
</table>



### Request Parameters


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Required

</th>
<th valign="top">

Data Type

</th>
<th valign="top">

Description

</th>
<th valign="top">

Parameter Type

</th>
</tr>
<tr>
<td valign="top">

`grant_type`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

String

</td>
<td valign="top">

The type of the authorization that is supported by the authorization server.

Set it to `client_credentials`.

</td>
<td valign="top">

Authorization protocol

</td>
</tr>
<tr>
<td valign="top">

`client_id`

</td>
<td valign="top">

No

</td>
<td valign="top">

String

</td>
<td valign="top">

The ID of the client associated with the `SaaS Provisioning` service instance.

Obtained from the service binding object. See the section Obtaining API Request Parameters of this document for details.

</td>
<td valign="top">

Relative URL path or JavaScript source code

</td>
</tr>
</table>



### Request Example \(curl for Mac OS\)

> ### Sample Code:  
> ```
> curl --location --request POST '<url>/oauth/token' \
> --header 'Content-Type: application/x-www-form-urlencoded' \
> --header 'Authorization: Basic <base64.encoded(client_id:client_secret)>' \
> --data-urlencode 'client_id=<client_id>' \
> --data-urlencode 'grant_type=client_credentials'
> ```



### Request Example \(curl for Windows OS\)

> ### Sample Code:  
> ```
> curl --location --request POST "<url>/oauth/token" ^
> --header "Content-Type: application/x-www-form-urlencoded" ^
> --header "Authorization: Basic <base64.encoded(client_id:client_secret)>" ^
> --data-urlencode "client_id=<client_id>" ^
> --data-urlencode "grant_type=client_credentials"
> ```



<a name="loio6391b5dfe4704c6c8b71a32126828e9c__section_rx5_m3p_ljb"/>

## **Response**

Generates the access token for a multitenant application.

**Content Type:** *JSON*



### Response Headers


<table>
<tr>
<th valign="top">

Header

</th>
<th valign="top">

Values

</th>
</tr>
<tr>
<td valign="top">

`Content-Type`

</td>
<td valign="top">

<application/json;charset=UTF-8\>

</td>
</tr>
</table>



### Response Status and Error Codes


<table>
<tr>
<th valign="top">

Code

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

200

</td>
<td valign="top">

Access token created successfully.

</td>
</tr>
</table>



### Response Properties


<table>
<tr>
<th valign="top">

Property Name

</th>
<th valign="top">

Property Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`access_token` 

</td>
<td valign="top">

JWT

</td>
<td valign="top">

Access token for the multitenant application.

This is the value for which you call the API

.

</td>
</tr>
<tr>
<td valign="top">

`token_type`

</td>
<td valign="top">

String

</td>
<td valign="top">

The type of access token issued.

</td>
</tr>
<tr>
<td valign="top">

`expires_in`

</td>
<td valign="top">

Number

</td>
<td valign="top">

The number of seconds until the access token expires.

</td>
</tr>
<tr>
<td valign="top">

`scope`

</td>
<td valign="top">

String

</td>
<td valign="top">

A space-delimited list of scopes that you authorized for the client.

</td>
</tr>
<tr>
<td valign="top">

`jti`

</td>
<td valign="top">

String

</td>
<td valign="top">

A globally unique identifier for JWT.

</td>
</tr>
</table>



### Response Example

> ### Sample Code:  
> ```
> HTTP/1.1 200 OK
> Content-Type: application/json;charset=UTF-8
> 
> {
>     "access_token": "eyJ***mh0d…",
>     "token_type": "bearer",
>     "expires_in": 43199,
>     "scope": "uaa.re***.subscription.read",
>     "jti": "df6cb84439a541fab33d5b7c298debe1"
> }
> 
> ```

**Related Information**  


[Using SAP SaaS Provisioning Service APIs to Manage Multitenant Applications](using-sap-saas-provisioning-service-apis-to-manage-multitenant-applications-ed08c7d.md "Use the SaaS Provisioning Service (technical name: saas-registry) APIs to work with multitenant applications.")

