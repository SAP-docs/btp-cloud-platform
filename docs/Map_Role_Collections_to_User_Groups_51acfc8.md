<!-- loio51acfc82c0c54db59de0a528f343902c -->

# Map Role Collections to User Groups

You want to assign a role collection to a user group provided by an identity provider that has a custom trust configuration in SAP BTP. In this case, the assignment is a mapping of a user group to a role collection. Your identity provider provides the user groups using the assertion attribute called `Groups`. Each value of the attribute is mapped to a role collection as described in this procedure.



<a name="loio51acfc82c0c54db59de0a528f343902c__prereq_n3x_1wp_p1b"/>

## Prerequisites

-   You've configured your custom identity provider and established trust with your subaccount.

    > ### Remember:  
    > The name of the trust configuration is different from SAP ID service. The name of a custom trust configuration to SAP Cloud Identity Services - Identity Authentication could be as follows:
    > 
    > `https://*<tenant\_id\>*.accounts.ondemand.com`

-   You've configured the identity provider so that it conveys the user's group memberships in the *Groups* assertion attribute.

-   You've created role collections.


For more information, see the related links.



## Context

The identity provider provides the business users, who can belong to user groups. It’s efficient to map user groups to role collections. The role collection as a reusable element contains the authorizations that are necessary for this user group. Mappings save time when you want to add a new business user. Simply add the user to the respective user group or groups, and the business user automatically gets all the authorizations that are included in the role collections.

You can also map role collections to attributes other than groups. For more information, see the related links.



## Procedure

1.  Go to your subaccount \(see [Navigate to Orgs and Spaces](Navigate_to_Orgs_and_Spaces_5bf8735.md)\) and choose *Security* \> *Role Collections*.

2.  Search for and choose a role collection.

3.  In the overview page for the role collection, choose the *Edit* button.

4.  Under *User Groups*, select an identity provider.

5.  Enter the name of the user group.

    > ### Tip:  
    > Use the **exact** name of the user group as provided by the identity provider.
    > 
    > > ### Example:  
    > > In the SAP Cloud Identity Services - Identity Authentication, find the user groups in the administration console of your SAP Cloud Identity Services - Identity Authentication tenant under *Users & Authorizations* \> *User Groups*. Open the administration console, using `https://*<tenant\_id\>*.accounts.ondemand.com/admin`.

6.  Save your entries.


**Related Information**  


[Trust and Federation with Identity Providers](Trust_and_Federation_with_Identity_Providers_cb1bc8f.md "When setting up accounts you need to assign users. While we provide you with your first users to get you started, your organization has its own user bases which you want to integrate.")

[Map Role Collections to User Groups](Map_Role_Collections_to_User_Groups_51acfc8.md "You want to assign a role collection to a user group provided by an identity provider that has a custom trust configuration in SAP BTP. In this case, the assignment is a mapping of a user group to a role collection. Your identity provider provides the user groups using the assertion attribute called Groups. Each value of the attribute is mapped to a role collection as described in this procedure.")

[Federation Attribute Settings of Any Identity Provider](Federation_Attribute_Settings_of_Any_Identity_Provider_6d07333.md "This table is supposed to display the attribute settings of the identity provider and the values administrators use to establish trust between the SAML 2.0 identity provider and a new subaccount.")

[Cloud Management Tools — Feature Set Overview](Cloud_Management_Tools_—_Feature_Set_Overview_caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

[Map Role Collections to User Attributes](Map_Role_Collections_to_User_Attributes_b3fbb1a.md "Map role collections to users dynamically through the use of user attributes. When user agents present the attributes of their users, the SAP Authorization and Trust Management service can assign role collections based on the values of those attributes.")

