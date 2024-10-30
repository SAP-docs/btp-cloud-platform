<!-- loiobb1b2f4814b04f41833ff0a5bdd5d599 -->

# Provision Users to SAP BTP Accounts

As people join, change roles, and eventually leave your organization, you care for the onboarding, maintenance, and offboarding of their users in your systems. If you're a small organization, you can use manual processes; otherwise, you should consider automating your processes.



<a name="loiobb1b2f4814b04f41833ff0a5bdd5d599__prereq_kyb_mkt_bnb"/>

## Prerequisites

-   You have the required authorizations.

    For more information, see [Security Administration: Managing Authentication and Authorization](security-administration-managing-authentication-and-authorization-1ff47b2.md) or [Role Collections and Roles in Global Accounts, Directories, and Subaccounts](../10-concepts/role-collections-and-roles-in-global-accounts-directories-and-subaccounts-0039cf0.md).

-   For global account, directory, and subaccount levels, you have API credentials.

    For more information, see [Accessing Administration Using APIs of the SAP Authorization and Trust Management Service](accessing-administration-using-apis-of-the-sap-authorization-and-trust-management-servi-dcb3bfd.md).




## Context

We recommend creating users within the SAP Cloud Identity Services. The persistency layer of SAP Cloud Identity Services is the Identity Directory. Use SAP Cloud Identity Services - Identity Provisioning to provision users to SAP cloud solutions, such as SAP BTP. Identity Provisioning has connectors to distribute user artifacts needed at different levels of your SAP BTP accounts. By managing your identities centrally, you also ensure that when you offboard users, they're removed from target systems.



## Procedure

Integrate with your identity and access management solution.

-   To integrate with SAP Cloud Identity Services, see [SAP BTP Integration Scenario](https://help.sap.com/docs/cloud-identity/system-integration-guide/sap-btp-integration-scenario?version=Cloud) for more information.

-   To integrate with another solution, use the User Management SCIM API. See [User Management \(System for Cross-domain Identity Management \(SCIM\)\)](https://api.sap.com/api/PlatformAPI/overview) for more information.

    > ### Note:  
    > For user management of Cloud Foundry organizations, use the provisioning connectors of SAP Cloud Identity Services - Identity Provisioning. For more information, see [SAP BTP Integration Scenario](https://help.sap.com/docs/cloud-identity/system-integration-guide/sap-btp-integration-scenario?version=Cloud).


