<!-- loio9e1bf57130ef466e8017eab298b40e5e -->

# Mapping Role Collections in the Subaccount

You've arranged roles in role collections, and now want to assign or map these role collections to business users.

How you assign users to their authorizations depends on the type of trust configuration and on whether or not you prefer to maintain the authorizations of individual users rather in the identity provider or in SAP BTP. The following options are available:

-   Directly assign role collections to users.

-   Map role collections to user groups or other user attributes defined in the identity provider. You initially maintain the mapping between user groups or other user attributes and role collections once in SAP BTP, and maintain group memberships or other attributes of users in the identity provider.


> ### Note:  
> If you’re using the default trust configuration with the default identity provider, you directly assign users to role collections. For more information, see [Default Identity Provider](default-identity-provider-d6a8db7.md).
> 
> However, if you’re using a custom trust configuration, for example, with SAP Cloud Identity Services, you can use both options. For more information about configuring the trust between your subaccount and a custom identity provider, see [Establish Trust and Federation Between SAP Authorization and Trust Management Service and SAP Cloud Identity Services](establish-trust-and-federation-between-sap-authorization-and-trust-management-service-a-161f8f0.md).

**Options for Assignment of Role Collections**


<table>
<tr>
<th valign="top">

Trust Configuration

</th>
<th valign="top">

Assignment Options

</th>
</tr>
<tr>
<td valign="top">

Default trust configuration \(SAP ID service\)

</td>
<td valign="top">

[Assign Users to Role Collections](assign-users-to-role-collections-c576676.md) 

</td>
</tr>
<tr>
<td valign="top">

Custom trust configuration \(for example: a tenant of SAP Cloud Identity Services\)

</td>
<td valign="top">

-   [Assigning Role Collections to Users or User Groups](assigning-role-collections-to-users-or-user-groups-31532c7.md)

-   [Map Role Collections to User Groups](map-role-collections-to-user-groups-51acfc8.md)

-   [Map Role Collections to User Attributes](map-role-collections-to-user-attributes-b3fbb1a.md)




</td>
</tr>
</table>

**Related Information**  


[Working with Role Collections](working-with-role-collections-393ea0b.md "As an administrator, you group application roles in role collections. You then assign role collections to application users.")

[Trust and Federation with Identity Providers](trust-and-federation-with-identity-providers-cb1bc8f.md "When setting up accounts you need to assign users. While we provide you with your first users from the default identity provider to get you started, your organization has identity providers that you want to integrate.")

