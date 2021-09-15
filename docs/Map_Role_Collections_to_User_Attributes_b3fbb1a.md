<!-- loiob3fbb1a9232d4cf99967a0b29dd85d4c -->

# Map Role Collections to User Attributes

Map role collections to users dynamically through the use of user attributes. When user agents present the attributes of their users, the SAP Authorization and Trust Management service can assign role collections based on the values of those attributes.



<a name="loiob3fbb1a9232d4cf99967a0b29dd85d4c__prereq_n3x_1wp_p1b"/>

## Prerequisites

-   You've configured your custom identity provider and established trust with your subaccount.

-   You've configured the identity provider so that it conveys the user attributes in the assertion attributes.

-   You've created role collections.


For more information, see the related links.



## Context

The identity provider hosts the users and their attributes. When a user is authenticated by the SAP Authorization and Trust Management service, a user agent presents a number of attributes of the user, such as an e-mail address. The SAP Authorization and Trust Management service uses this attribute to identify the user. You can use such attributes to assign role collections. For example, you can use the `company_region` attribute to assign role collections specific to the provinces or states your users are located. More use cases are to have different role collections for different cost centers or job functions. Mapping role collections to the attribute `Groups` is so common that we have a separate use case for it. For more information, see *Map Role Collections to User Groups* in the related links.

> ### Tip:  
> Mappings save time when you add new users. Simply set the relevant attributes in the identity provider for the users, and the users automatically gets all the authorizations that are included in the role collections.



## Procedure

1.  Go to your subaccount \(see [Navigate to Orgs and Spaces](Navigate_to_Orgs_and_Spaces_5bf8735.md)\) and choose *Security* \> *Role Collections*.

2.  Search for and choose a role collection.

3.  In the overview page for the role collection, choose the *Edit* button.

4.  Under *Attribute Mapping*, select an identity provider.

5.  Enter the name of the attribute and the value for the SAP Authorization and Trust Management service to use to map the role collection to users.

    > ### Tip:  
    > Provide the **exact** name of the attribute and its value as provided by the identity provider. These values are case-sensitive.
    > 
    > For more information, see [Federation Attribute Settings of Any Identity Provider](Federation_Attribute_Settings_of_Any_Identity_Provider_6d07333.md) or [Configure the User Attributes Sent to the Application](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/d361407d36c5443298a909acbbd96ec4.html) in the documentation of the Identity Authentication service.

6.  Save your entries.


**Related Information**  


[Trust and Federation with Identity Providers](Trust_and_Federation_with_Identity_Providers_cb1bc8f.md "When setting up accounts you need to assign users. While we provide you with your first users to get you started, your organization has its own user bases which you want to integrate.")

[Establish Trust and Federation Between UAA and Identity Authentication](Establish_Trust_and_Federation_Between_UAA_and_Identity_Authentication_161f8f0.md#loio161f8f0cfac64c4fa2d973bc5f08a894 "Use your SAP Cloud Identity Services - Identity Authentication tenant as an identity provider or a proxy to your own identity provider hosting your business users. This method avoids the upload and download of SAML meta data by using Open ID Connect (OIDC) to establish trust.")

[Federation Attribute Settings of Any Identity Provider](Federation_Attribute_Settings_of_Any_Identity_Provider_6d07333.md "This table is supposed to display the attribute settings of the identity provider and the values administrators use to establish trust between the SAML 2.0 identity provider and a new subaccount.")

[Map Role Collections to User Groups](Map_Role_Collections_to_User_Groups_51acfc8.md "You want to assign a role collection to a user group provided by an identity provider that has a custom trust configuration in SAP BTP. In this case, the assignment is a mapping of a user group to a role collection. Your identity provider provides the user groups using the assertion attribute called Groups. Each value of the attribute is mapped to a role collection as described in this procedure.")

[Create Role Collections with Predefined Roles](Create_Role_Collections_with_Predefined_Roles_fe75054.md "As an application developer, you want to create role collections for immediate use. You want to deliver role collections that administrators can use in the cockpit, and easily assign to users, for example in an onboarding process.")

