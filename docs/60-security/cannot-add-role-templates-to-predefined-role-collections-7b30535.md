<!-- loio7b305356bac74694bee8ddfe3e47427a -->

# Cannot Add Role Templates to Predefined Role Collections



## Symptom

You want to update your SAP Authorization and Trust Management service \(XSUAA\) instance and add role templates to a previously defined role collection in the *xs-security.json*. The service instance update fails with the error message:

```
Cannot add or remove role-template-references from role collection if already in use (app subscribed or role collection assigned to user). Please create a new role-collection with a different name instead.
```



## Reason and Prerequisites

You tried to add a role template to an existing role collection that is already in use. If your application was either subscribed \(for a multi-tenant enabled application\) or the role collection in question was already assigned to a user, an update of the role collection is not possible anymore. The security reason for this is that role collections might have already been audited by subscribers and/or the security administrator assigned these role collections to users based on the initial state of the role collections. Changes to the role collections at a later point in time would render these audits invalid.

**In general, you should never modify any authorization object \(role template, role\) that is already in use in a way that it grants additional authorization without explicit approval of the user and role administrator.**



## Solution



### Create a new role collection with a different name

You can add an additional role collection with a different name to your *xs-security.json*. Administrators can then audit the new role collection and migrate the users to the updated role collection. To do this, follow these steps:

1.  Add a new role collection with a different name to the *xs-security.json*.
2.  Add/modify the role templates within that role collection according to your needs.
3.  Update the SAP Authorization and Trust Management service service instance. See [Update Service Instances Using the SAP BTP Cockpit or Cloud Foundry Command Line Interface](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/54fe2e7250924b12916897727ea78d29.html).
4.  Assign the new role collection to the application users.
5.  \(Optional\) When all users have been migrated to the new role collection, remove the old role collection from the *xs-security.json*.
6.  \(Optional\) Update the SAP Authorization and Trust Management service service instance.



For more information about the creation of role collections and the *xs-security.json*, see [Create Role Collections \(with Predefined Roles\)](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/fe750543788a40b79a49854590ad0b11.html) and [Application Security Descriptor Configuration Syntax](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/517895a9612241259d6941dbf9ad81cb.html).

