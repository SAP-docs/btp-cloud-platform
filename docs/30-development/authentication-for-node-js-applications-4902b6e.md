<!-- loio4902b6e66cbd42648b5d9eaddc6a363d -->

# Authentication for Node.js Applications

A collection of Node.js packages developed by SAP is provided as part of the Cloud Foundry environment at SAP BTP.



SAP BTP includes a selection of standard Node.js packages, which are available for download and use from the SAP NPM public registry to customers and partners. SAP BTP only includes the Node.js packages with long-time support \(LTS\). For more information, see [https://nodejs.org](https://nodejs.org). Enabling access to an NPM registry requires configuration using the SAP NPM Registry.

-   Besides the standard NPM Package Manager, you can use the NPM Package Manager to download the packages from the npm repository.

    [https://registry.npmjs.org](https://registry.npmjs.org)

-   As an alternative option, you can use the `SAP CLIENT LIB 1.0`. Search for the software component named `SAP CLIENT LIB 1.0` on the ONE Support Launchpad.

    [ONE Support Launchpad](https://support.sap.com/swdc)


The `SAP CLIENT LIB 1.0` package contains the following modules:

> ### Tip:  
> For more details of the package contents, see the `README` file in the corresponding package.

<a name="loio4902b6e66cbd42648b5d9eaddc6a363d__table_hpz_1gt_vt"/>Contents of SAP CLIENT LIB 1.0


<table>
<tr>
<th valign="top">

Package Name



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 [`@sap/approuter`](authentication-for-node-js-applications-4902b6e.md#loio4902b6e66cbd42648b5d9eaddc6a363d__section_zrn_flt_vt) 



</td>
<td valign="top">

The application router is the single entry point for the \(business\) application.



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/xssec`](authentication-for-node-js-applications-4902b6e.md#loio4902b6e66cbd42648b5d9eaddc6a363d__section_atx_2vt_vt) 



</td>
<td valign="top">

The client security library, including the XS advanced container security API for Node.js



</td>
</tr>
</table>



<a name="loio4902b6e66cbd42648b5d9eaddc6a363d__section_zrn_flt_vt"/>

## @sap/approuter

The application router is the single entry point for the \(business\) application. It has the responsibility to serve static content, authenticate users, rewrite URLs, and proxy requests to other micro services while propagating user information.

For more information, see the applications section of SAP BTP.



<a name="loio4902b6e66cbd42648b5d9eaddc6a363d__section_atx_2vt_vt"/>

## @sap/xssec

The client security library includes the container security API for Node.js.

Authentication for node applications relies on the usage of the OAuth 2.0 protocol, which is based on central authentication at the User Account and Authentication \(UAA\) server that then vouches for the authenticated user's identity by means of a so-called OAuth access token. The implementation uses as access token a JSON web token \(JWT\), which is a signed text-based token formatted according to the JSON syntax.

The trust for the offline validation is created by binding the UAA service instance to your application. The key for validation of tokens is included in the credentials section in the environment variable *<VCAP\_SERVICES\>*. By default, the offline validation check only accepts tokens intended for the same OAuth 2.0 client in the same UAAsubaccount. This makes sense and covers the majority of use cases. However, if an application needs to consume tokens that were issued either for different OAuth 2.0 clients or for different subaccounts, you can specify a dedicated access control list \(ACL\) entry in an environment variable named *<SAP\_JWT\_TRUST\_ACL\>*. The name of the OAuth 2.0 client has the prefix `sb-`. The content is a JSON string. It contains an array of subaccounts and OAuth 2.0 clients. To establish trust with other OAuth 2.0 clients and/or subaccounts, specify the relevant OAuth 2.0 client IDs and subaccounts.

> ### Caution:  
> For testing purposes, use an asterisk \(`*`\). This setting should never be used for productive applications.

Subaccounts are not used for on-premise systems. The value for the subaccount is `uaa`.

***SAP\_JWT\_TRUST\_ACL: \[ \{"clientid":"<OAuth\_2.0\_client\_ID\>","***subaccount***":"<*** subaccount***\>"\},...\]***

> ### Caution:  
> The client libraries \(java-security, spring-xsuaa, and container security api for node.js \>= 3.0.6\) have been updated. When using these libraries, setting the parameter `SAP_JWT_TRUST_ACL` has become obsolete. This update comes with a change regarding scopes. For a business application A that wants to call an application B, it's now mandatory that application B grants at least one scope to the calling business application A. Furthermore business application A has to accept these granted scopes or authorities as part of the application security descriptor. You can grant scopes with the `xs-security.json` file. For more information, see [Application Security Descriptor Configuration Syntax](application-security-descriptor-configuration-syntax-517895a.md), specifically the sections "Referencing the Application" and "Authorities".

In a typical deployment scenario, your node application consists of several parts, which appear as separate application modules in your manifest file, for example:

-   Application logic

    This application module \(<code><i class="varname">&lt;myAppName&gt;</i>/js/</code>\) contains the application logic: code written in Node.js. This module can make use of this *XS Advanced Container Security API* for Node.js\).

-   UI client

    This application module \(<code><i class="varname">&lt;myAppName&gt;</i>/web/</code>\) is responsible for the UI layer; this module can make use of the application router functionality \(defined in the file `xs-app.json`\).


> ### Note:  
> The application logic written in Node.js and the application router should be bound to one and the same UAA service instance so that these two parts use the same OAuth client credentials.

To use the capabilities of the container security API, add the module “`@sap/xssec`” to the dependencies section of your application's `package.json` file.

> ### Note:  
> To enable tracing, set the environment variable `DEBUG` as follows: `DEBUG=xssec:*`.



### Usage

All SAP modules, for example `@sap/xssec`, are located in the namespace of the SAP NPM registry. For this reason, you must use the SAP NPM registry and the default NPM registry.

Path to the NPM registries:


<table>
<tr>
<th valign="top">

NPM Registry



</th>
<th valign="top">

Path



</th>
</tr>
<tr>
<td valign="top">

SAP NPM registry



</td>
<td valign="top">

 `@sap:registry = "https://registry.npmjs.org` 



</td>
</tr>
<tr>
<td valign="top">

Default NPM registry



</td>
<td valign="top">

 `registry = "http://registry.npmjs.org/"` 



</td>
</tr>
</table>

If you use express and passport, you can easily plug a ready-made authentication strategy.

> ### Sample Code:  
> ```
> var express = require('express');
> var passport = require('passport');
> var JWTStrategy = require('@sap/xssec').JWTStrategy;
> var xsenv = require('@sap/xsenv'); 
> 
> ...
> 
> var app = express();
> 
> ...
> 
> passport.use(new JWTStrategy(xsenv.getServices({uaa:{tag:'xsuaa'}}).uaa));
> 
> app.use(passport.initialize());
> app.use(passport.authenticate('JWT', { session: false }));
> ```

We recommend that you disable the session as in the example above. Each request comes with a JWT token so it is authenticated explicitly and identifies the user. If you still need the session, you can enable it but then you should also implement user serialization/deserialization and some sort of session persistency.



### Container Security API

> ### Tip:  
> For more details of the package contents, see the `README` file in the corresponding package.

<a name="loio4902b6e66cbd42648b5d9eaddc6a363d__table_ukv_l1n_wt"/>Container Security API


<table>
<tr>
<th valign="top">

API



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `createSecurityContext` 



</td>
<td valign="top">

Creates the “security context” by validating the received access token against credentials put into the application's environment via the UAA service binding

Returns a structure with the following properties:

-   `getLogonName`

-   `getGivenName`

-   `getFamilyName`

-   `getEmail`

-   `getHdbToken`

-   `getAdditionalAuthAttribute`

-   `getExpirationDate`

-   `getGrantType`




</td>
</tr>
<tr>
<td valign="top">

 `checkLocalScope` 



</td>
<td valign="top">

Checks a scope that is published by the current application in the `xs-security.json` file



</td>
</tr>
<tr>
<td valign="top">

 `checkScope` 



</td>
<td valign="top">

Checks a scope that is published by an application



</td>
</tr>
<tr>
<td valign="top">

 `getToken` 



</td>
<td valign="top">

Returns a token that can be used to connect to the SAP HANA database. If the token that the security context has been instantiated with is a foreign token \(meaning that the OAuth client contained in the token and the OAuth client of the current application do not match\), “`null`” is returned instead of a token; the following attributes are available:

-   `namespace`

    Tokens can be used in different contexts, for example, to access the SAP HANA database, to access another XS advanced-based service such as the Job Scheduler, or even to access other applications or containers. To differentiate between these use cases, the namespace is used. In `lib/constants.js` we define supported name spaces \(for example, `SYSTEM` \).

-   `name`

    The name is used to differentiate between tokens in a given namespace, for example, “`HDB`” for the SAP HANA database. These names are also defined in the file `lib/constants.js`.




</td>
</tr>
<tr>
<td valign="top">

 `hasAttributes` 



</td>
<td valign="top">

Returns “`true`” if the token contains any XS advanced user attributes; otherwise “`false`”.



</td>
</tr>
<tr>
<td valign="top">

 `getAttribute` 



</td>
<td valign="top">

Returns the attribute exactly as it is contained in the access token. If no attribute with the given name is contained in the access token, “`null`” is returned. If the token that the security context has been instantiated with is a foreign token \(meaning that the OAuth client contained in the token and the OAuth client of the current application do not match\), “`null`” is returned regardless of whether the requested attribute is contained in the token or not. The following attributes are available:

-   `name`

    The name of the attribute that is requested




</td>
</tr>
<tr>
<td valign="top">

 `isInForeignMode` 



</td>
<td valign="top">

Returns “`true`” if the token, that the security context has been instantiated with, is a foreign token that was not originally issued for the current application, otherwise “`false`”.



</td>
</tr>
<tr>
<td valign="top">

 `getIdentityZone` 



</td>
<td valign="top">

Returns the subaccount that the access token has been issued for.



</td>
</tr>
</table>

