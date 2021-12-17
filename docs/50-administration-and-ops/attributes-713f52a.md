<!-- loio713f52ac36a041ef8fdc72560d6cfbcd -->

# Attributes

Attributes use information that is specific to the user, for example the user's country. If the application developer in the Cloud Foundry environment of SAP BTP has created a country attribute to a role, this restricts the data a business user can see based on this attribute.

A lot of applications provide purely functional role templates which grant access for all data of a certain type within your subaccount. Roles for such role templates are generated automatically. Some other applications also provide the possibility for administrators to restrict access not only by functional authorizations, but also by instance-based authorizations. That means that users can only work with a certain subset of the data in your subaccount.

The restriction can be either based on information within the respective role, or on user-specific information provided by the identity provider. This makes instance-based authorizations specific for each customer because the respective roles cannot be generated automatically. Instead, administrators must create them. Typical restrictions depend on information like the user's country or cost center.

Each restriction is represented by a dedicated attribute which belongs to a role template of the application.

> ### Note:  
> Application developers can define attribute references in the application security descriptor file \(`xs-security.json`\): For more information, see [Application Security Descriptor Configuration Syntax](../30-development/application-security-descriptor-configuration-syntax-517895a.md).

For each attribute, administrators have multiple options to specify the value which restricts data access:

-   Static attributes

    They are stored in the role. The user is given the attribute value when the administrator assigns the role collection with this role to the user.

-   Attributes from a custom identity provider

    Since an identity provider provides the business users, you can dynamically reference all attributes that come with the SAML 2.0 assertion. You define the attributes and the attribute values in the identity provider. In the Cloud Foundry environment of SAP BTP, administrators can use the assertion attributes to refine the roles.

    > ### Note:  
    > If you want to reference attributes from your identity provider, you must know the exact identifier of the assertion attribute. Go to the SAML 2.0 configuration of your identity provider and use the assertion attributes as they are defined there.
    > 
    > There is an exception. The following attributes from the identity provider are automatically mapped:
    > 
    > <a name="loio713f52ac36a041ef8fdc72560d6cfbcd__table_qxk_j43_vlb"/>Automatic Mapping of Attributes
    > 
    > 
    > <table>
    > <tr>
    > <th valign="top">
    > 
    > Attribute from Identity Provider
    > 
    > 
    > 
    > </th>
    > <th valign="top">
    > 
    > Automatically Mapped to Attribute
    > 
    > 
    > 
    > </th>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    >  *first\_name* 
    > 
    > 
    > 
    > </td>
    > <td valign="top">
    > 
    >  *given\_name* 
    > 
    > 
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    >  *last\_name* 
    > 
    > 
    > 
    > </td>
    > <td valign="top">
    > 
    >  *family\_name* 
    > 
    > 
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    >  *mail* 
    > 
    > 
    > 
    > </td>
    > <td valign="top">
    > 
    >  *email* 
    > 
    > 
    > 
    > </td>
    > </tr>
    > </table>

-   Unrestricted attributes

    In this case, you want to express that it is not necessary to set a specific value for this attribute. The behavior is the same as if the attribute would not exist for this role.


**Related Information**  


[Specify Attributes in a Role](specify-attributes-in-a-role-4827f0b.md "As an administrator of the Cloud Foundry environment, you can specify attributes in roles to refine authorizations of the business users. Depending on these attributes, business users with this role have restricted access to data.")

[Specify Attributes in a New Role](specify-attributes-in-a-new-role-ab089a9.md "As an administrator of the Cloud Foundry environment, you can specify attributes in a new role to refine authorizations of business users. Depending on these attributes, business users with this role have restricted access to data.")

