<!-- loio8980b91c14f9474a9d7c7d831bbad8e9 -->

# Bringing Your Corporate Identity Provider for Platform Users

SAP BTP supports the use of your own identity provider for platform users.

Platform users perform technical development, operations, and administration tasks. They manage global accounts, directories, and subaccounts using the SAP BTP cockpit and the SAP BTP CLI. They also develop and operate custom applications. By hosting these users in your own identity provider, you gain a number of advantages over hosting them in SAP ID service or in SAP Universal ID.

-   Integrate the management of these users with your broader identity management strategy, hosted on your own identity providers. You control your own user lifecycle and single sign-on strategies throughout the entire landscape.

-   Enforce your own password and authentication policies, such as stronger passwords or multifactor authentication.


The following figure illustrates the architecture required for platform users. This configuration is independent of the default configuration with SAP ID service. You can continue to use SAP ID service in parallel.

  
  
**Authentication Architecture for Platform Users with a Corporate Identity Provider**



![](images/SAP_BTP_Account_Mapping_e29be15.png)

In the preceding figure, you enable trust between the SAP BTP global account and your corporate identity provider over your tenant of SAP Cloud Identity Services - Identity Authentication. Trust is configured differently in the Kyma environment \(see the related link\). For each global account, you choose the SAP Cloud Identity Services tenant to use as the identity provider for platform users. For the platform identify provider, you can have up to three SAP Cloud Identity Services tenants per global account. Multiple global accounts can share the same SAP Cloud Identity Services tenant. When you log on to a platform resource, such as the cockpit, you indicate the SAP Cloud Identity Services tenant that you want to log on with. For example, to log on to the cockpit, copy a URL parameter from the cockpit to identify the tenant:

<code>https://cockpit.btp.cloud.sap/cockpit/?idp=<i class="varname">&lt;tenant&gt;</i>.accounts.ondemand.com</code>

For example: `https://cockpit.btp.cloud.sap/cockpit/?idp=cidppuxhm.accounts.ondemand.com`

Once you’ve logged on, the cockpit displays any global accounts and subaccounts of which your platform user is a member.

A user identifier alone isn’t enough to identify a user. Additionally, you also need an identifier for an identity provider. The reason is that the system treats users with the same name but from different identity providers as separate users.

For global accounts, directories, multi-environment subaccounts, and the Cloud Foundry environment, the user identifier is always an email address, and the identifier of the identity provider is the origin key \(alias for the trust configuration\). For example, a platform user in the default identity provider, SAP ID service, and another user in your corporate identity provider with the same email address might have different authorizations.

> ### Example:  
> There are two users with the same email address. It is common practise that the two users with different identity providers have different authorizations and can access different applications.
> 
> -   julia.moore@acme.com with the default identity provider isn't authorized for any subaccount.
> 
> -   julia.moore@acme.com with the `acme-platform` custom identity provider is the administrator for multiple subaccounts. The subaccounts are only visible when she logs on with the custom identity provider.

You can log on to the cockpit with both, but the cockpit displays different user information. This difference is because you’ve logged on with different identity providers.

For Neo subaccounts, it is, by default, the P user ID for local SAP Cloud Identity Services users or whatever the corporate identity provider connected to the SAP Cloud Identity Services tenant sends as subject. The identifier of the identity provider is the default domain of the SAP Cloud Identity Services tenant, for example `acme.accounts.ondemand.com`. It is called "user base". For more information, see [Platform Identity Provider](https://help.sap.com/docs/btp/sap-btp-neo-environment/platform-identity-provider?q=%22user%20base%22).

You also see this difference when assigning roles. You must provide the origin or user base in addition to the email address or user ID of the user. When platform users use the Cloud Foundry command-line interface or service dashboards, they need to remember the origin. You can choose your own origin, but the origin must be unique across all customers. We recommend that you use a meaningful name that helps identify the target it points to.

In SAP Cloud Identity Services - Identity Authentication in Neo subaccounts, there's one application that represents SAP BTP overall. So, if you have multiple global accounts with the same SAP Cloud Identity Services tenant, they all share the same application in your SAP Cloud Identity Services tenant. Here customers typically configure settings such as the corporate identity provider used for authentication and user attribute mapping between systems. For more information, see [Map User Attributes from a Corporate Identity Provider for Platform Users](../50-administration-and-ops/map-user-attributes-from-a-corporate-identity-provider-for-platform-users-40c2e54.md).

**Related Information**  


[Log On with a Custom Identity Provider to the Cloud Foundry Environment Using the Cloud Foundry Command-Line Interface](../50-administration-and-ops/log-on-with-a-custom-identity-provider-to-the-cloud-foundry-environment-using-the-cloud-d477618.md "Learn how to use different methods to log on to Cloud Foundry using a custom identity provider (IdP).")

[Establish Trust and Federation of Custom Identity Providers for Platform Users](../50-administration-and-ops/establish-trust-and-federation-of-custom-identity-providers-for-platform-users-c368984.md "You want to use a custom identity provider for the platform users of SAP BTP in different environments and at the different account levels: global account, directory, and subaccount. By default, platform users in multi-environment subaccounts are users in the default identity provider.")

[Configuring a Custom Identity Provider for Kyma](../60-security/configuring-a-custom-identity-provider-for-kyma-67bcc6e.md "Enable the Kyma environment with a custom identity provider (IdP).")

