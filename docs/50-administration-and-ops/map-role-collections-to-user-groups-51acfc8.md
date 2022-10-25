<!-- loio51acfc82c0c54db59de0a528f343902c -->

# Map Role Collections to User Groups

You want to assign a role collection to a user group provided by an identity provider that has a custom trust configuration in SAP BTP. In this case, the assignment is a mapping of a user group to a role collection. Your identity provider provides the user groups using the assertion attribute called `Groups`. Each value of the attribute is mapped to a role collection as described in this procedure.



<a name="loio51acfc82c0c54db59de0a528f343902c__prereq_n3x_1wp_p1b"/>

## Prerequisites

-   You've configured your custom identity provider and established trust with your subaccount.

    > ### Remember:  
    > The name of the trust configuration is different from SAP ID service. The name of a custom trust configuration to SAP Cloud Identity Services - Identity Authentication could be as follows:
    > 
    > <code>https://<i class="varname">&lt;tenant_id&gt;</i>.accounts.ondemand.com</code>

-   You've configured the identity provider so that it conveys the user's group memberships in the *Groups* assertion attribute.

-   You've created role collections.


For more information, see the related links.



## Context

The identity provider provides the business users, who can belong to user groups. It’s efficient to map user groups to role collections. The role collection as a reusable element contains the authorizations that are necessary for this user group. Mappings save time when you want to add a new business user. Simply add the user to the respective user group or groups, and the business user automatically gets all the authorizations that are included in the role collections.



## Procedure

To map a user group to a role collection, see [Assign User Groups to Role Collections](assign-user-groups-to-role-collections-9562d9d.md).

You can also map role collections to attributes other than groups. For more information, see the related links.

**Related Information**  


[Trust and Federation with Identity Providers](trust-and-federation-with-identity-providers-cb1bc8f.md "When setting up accounts you need to assign users. While we provide you with your first users to get you started, your organization has identity providers that you want to integrate.")

[Federation Attribute Settings of Any Identity Provider](federation-attribute-settings-of-any-identity-provider-6d07333.md "This table is supposed to display the attribute settings of the identity provider and the values administrators use to establish trust between the SAML 2.0 identity provider and a new subaccount.")

[Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

[Map Role Collections to User Attributes](map-role-collections-to-user-attributes-b3fbb1a.md "Map role collections to users dynamically through the use of user attributes. When user agents present the attributes of their users, the SAP Authorization and Trust Management service can assign role collections based on the values of those attributes.")

