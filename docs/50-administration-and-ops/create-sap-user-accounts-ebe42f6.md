<!-- loioebe42f6900384c75bb7def32c011fa40 -->

# Create SAP User Accounts

To grant authorizations to people from the default identity provider in your subaccount, ensure that they have a user account.



## Context

If the person in question already has a user account on `sap.com` Web sites, then that person already has a user in the default identity provider. Add this user to your accounts, if you know this person's e-mail address.

Consider using a custom identity provider to integrate your own identity and access management solution.

> ### Note:  
> For technical users, create the user in your custom identity provider. The default identity provider is meant for human users, who interact with SAP and our solutions. Use custom identity providers for technical users, so you control the access policies of these users independently from the policies we set for the default identity provider.



## Procedure

Send your colleagues the self-registration URL.

`https://account.sap.com/core/create/register?redirectURL=https%3A%2F%2Femea.cockpit.btp.cloud.sap%2Fcockpit%2F`

The Web site registers you with SAP Universal ID, which also registers you with SAP ID service. If you already have a user in SAP ID service, you've the option to associate this user with your new SAP Universal ID account. SAP Universal ID manages the users of official SAP sites, including the SAP developer and partner community.

> ### Tip:  
> If you already know the e-mail addresses of your colleagues, you can add them to your subaccount and assign role collections. After registering, your colleagues have the option to return to the SAP BTP cockpit. If you've already assigned authorizations to that user, then your colleagues have access when they log on.



<a name="loioebe42f6900384c75bb7def32c011fa40__result_yzf_ccq_p5b"/>

## Results

**Related Information**  


[Add Users from SAP ID Service for Multi-Environment Subaccounts](add-users-from-sap-id-service-for-multi-environment-subaccounts-760ab77.md "Before you can assign role collection to a user from SAP ID service, ensure that this user exists in your subaccount.")

[Default Identity Provider](default-identity-provider-d6a8db7.md "SAP ID service is the default identity provider for both platform users and business users (in applications) at SAP BTP. You can start using it without further configuration.")

[Trust and Federation with Identity Providers](trust-and-federation-with-identity-providers-cb1bc8f.md "When setting up accounts you need to assign users. While we provide you with your first users to get you started, your organization has identity providers that you want to integrate.")

