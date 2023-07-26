<!-- loio5b6290112008456b9e9400faebb8cd33 -->

# Identity and Access Management \(IAM\)

Learn more about the basic concepts and procedures for managing users and defining authorizations for business services and SAP Fiori applications.



<a name="loio5b6290112008456b9e9400faebb8cd33__section_fvs_1qz_jrb"/>

## What Is Identity and Access Management?

The main components of Identity and Access Management are:

-   User and Identity Management
-   Roles and Authorization
-   Authentication

![](images/IAM_Overview_215b0ed.png)

In the configuration phase, an administrator registers and authorizes access rights.

In the operation phase, business users identify and authenticate themselves. The access to applications is based on previously authorized access rights.

In a business scenario, this means that an administrator manages the authentication and authorization of business users, including configuring [trust and identity federation](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/cb1bc8f1bd5c482e891063960d7acd78.html) in the subaccount usually by configuring a [custom identity authentication service tenant](../20-getting-started/setup-of-a-custom-identity-service-550251a.md)​. As a fallback, [SAP ID service](https://help.sap.com/viewer/ae8e8427ecdf407790d96dad93b5f723/Cloud/en-US/d6a8db70bdde459f92f2837349f95090.html) is configured as the default identity provider. Additionally, an administrator also creates roles using templates, adds roles to role collections, and assigns role collections to business users. The business users can then log on to SAP Fiori applications and get authenticated.



<a name="loio5b6290112008456b9e9400faebb8cd33__section_xxr_1hr_cmb"/>

## Who Is This Guide For?

If you’re an SAP customer **developer** or partner developer and you create business services in the ABAP environment using ABAP Development Tools for Eclipse, this guide is for you. It guides you through an example of a business service based on a service binding. Note that http services work in a similar way.

In addition, the guide also covers activities that need to be performed by an **administrator**, such as assigning users to business roles.



<a name="loio5b6290112008456b9e9400faebb8cd33__section_fbd_1m4_nlb"/>

## What Is This Guide About?

The guide starts with an overview of the basic concepts of identity and access management. It then leads you step by step through the design and implementation of your authorization model using an example.

Why should you care about access control and authorizations? You must know that every new service is automatically available to all developers in a development system, provided the system administrator has assigned them a role that is derived from the developer role `SAP_BR_DEVELOPER` \(which is typically the case\). However, business users in nondevelopment systems can only access the business service if a developer has defined the appropriate authorizations and an administrator grants the business users access for each relevant system. The same is true for communication users that are needed in scenarios where you work with an API business service \(inbound or outbound\) from or into the ABAP environment.

The **Identity Management** section gives you an overview about Identity and User Management, which includes identity federation, user types, and user provisioning.

The **Access Management** section includes the following main scenarios about how you can implement and provide authorizations for your services:

-   In chapter [Providing \(Unrestricted\) Access for Business Users](providing-unrestricted-access-for-business-users-41f3639.md), you learn how to provide users in a nondevelopment system access to the service.

    Providing unrestricted access is the simplest scenario with only a few steps. The access is unrestricted, though, which means, for example, that you can't differentiate between write and read access.

-   In chapter [Providing Access Based on Activities for Business Users](providing-access-based-on-activities-for-business-users-f070f5d.md), you learn how to implement access for different activities, for example, separate read and write authorizations.

-   In chapter [Providing Access Based on Field Values for Business Users](providing-access-based-on-field-values-for-business-users-d60c7fb.md), you learn how to fine-tune your access restrictions depending on field values.


OData services that you develop using ADT can also be consumed in SAP Fiori applications \(developed using the Business Application Studio\). In this guide, you also learn how to provide access to an SAP Fiori application that consumes a business service.

