<!-- loio8b23d425aa424c92a12dbd45311d0560 -->

# Providing Access to a Business Service for Business Users

For business users, you must provide access to a newly created service because access isn’t automatically available.



<a name="loio8b23d425aa424c92a12dbd45311d0560__section_s2r_k45_mpb"/>

## Motivation

If you have the developer role `SAP_BR_DEVELOPER`, for example, you can test your new service immediately without having to create an IAM app and assign it to a business catalog and a business role. Activating the service binding, for example, creates the IAM app and assigns it to the business catalog `SAP_CORE_BC_EXT_TST` that is shipped to customers for testing purposes. This business catalog is assigned to the developer role template `SAP_BR_DEVELOPER`. Therefore, when you create a new service in a development system and activate the service binding, all users with this developer role can automatically access and use the service. Of course, all users with another role containing this catalog will also be able to access and use the service.

This kind of access isn’t available anymore when you pull the business service into nondevelopment systems, for example, where this test catalog feature isn’t enabled. You must develop identity and access management artifacts, which is explained in detail in this guide. They ensure that you can define the necessary authorizations and enable business users to consume the business service.



<a name="loio8b23d425aa424c92a12dbd45311d0560__section_fbd_1m4_nlb"/>

## Overview of Development Options

Now let’s assume you would like to achieve that certain business users are able to view and edit bonus calculations:

-   Under *Providing Unrestricted Access*, you learn how to provide users read and write access to all bonus calculations.

    This scenario is simple to implement. It's enough if you have one user group that is allowed to make full use of the business service while all other users don't need access, not even read access. In this case, if managers have access to the business service, they can create, update, display, and delete all available bonus calculations.

-   Under *Providing Access Based on Activities*, you learn how to create two business roles for separate read and write authorizations.

    With this scenario, you can keep business users with read access only from changing bonus calculations.

-   Under *Providing Access Based on Field Values*, you learn how to fine-tune your access restrictions to particular fields, that is, on the level of data elements, such as the bonus variant.

    This is the most complex scenario, but it allows administrators to define business roles that authorize users to view and change only particular data; other data is filtered. In the case of the bonus calculation service, managers can only create, view, update, and delete bonus calculations that have a specific bonus variant. The advantage of this scenario is that you, as a developer, can shift some decisions about the business role design to the administrator, who can decide which data is visible to business users, based on restriction fields in the business role.


After you have implemented access based on one of the scenarios mentioned, you can then also go on and implement access to the corresponding SAP Fiori application for the business service.



<a name="loio8b23d425aa424c92a12dbd45311d0560__section_qq3_djz_cqb"/>

## Tutorial

In addition to this documentation, the following tutorial is also available:

[Create Authorization Model with SAP BTP, ABAP Environment](https://developers.sap.com/group.abap-env-authorizations.html)

-   **[Considerations for Implementing Access and Authorizations](Considerations_for_Implementing_Access_and_Authorizations_c324022.md "You can implement data access and authorizations for a service differently, depending on how you want to implement differences on the UI
		for different target groups. It also matters how you want  to design business roles. Therefore, before you start with the actual
		implementation of data access and authorizations, you need to consider how you want to proceed.")**  
You can implement data access and authorizations for a service differently, depending on how you want to implement differences on the UI for different target groups. It also matters how you want to design business roles. Therefore, before you start with the actual implementation of data access and authorizations, you need to consider how you want to proceed.
-   **[Providing \(Unrestricted\) Access for Business Users](Providing_(Unrestricted)_Access_for_Business_Users_41f3639.md "In this scenario, you get information about how to provide unrestricted access with a few steps.")**  
In this scenario, you get information about how to provide unrestricted access with a few steps.
-   **[Providing Access Based on Activities for Business Users](Providing_Access_Based_on_Activities_for_Business_Users_f070f5d.md "In this scenario, you provide access depending on what the user should be allowed to do, for example, read or write access. ")**  
In this scenario, you provide access depending on what the user should be allowed to do, for example, read or write access.
-   **[Providing Access Based on Field Values for Business Users](Providing_Access_Based_on_Field_Values_for_Business_Users_d60c7fb.md "You can enable access to a service in such a way that it's dependent on the field values of a business object. As a result, business users
		can view or change only business object instances where the field values match their authorizations.")**  
You can enable access to a service in such a way that it's dependent on the field values of a business object. As a result, business users can view or change only business object instances where the field values match their authorizations.

