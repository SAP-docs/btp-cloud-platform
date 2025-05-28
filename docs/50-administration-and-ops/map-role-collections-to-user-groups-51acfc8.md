<!-- loio51acfc82c0c54db59de0a528f343902c -->

# Map Role Collections to User Groups

You want to assign a role collection to a user group provided by an identity provider that has a custom trust configuration in SAP BTP. In this case, the assignment is a mapping of a user group to a role collection. Your identity provider provides the user groups using the attribute called `Groups`. Each value of the attribute is mapped to a role collection as described in this procedure.



<a name="loio51acfc82c0c54db59de0a528f343902c__prereq_n3x_1wp_p1b"/>

## Prerequisites

-   You've configured your custom identity provider and established trust with your subaccount.

    > ### Remember:  
    > The name of the trust configuration is different from SAP ID service. The name of a custom trust configuration to SAP Cloud Identity Services could be as follows:
    > 
    > <code>https://<i class="varname">&lt;tenant_id&gt;</i>.accounts.ondemand.com</code>

-   You've configured the identity provider so that it conveys the user's group memberships in the *groups* attribute.

    -   For business users, see [Map User Attributes from a Corporate Identity Provider for Business Users](map-user-attributes-from-a-corporate-identity-provider-for-business-users-bbb4a8a.md).

    -   For platform users, see [Map User Attributes from a Corporate Identity Provider for Platform Users](map-user-attributes-from-a-corporate-identity-provider-for-platform-users-40c2e54.md).


-   You've created role collections.




## Context

The identity provider provides the users, who can belong to user groups. It’s efficient to map user groups to role collections. The role collection as a reusable element contains the authorizations that are necessary for this user group. Mappings save time when you want to add a new user. Simply add the user to the respective user group or groups, and the user automatically gets all the authorizations that are included in the role collections.



## Procedure

To map a user group to a role collection, see [Assign User Groups to Role Collections](assign-user-groups-to-role-collections-9562d9d.md).

You can also map role collections to attributes other than groups. For more information, see the related links.

**Related Information**  


[Trust and Federation with Identity Providers](trust-and-federation-with-identity-providers-cb1bc8f.md "When setting up accounts you need to assign users. While we provide you with your first users from the default identity provider to get you started, your organization has identity providers that you want to integrate.")

[Cloud Management Tools](../10-concepts/cloud-management-tools-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

[Map Role Collections to User Attributes](map-role-collections-to-user-attributes-b3fbb1a.md "Map role collections to users dynamically through the use of user attributes. When user agents present the attributes of their users, the SAP Authorization and Trust Management service can assign role collections based on the values of those attributes.")

