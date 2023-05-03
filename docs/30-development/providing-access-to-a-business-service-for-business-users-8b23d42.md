<!-- loio8b23d425aa424c92a12dbd45311d0560 -->

# Providing Access to a Business Service for Business Users

For a newly created business service, you must define how business users can access it and which activities are allowed.



<a name="loio8b23d425aa424c92a12dbd45311d0560__section_s2r_k45_mpb"/>

## Motivation

If you have the developer role `SAP_BR_DEVELOPER`, for example, you can test your new service immediately without having to create an IAM app and assign it to a business catalog and a business role. Activating the service binding, for example, creates the IAM app and assigns it to the business catalog `SAP_CORE_BC_EXT_TST` that is shipped to customers for testing purposes. This business catalog is assigned to the developer role template `SAP_BR_DEVELOPER`. Therefore, when you create a new service in a development system and activate the service binding, all users with this developer role can automatically access and use the service. Of course, all users with another role containing this catalog are then also able to access and use the service.

This kind of access isn’t available anymore when you pull the business service into nondevelopment systems, for example, where this test catalog feature isn’t enabled.

For business users, you must provide access to a newly created service because access isn’t automatically available. However, all activities are allowed as long as you don't protect your business service. Therefore, you must develop identity and access management artifacts, which is explained in detail in this guide. They ensure that you can define the necessary authorizations and enable business users to consume the business service.



<a name="loio8b23d425aa424c92a12dbd45311d0560__section_fbd_1m4_nlb"/>

## Overview of Development Options

Now, let’s assume you would like to achieve that certain business users are able to view and edit bonus calculations:

-   Under *Providing Unrestricted Access*, you learn how to provide users read and write access to all bonus calculations.

    This scenario is simple to implement. It's enough if you have one user group that is allowed to make full use of the business service while all other users don't need access, not even read access. In this case, if managers have access to the business service, they can create, update, display, and delete all available bonus calculations.

-   Under *Providing Access Based on Activities*, you learn how to create two business roles for separate read and write authorizations.

    With this scenario, you can keep business users with read access only from changing bonus calculations.

-   Under *Providing Access Based on Field Values*, you learn how to fine-tune your access restrictions to particular fields, that is, on the level of data elements, such as the bonus variant.

    This is the most complex scenario, but it allows administrators to define business roles that authorize users to view and change only particular data; other data is filtered. For the bonus calculation service, managers can only create, view, update, and delete bonus calculations that have a specific bonus variant. The advantage of this scenario is that you, as a developer, can delegate some decisions about the business role design to the administrator. The administrator can decide which data is visible to business users, based on restriction fields in the business role.


After you've implemented access based on one of the scenarios mentioned, you can then also go on and implement access to the corresponding SAP Fiori application for the business service.



<a name="loio8b23d425aa424c92a12dbd45311d0560__section_qq3_djz_cqb"/>

## Tutorial

In addition to this documentation, the following tutorial is also available:

[Create Authorization Model with SAP BTP, ABAP Environment](https://developers.sap.com/group.abap-env-authorizations.html)

