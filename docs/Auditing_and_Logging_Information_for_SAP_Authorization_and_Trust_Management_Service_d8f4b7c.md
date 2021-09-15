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

<a name="loiod8f4b7c7298a422183beddb4ad47c108__table_dqf_pkf_p4b"/>Security Events Written in Audit Logs


<table>
<tr>
<th>

Event grouping



</th>
<th>

What events are logged



</th>
<th>

How to identify related log events



</th>
<th>

Additional information



</th>
</tr>
<tr>
<td rowspan="6">

Identity provider management



</td>
<td rowspan="2">

Trust identity provider.



</td>
<td>

 `object with type "IdentityProvider" and id consisting of: crudType "CREATE"` 



</td>
<td>

Attributes of the identity provider.



</td>
</tr>
<tr>
<td>

 `tableName "xs_tenant", crudType "UPDATE"` 



</td>
<td>

Trusting an identity provider using OpenID Connect triggers a change in the XSUAA tenant.



</td>
</tr>
<tr>
<td rowspan="2">

Update trust with identity provider.



</td>
<td>

 `object with type "IdentityProvider" and id consisting of: crudType "UPDATE"` 



</td>
<td>

Old attributes of the identity provider and any attributes required to identify the changes.



</td>
</tr>
<tr>
<td>

 `tableName "xs_tenant", crudType "UPDATE"` 



</td>
<td>

Updating trust in an identity provider using OpenID Connect can trigger a change in the XSUAA tenant.



</td>
</tr>
<tr>
<td rowspan="2">

Delete trust with identity provider.



</td>
<td>

 `object with type "IdentityProvider" and id consisting of: crudType "DELETE"` 



</td>
<td>

Attributes of the service instance.



</td>
</tr>
<tr>
<td>

 `tableName "xs_tenant", crudType "UPDATE"` 



</td>
<td>

Removing trust in an identity provider using OpenID Connect triggers a change in the XSUAA tenant.



</td>
</tr>
<tr>
<td rowspan="3">

Instance management



</td>
<td>

Create instance.



</td>
<td>

`Attribute with name "complete" and value ""ServiceInstanceId: *<Instance\_ID\>*`

…

`object with type "*<Instance\_Name\>*" and id consisting of: crudType "CREATE"`



</td>
<td>

Attributes of the service instance.



</td>
</tr>
<tr>
<td>

Update instance.



</td>
<td>

`Attribute with name "complete" and value ""ServiceInstanceId: *<Instance\_ID\>*`

…

`object with type "*<Instance\_Name\>*" and id consisting of: crudType "UPDATE"`



</td>
<td>

Old attributes of the service instance and any attributes required to identify the changes.



</td>
</tr>
<tr>
<td>

Delete instance.



</td>
<td>

`Attribute with name "complete" and value ""ServiceInstanceId: *<Instance\_ID\>*`

…

`object with type "*<Instance\_Name\>*" and id consisting of: crudType "DELETE"`



</td>
<td>

Attributes of the service instance.



</td>
</tr>
<tr>
<td rowspan="4">

Role collection management



</td>
<td>

Create role collection.



</td>
<td>

`tableName "xsrolecollections", crudType "CREATE"`

audit.configuration



</td>
<td>

Other attributes:

-   Timestamp

-   Origin key

-   Role collection name

-   Zone ID




</td>
</tr>
<tr>
<td>

Assign users to role collection.



</td>
<td>

Direct assignment to users: `tableName "xs_rolecollection2user", crudType "CREATE"`

Mapping to users with attributes: `tableName "xsrolecollection2samlattribute", crudType "CREATE"`

audit.configuration



</td>
<td>

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
<td>

Assign roles to role collection.



</td>
<td>

 `tableName "xsrolecollection2role", crudType "CREATE"` 



</td>
<td>

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
<td>

Delete role collection.



</td>
<td>

`tableName "xsrolecollections", crudType "DELETE"`

audit.configuration



</td>
<td>

Other attributes:

-   Timestamp

-   Origin key

-   Role collection name

-   Zone ID




</td>
</tr>
<tr>
<td rowspan="3">

Role management



</td>
<td>

Create role.



</td>
<td>

`tableName "xsrole", crudType "CREATE"`

audit.configuration



</td>
<td>

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
<td>

Modify attribute values in role.



</td>
<td>

`tableName "xsattribute2role", crudType "CREATE"`

audit.configuration



</td>
<td>

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
<td>

Delete role.



</td>
<td>

`tableName "xsrole", crudType "DELETE"`

audit.configuration



</td>
<td>

Other attributes:

-   Timestamp

-   Origin key

-   Role template app ID

-   Role name

-   Role template name

-   Zone ID




</td>
</tr>
</table>

**Related Information**  


[Audit Logging in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/f92c86ab11f6474ea5579d839051c334.html)

[Audit Logging in the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/02c39712c1064c96b37c1ea5bc9420dc.html)

