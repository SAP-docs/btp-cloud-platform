<!-- loiod8f4b7c7298a422183beddb4ad47c108 -->

# Auditing and Logging Information for SAP Authorization and Trust Management Service

Here you can find a list of the security events that are logged by SAP Authorization and Trust Management service \(XSUAA\). These events are provided in addition to the events of the Cloud Foundry User Account and Authentication service \(UAA\).



<a name="loiod8f4b7c7298a422183beddb4ad47c108__section_xmv_pfp_spb"/>

## Security Events of the User Account and Authentication Service

For information about the security events of the UAA, see [UAA Audit Requirements](https://docs.cloudfoundry.org/running/managing-cf/uaa-audit-requirements.html) in the Cloud Foundry documentation.



<a name="loiod8f4b7c7298a422183beddb4ad47c108__section_ekp_ggp_spb"/>

## Security Events of the SAP Authorization and Trust Management Service

In cloud management tools feature set A, account management and role assignments, such as for the security administrator, are managed by SAP Authorization and Trust Management service in the Neo environment. For more information about audit logging in the Neo environment, see the related links at the end of this document.

In cloud management tools feature set B, SAP Authorization and Trust Management service uses role collections to handle account management.

SAP Authorization and Trust Management service records all its changes in its database tables and summarizes these changes in the audit log. The following table summarizes the audit log entries.

**Security Events Written in Audit Logs**


<table>
<tr>
<th valign="top">

Event grouping



</th>
<th valign="top">

What events are logged



</th>
<th valign="top">

How to identify related log events



</th>
<th valign="top">

Additional information



</th>
</tr>
<tr>
<td valign="top" rowspan="6">

Identity provider management



</td>
<td valign="top" rowspan="2">

Trust identity provider.



</td>
<td valign="top">

`object with type "IdentityProvider" and id consisting of: crudType "CREATE"` 



</td>
<td valign="top">

Attributes of the identity provider.



</td>
</tr>
<tr>
<td valign="top">

`tableName "xs_tenant", crudType "UPDATE"` 



</td>
<td valign="top">

Trusting an identity provider using OpenID Connect triggers a change in the XSUAA tenant.



</td>
</tr>
<tr>
<td valign="top" rowspan="2">

Update trust with identity provider.



</td>
<td valign="top">

`object with type "IdentityProvider" and id consisting of: crudType "UPDATE"` 



</td>
<td valign="top">

Old attributes of the identity provider and any attributes required to identify the changes.



</td>
</tr>
<tr>
<td valign="top">

`tableName "xs_tenant", crudType "UPDATE"` 



</td>
<td valign="top">

Updating trust in an identity provider using OpenID Connect can trigger a change in the XSUAA tenant.



</td>
</tr>
<tr>
<td valign="top" rowspan="2">

Delete trust with identity provider.



</td>
<td valign="top">

`object with type "IdentityProvider" and id consisting of: crudType "DELETE"` 



</td>
<td valign="top">

Attributes of the service instance.



</td>
</tr>
<tr>
<td valign="top">

`tableName "xs_tenant", crudType "UPDATE"` 



</td>
<td valign="top">

Removing trust in an identity provider using OpenID Connect triggers a change in the XSUAA tenant.



</td>
</tr>
<tr>
<td valign="top" rowspan="4">

Instance management



</td>
<td valign="top">

Create instance.



</td>
<td valign="top">

<code>Attribute with name "complete" and value ""ServiceInstanceId: <i class="varname">&lt;Instance_ID&gt;</i></code>

…

<code>object with type "<i class="varname">&lt;Instance_Name&gt;</i>" and id consisting of: crudType "CREATE"</code>



</td>
<td valign="top">

Attributes of the service instance.



</td>
</tr>
<tr>
<td valign="top">

Update instance.



</td>
<td valign="top">

<code>Attribute with name "complete" and value ""ServiceInstanceId: <i class="varname">&lt;Instance_ID&gt;</i></code>

…

<code>object with type "<i class="varname">&lt;Instance_Name&gt;</i>" and id consisting of: crudType "UPDATE"</code>



</td>
<td valign="top">

Old attributes of the service instance and any attributes required to identify the changes.



</td>
</tr>
<tr>
<td valign="top">

Delete instance.



</td>
<td valign="top">

<code>Attribute with name "complete" and value ""ServiceInstanceId: <i class="varname">&lt;Instance_ID&gt;</i></code>

…

<code>object with type "<i class="varname">&lt;Instance_Name&gt;</i>" and id consisting of: crudType "DELETE"</code>



</td>
<td valign="top">

Attributes of the service instance.



</td>
</tr>
<tr>
<td valign="top" colspan="3">

> ### Note:  
> If you create a new binding secret for the service instance, a new binding entry is created in the SAP Authorization and Trust Management service. This entry then appears in the audit log of the subaccount of the service instance. The audit log of the subaccount of the reuse service itself isn't affected.



</td>
</tr>
<tr>
<td valign="top" rowspan="4">

Role collection management



</td>
<td valign="top">

Create role collection.



</td>
<td valign="top">

`tableName "xsrolecollections", crudType "CREATE"`

audit.configuration



</td>
<td valign="top">

Other attributes:

-   Timestamp

-   Origin key

-   Role collection name

-   Zone ID




</td>
</tr>
<tr>
<td valign="top">

Assign users to role collection.



</td>
<td valign="top">

Direct assignment to users: `tableName "xs_rolecollection2user", crudType "CREATE"`

Mapping to users with attributes: `tableName "xsrolecollection2samlattribute", crudType "CREATE"`

audit.configuration



</td>
<td valign="top">

Other attributes for direct assignment:

-   Timestamp

-   Origin key

-   User SCIM ID

-   Zone ID

-   Role collection name


Other attributes for mapping:

-   Timestamp

-   Origin key

-   Attribute name

-   Attribute value

-   Identity provider URL

-   Zone ID

-   Role collection name




</td>
</tr>
<tr>
<td valign="top">

Assign roles to role collection.



</td>
<td valign="top">

`tableName "xsrolecollection2role", crudType "CREATE"` 



</td>
<td valign="top">

-   Timestamp

-   Origin key

-   Role name

-   Role zone ID

-   Role template name

-   Role collection zone ID

-   Role template app ID

-   Role collection name




</td>
</tr>
<tr>
<td valign="top">

Delete role collection.



</td>
<td valign="top">

`tableName "xsrolecollections", crudType "DELETE"`

audit.configuration



</td>
<td valign="top">

Other attributes:

-   Timestamp

-   Origin key

-   Role collection name

-   Zone ID




</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Role management



</td>
<td valign="top">

Create role.



</td>
<td valign="top">

`tableName "xsrole", crudType "CREATE"`

audit.configuration



</td>
<td valign="top">

Other attributes:

-   Timestamp

-   Origin key

-   App ID

-   Role name

-   Role template name

-   Zone ID




</td>
</tr>
<tr>
<td valign="top">

Modify attribute values in role.



</td>
<td valign="top">

`tableName "xsattribute2role", crudType "CREATE"`

audit.configuration



</td>
<td valign="top">

Other attributes:

-   Timestamp

-   Origin key

-   Role name

-   Zone ID

-   Attribute app ID

-   Role template name

-   Attribute name

-   Attribute value

-   Role template app ID




</td>
</tr>
<tr>
<td valign="top">

Delete role.



</td>
<td valign="top">

`tableName "xsrole", crudType "DELETE"`

audit.configuration



</td>
<td valign="top">

Other attributes:

-   Timestamp

-   Origin key

-   Role template app ID

-   Role name

-   Role template name

-   Zone ID




</td>
</tr>
<tr>
<td valign="top">

Token Embedding



</td>
<td valign="top">

Embedding error



</td>
<td valign="top">

`Error during handling of IAS Tokens for embedding.`

audit.security-events



</td>
<td valign="top">

Occurs when an error occurs when attempting to exchange a token for a token with an embedded token from Identity Authentication or a corporate identity provider. Check the configuration of the application.

For more information, see [Include Tokens from Corporate Identity Providers or Identity Authentication in Tokens of the SAP Authorization and Trust Management Service](../30-development/include-tokens-from-corporate-identity-providers-or-identity-authentication-in-tokens-of-8dc480a.md).



</td>
</tr>
<tr>
<td valign="top" rowspan="7">

SAML authentication



</td>
<td valign="top" rowspan="5">

Authentication error



</td>
<td valign="top">

`SAMLAuthenticationError`

<code>Response issue time is either too old or with date in the future. Sync IdP to match skew <i class="varname">&lt;skew&gt;</i></code>

audit.security-events



</td>
<td valign="top">

Occurs when the time skew between SAP Authorization and Trust Management service and the identity provider is larger than 60 seconds. Or the authentication response took more than 60 seconds to reach the SAP Authorization and Trust Management service after being issued.

Check the time skew between the identity provider and SAP Authorization and Trust Management service. Synchronize the clock of the identity provider.



</td>
</tr>
<tr>
<td valign="top">

`SAMLAuthenticationError`

<code>Unexpected AuthnResponse : Existing authentication - <i class="varname">&lt;user&gt;</i></code>

audit.security-events



</td>
<td valign="top">

The user has probably chosen the back button on the browser, triggering a second authentication request to the identity provider with the same user ID. The identity provider issues a second authentication response for the same user ID. SAP Authorization and Trust Management service rejects duplicate responses.



</td>
</tr>
<tr>
<td valign="top">

`SAMLAuthenticationError`

<code>AuthnRequest expired - ID: <i class="varname">&lt;request_id&gt;</i> Destination: <i class="varname">&lt;identity_provider_destination&gt;</i></code>

audit.security-events



</td>
<td valign="top">

Occurs when an authentication response from an identity provider takes more than 15 minutes.

If this error occurs consistently, check why the identity provider needs more than 15 minutes to issue an authentication response.



</td>
</tr>
<tr>
<td valign="top">

`SAMLAuthenticationError`

`InResponseToField of Response doesn‘t correspond to the sent message`

audit.security-events



</td>
<td valign="top">

Occurs when a user attempts to log on or refresh a session for which the authentication request has expired, for example, if this message is preceded by `AuthnRequest expired - ID`.



</td>
</tr>
<tr>
<td valign="top">

`SAMLAuthenticationError`

`No valid credential to evaluate the token`

audit.security-events



</td>
<td valign="top">

Occurs when the certificate used to sign the SAML response isn't valid.



</td>
</tr>
<tr>
<td valign="top">

Authentication success



</td>
<td valign="top">

`UserAuthenticationSuccess`

audit.security-events



</td>
<td valign="top">

These entries are in addition to the entries made by the UAA. See the previous section *Security Events of the User Account and Authentication Service*. Authentication success includes:

-   User name

-   Principle \(SCIM user ID\)

-   Origin key

-   Zone ID




</td>
</tr>
<tr>
<td valign="top">

SAML responses



</td>
<td valign="top">

<code>"msgNo":<i class="varname">&lt;index&gt;</i>,"msgId":"<i class="varname">&lt;message_id&gt;</i>",</code>

audit.security-events



</td>
<td valign="top">

We include SAML responses in the audit log for web single sign-on and SAML bearer assertions.

> ### Note:  
> When messages exceed 4k, we break the messages into multiple entries. We identify each message with a `msgId` GUID and the parts with a `msgNo` index. To view the whole SAML response, gather the parts and stitch the contents together.



</td>
</tr>
</table>

**Related Information**  


[Audit Logging in the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/02c39712c1064c96b37c1ea5bc9420dc.html)

