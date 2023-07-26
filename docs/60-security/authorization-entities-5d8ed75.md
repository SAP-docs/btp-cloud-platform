<!-- loio5d8ed75b5c72432cb0e4d846f411e0cd -->

# Authorization Entities

Business users in an application require different authorizations because they work in different jobs.

For example, in a leave request process, there are employees who want to create and submit leave requests, managers who approve or reject, and payroll administrators who need to see all approved leave requests to calculate the leave reserve. The authorization concept of a leave request application has to cover the needs of these employee groups. This authorization concept includes elements such as roles, scopes, and attributes.

A role is an instance of a role template; you can build a role based on a role template and assign the role to a role collection.

Role templates refer to attributes and scopes. The role templates contain the authorizations for activities, such as viewing, editing, or deleting data.

Information that is specific to the user is stored in attributes. For each attribute, administrators can specify the value that restricts data access. Static attributes are stored in the role, whereas in cases in which a custom identity provider provides the business users, you can dynamically reference all the attributes that come with the access token.

  
  
**Relationship Between Authorization Components**

![Understand how the different authorization components relate to each other.](images/Relationship_between_authorization_entities_fef7332.png "Relationship Between Authorization Components")



<a name="loio5d8ed75b5c72432cb0e4d846f411e0cd__section_aht_3mh_l4b"/>

## Scopes for Functional Authorization Checks

The application defines scopes, which describe the authorizations required by the application to execute functions such as editing, viewing, and deleting.

The application security descriptor file \(`xs-security.json`\) defines the scopes used by the application.



<a name="loio5d8ed75b5c72432cb0e4d846f411e0cd__section_l5w_mmh_l4b"/>

## Role Templates

A role template is a description of one or more roles \(for example, employee or manager\) and any attributes that apply to those roles.

If a role template contains attributes, the administrator must create different versions of the roles and fill in the attributes that are subject to customization; for example, one where country equals UK and another where country equals USA. This instantiates the role template. Else, the roles will have empty attributes \(with no concrete values\).

Role templates that contain only application-specific local scopes can be instantiated without the administrator having to do anything.



<a name="loio5d8ed75b5c72432cb0e4d846f411e0cd__section_bbh_4mh_l4b"/>

## Role Collections

Role collections reference role templates.

After the developer has created the role templates and deployed them to the relevant application, it's the administrator’s task to use those role templates to build roles with the required attributes, aggregate the roles into role collections, and then assign the role collections to business users in the application.



<a name="loio5d8ed75b5c72432cb0e4d846f411e0cd__section_jfq_lmh_l4b"/>

## Attributes

Information retrieved from the user's identity \(such as department or cost center\) is stored in attributes. Attributes refine the authorizations of business users according to the attributes that come with the business users. For example, you can use static attribute values such as country equals USA, or dynamic attribute values from the access token or identity provider, such as group ID.

