<!-- loio363d2ea033b14ecfa5c67cf8d3e7cb01 -->

# Configure and Implement a Customer Project

After you have set up the consumer subaccount, tenant, and tenant user, a remaining customer implementation project in the consumer tenant can start. This includes the setup of identity and authentication management, integration with other systems or services, and adjustment of business configuration.

Once you have configured and implemented the customer project, the SaaS solution matches the requirements of the customer and you can provide the SaaS application URL to the customer.

> ### Tip:  
> We recommend providing documentation for your solution that includes specific configuration steps, for example to describe which business roles users have to create. In the following, we only describe the generic configuration steps.

> ### Note:  
> If you use gCTS for delivery to a customer production system AMT instead of add-ons, the system is initially created without application content. Therefore, you have to clone the required software components manually.
> 
> For the initial import of a software component, as a SaaS solution operator on the provider side, you have to clone the software component in the customer production system AMT. The system can be accessed via the*Landscape Portal* application. In the *Landscape Portal*, the *Systems Overview* app provides an overview about the provisioned systems. Open the system that has been created during subscription to the multitenant application. In the *Tenants Overview*, the production tenant \(client 100\) can then be opened for provider access.
> 
> In the *Manage Software Components* app, select a software component and clone the branch of the software component with the product version, for example v1.0.0.
> 
> See [Delivery via Add-On or gCTS](delivery-via-add-on-or-gcts-438d7eb.md#loio438d7ebfdc4a41de82dcdb156f01857e).



<a name="loio363d2ea033b14ecfa5c67cf8d3e7cb01__section_g5z_xcp_drb"/>

## Prerequisites

To start with the customer project, you have to know the requirements of the customer, and need to have a consumer tenant subscription and a user for the initial consumer access. See [**Subscribe to Multitenant Applications Using the Cockpit**](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/7a3e39622be14413b2a4df7c02ca1170.html) and [Initial User Onboarding](order-and-provide-975bd3e.md#loio4a9c5011922847ac91db165c78656149).

As the consumer subaccount administrator, access the SAP Fiori launchpad of the SaaS Solution subscription from the consumer subaccount account by navigating to *Services* \> *Instances and Subscriptions*.



<a name="loio363d2ea033b14ecfa5c67cf8d3e7cb01__section_t3j_g2p_wqb"/>

## Set Up IAM

**Create and Assign Business Roles**

Before creating and assigning business roles, you have to make sure that business users are already available. They can be created manually or automatically. See [User Provisioning](user-provisioning-ef52a68.md).

As a business user, you configure the authorization to access the applications that are part of the SaaS solution via business roles. With the *Maintain Business Roles* app, you define business roles by combining predefined business catalogs and, if necessary, define value help, read and write access by maintaining the allowed values for fields.

Instead of creating a business role from scratch, you can also use business role templates. See [How to Create a Business Role from a Template](../50-administration-and-ops/how-to-create-a-business-role-from-a-template-ec310a8.md).

**Create Spaces and Pages for Business Roles**

The spaces mode offers more flexibility to adjust the SAP Fiori launchpad layout for specific user groups.

As a business user, to create launchpad spaces and pages, see [How to Create Spaces and Pages for a Business Role](../50-administration-and-ops/how-to-create-spaces-and-pages-for-a-business-role-18cdb97.md).



<a name="loio363d2ea033b14ecfa5c67cf8d3e7cb01__section_pxn_j2p_wqb"/>

## Integrate

**Create Communication Arrangements**

A communication arrangement is a runtime description of a specific communication scenario created by you as a business user. It describes which communication partners communicate with each other in the scenario and how they communicate. See [How to Create a Communication Arrangement](../50-administration-and-ops/how-to-create-a-communication-arrangement-a0771f6.md).

> ### Note:  
> Depending on whether you want to use an authentication method for outbound communication that requires a business user context \(OAuth 2.0 SAML Bearer Assertion, OAuth 2.0 User Token Exchange, JWT Principal Propagation\), you need to configure a destination for communication arrangements in the system instead of maintaining credentials by using an outbound communication user. See [Supported Protocols and Authentication Methods](supported-protocols-and-authentication-methods-437e9d4.md) and [Create a Destination](create-a-destination-3fa7934.md).

See [Integrating On-Premise Systems](integrating-on-premise-systems-c95327f.md) on how to integrate the SaaS solution with on-premise systems.



<a name="loio363d2ea033b14ecfa5c67cf8d3e7cb01__section_urg_l2p_wqb"/>

## Configure

**Create Business Configuration**

As a business user, you can use the *Custom Business Configurations* app to adjust business configuration objects to change and influence the system behavior.

See [Custom Business Configurations App](../50-administration-and-ops/custom-business-configurations-app-76384d8.md) on how to adjust configuration objects provided in the SaaS solution.



**Configure Key User Extensibility**

Key user extensibility that is enabled in the SaaS solution can be configured and consumed in consumer tenants.

> ### Note:  
> Key user extensibility provided in a SaaS solution can only be configured in tenants of particular types, for consumption purposes in customer systems, such as AMT, in tenants of type *Partner Customer Test* or *Partner Customer Production* depending on parameter `usage` in the configuration of the ABAP solution. See [ABAP Solution Service](order-and-provide-975bd3e.md#loio1697387c02e74e66a55cf21a05678167).
> 
> These tenant types are provisioned in non-development systems, such as customer system AMT, where development is not allowed \(`is_development_allowed = false`\). The tenants are created dependent on a subscription to the SaaS solution. See [**Subscribe to Multitenant Applications Using the Cockpit**](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/7a3e39622be14413b2a4df7c02ca1170.html).

As a business user in a *Partner Customer Test* or *Partner Customer Production* tenant \(client \>= 200\), you configure key user extensibility in a customer production system AMT.

-   See [Custom Logic \(Deprecated\)](../50-administration-and-ops/custom-logic-deprecated-05880c7.md) for guidance on how to use the *Custom Logic* app to create and maintain custom logic for business add-ins \(BAdIs\).
-   See [Configuring Predefined Custom Fields](../50-administration-and-ops/configuring-predefined-custom-fields-0033cbc.md) for guidance on how to configure predefined custom fields to customize applications and their UIs.
-   See [Adapting SAP Fiori UIs at Runtime - Key User Adaptation](https://help.sap.com/docs/btp/sap-fiori-launchpad-for-sap-btp-abap-environment/adapting-sap-fiori-uis-at-runtime-key-user-adaptation?version=Cloud)for guidance on how to adapt the user interface of an app separately for specific user roles.


