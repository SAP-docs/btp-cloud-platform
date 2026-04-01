<!-- loio8c5b4d76a05b4bed8df01937f4d8d487 -->

# Test in the ABAP Environment SAP Fiori Launchpad





### Import Software Components

Before testing new developments in a software component in the test system, as an add-on admin, you have to import the latest changes from the remote repository. After you have cloned a software component into the test system TST, you can import the latest changes by pulling the software component in the *Manage Software Components* app. See [Pull Software Components](../50-administration-and-ops/pull-software-components-90b9b9d.md).



### Create and Assign Business Roles

Before creating and assigning business roles, you have to make sure that business users are already available. They can be created manually or automatically. See [User Provisioning](user-provisioning-ef52a68.md).

To test the developed business services, as a test user, create business roles from the role templates in the test system and assign them to your user. See [Maintain Business Roles](../50-administration-and-ops/maintain-business-roles-8980ad0.md).



### Create Launchpad Space and Pages for Business Roles

To enable navigation to custom UIs via tiles, enable launchpad spaces and pages. Add spaces to the relevant business roles and add the needed SAP Fiori launchpad tiles to those spaces. Finally, enable spaces for business users in the system launchpad settings. See [How to Create Spaces and Pages for a Business Role](../50-administration-and-ops/how-to-create-spaces-and-pages-for-a-business-role-18cdb97.md).



### Create Communication Arrangements

To test inbound and outbound communication, create communication arrangements in the test system TST based on the implemented communication scenarios. See [How to Create a Communication Arrangement](../50-administration-and-ops/how-to-create-a-communication-arrangement-a0771f6.md).

> ### Note:  
> Depending on whether you want to use an authentication method for outbound communication that requires a business user context \(Oauth2 SAML Bearer Assertion, Oauth2 User Token Exchange, JWT Principal Propagation\), you need to configure a destination in a communication arrangement instead of maintaining credentials by using an outbound communication user. See [Supported Protocols and Authentication Methods](https://help.sap.com/docs/abap-cloud/abap-integration-connectivity/supported-protocols-and-authentication-methods) and [Creating a Destination](https://help.sap.com/docs/abap-cloud/abap-integration-connectivity/creating-destination).

You can integrate the test system TST with on-premise systems. See [Integrating On-Premise Systems](integrating-on-premise-systems-c95327f.md).

In the subaccount of test system TST, the subaccount for testing, you can assign the Cloud Connector administrator role collection to the Cloud Connector administrator user to operate the data transmission tunnels used by the Cloud Connector.



### Create Business Configuration

As a test user, you can adjust business configuration objects in the *Maintain Business Configurations* app to change and influence the system behavior. See [Custom Business Configurations App](../50-administration-and-ops/custom-business-configurations-app-76384d8.md).



### Configure Key User Extensibility

Key user extensibility that is enabled in the SaaS solution can be configured and consumed in test systems.

> ### Note:  
> Key user extensibility provided in a SaaS solution can only be configured in tenants of particular types, for testing purposes in tenants of type Test Tenant.
> 
> These tenant types are provisioned in non-development systems, such as test system TST or quality assurance system QAS, where development is not allowed \(`is_development_allowed = false`\). The tenants are created independently from a subscription to the SaaS solution by using the *Landscape Portal* application. See [Manage Test Tenants](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/acc85d68b6da441fa6349af3ae4e4bb4.html).

As a test user in a Test Tenant \(client \>= 200\), you configure key user extensibility in a test system.

-   See [Custom Logic \(Deprecated\)](../50-administration-and-ops/custom-logic-deprecated-05880c7.md) for guidance on how to use the *Custom Logic* app to create and maintain custom logic for business add-ins \(BAdIs\).
-   See [Configuring Predefined Custom Fields](../50-administration-and-ops/configuring-predefined-custom-fields-0033cbc.md) for guidance on how to configure predefined custom fields to customize applications and their UIs.

