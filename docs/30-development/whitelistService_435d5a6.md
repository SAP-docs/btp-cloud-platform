<!-- loio435d5a66e95f441cbae4253f945bfe24 -->

# `whitelistService`

Enable the allowlist service to help prevent against click-jacking attacks.



Enabling the allowlist service \(which is called `whitelistService` in the code\) opens an endpoint accepting GET requests at the relative path configured in the `endpoint` property, as illustrated in the following example:

> ### Sample Code:  
> ```
> {
>   "whitelistService": {
>     "endpoint": "/whitelist/service"
>   }
> }
> ```

If the allowlist service is enabled in the application router, each time an HTML page needs to be rendered in a frame, the allowlist service is used check if the parent frame is allowed to render the content in a frame.



### Host Names and Domain Names

The allowlist service reads a list of allowed host names and domains defined in the environment variable *<CJ\_PROTECT\_WHITELIST\>*; the content is a JSON list of objects with the following properties:

<a name="loio435d5a66e95f441cbae4253f945bfe24__table_dhz_41z_lv"/>Allowlist of Host and Domain Names


<table>
<tr>
<th valign="top">

Property



</th>
<th valign="top">

Type



</th>
<th valign="top">

Mandatory



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `protocol` 



</td>
<td valign="top">

String



</td>
<td valign="top">

No



</td>
<td valign="top">

URI scheme, for example “HTTP”.



</td>
</tr>
<tr>
<td valign="top">

 `host` 



</td>
<td valign="top">

String



</td>
<td valign="top">

Yes



</td>
<td valign="top">

A valid host name, for example, `acme.com.hostname`, or a domain name defined with an asterisk \(\*\) `*.acme.com`.



</td>
</tr>
<tr>
<td valign="top">

 `port` 



</td>
<td valign="top">

String/Number



</td>
<td valign="top">

No



</td>
<td valign="top">

Port string or number containing a valid port.



</td>
</tr>
</table>

The following snippet shows an example of the resulting JSON array:

> ### Sample Code:  
> ```
> [
>  {
>   "protocol": "http", 
>   "host": "*.acme.com", 
>   "port": 12345 
>  },
>  {
>   "host": "hostname.acme.com"
>  }
> ]
> ```

> ### Note:  
> Matching is done against the properties provided. For example, if only host name is provided, the allowlist service returns “`framing: true`” for all, and matching will be for all schemata and protocols.



### Return Value

The allowlist service accepts only `GET` requests, and returns a JSON object as the response. The allowlist service call uses the parent origin as URI parameter \(URL encoded\) as follows:

> ### Sample Code:  
> ```
> GET url/to/whitelist/service?parentOrigin=https://parent.domain.acme.com
> 
> ```

The response is a JSON object with the following properties; property `“active”` has the value `false` only if *<CJ\_PROTECT\_WHITELIST\>* is not provided:

> ### Sample Code:  
> ```
> {
>   "version" : "1.0",
>   "active" : true | false, 
>   "origin" : "*<same as passed to service\>*", 
>   "framing" : true | false
> }
> ```

The `“active”` property enables framing control; the `“framing”` property specifies if framing should be allowed. By default, the application router \(`approuter.js`\) sends the `X-Frame-Options` header with value the `SAMEORIGIN`.

> ### Tip:  
> If the allowlist service is enabled, the header value probably needs to be changed, see the *X-Frame-Options* header section for details about how to change it.

