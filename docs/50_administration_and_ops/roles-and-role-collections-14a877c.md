<!-- loio14a877c6e2f14832999df500ffa6e05e -->

# Roles and Role Collections

Usually a role collection consists of one or multiple roles. You can use the SAP BTP cockpit to add or remove roles.



<a name="loio14a877c6e2f14832999df500ffa6e05e__section_fqg_5b5_rt"/>

## Role

A role is an instance of a role template; you can build a role based on a role template and assign the role to a role collection. The SAP BTP cockpit helps you to display information about the selected application and any related roles in the following windows, tabs, and panes:

-   Roles

-   Scopes

-   Attributes

-   Role templates




<a name="loio14a877c6e2f14832999df500ffa6e05e__section_ezb_xb5_rt"/>

## Role Collection

Roles are assigned to role collections which are assigned in turn to users or user groups if an SAML 2.0 identity provider stores the users. Using the SAP BTP cockpit, you can display information about the role collections that have been maintained as well as the roles available in a role collection. Additional information includes: which templates the roles are based on, and which applications the roles apply to. Role collections enable you to group together the roles you create. The role collections you define can be assigned as follows:

-   To users logged on to the `SAP ID service`.

-   To user groups containing users logging on with SAML 2.0 assertions.


**Related Information**  


[Attributes](attributes-713f52a.md "Attributes use information that is specific to the user, for example the user's country. If the application developer in the Cloud Foundry environment of SAP BTP has created a country attribute to a role, this restricts the data a business user can see based on this attribute.")

[Security Administration: Managing Authentication and Authorization](security-administration-managing-authentication-and-authorization-1ff47b2.md "This section describes the tasks of administrators in the Cloud Foundry environment of SAP BTP. Administrators ensure user authentication and assign authorization information to users and user groups.")

