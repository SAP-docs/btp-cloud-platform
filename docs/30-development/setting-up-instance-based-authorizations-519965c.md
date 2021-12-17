<!-- loio519965ca3f214a788c9d24eed3513119 -->

# Setting Up Instance-Based Authorizations

Instance-based authorizations are authorization checks based on the value of some authorization-relevant attribute defined by the application. Functional authorizations define whether you've permission to edit or view some function in the application, while instance-based authorizations define what data you can act upon.

As a developer, you develop your application as you did in our previous examples for functional authorization checks. In that example, we defined attributes in the application security descriptor \(`xs-security.json`\) even though we didn't use them. In that example, we defined *CostCenter* as an attribute. Let's look at an example.

Your application is used by a controller to view the expenses of their organization. So, your application shows the controller all invoices, which belong to the cost center of the controller. So, your application takes the dataset of invoices and shows the instance of that dataset where the cost center equals the cost center of the controller. Control access to this dataset by creating a role collection that includes the *CostCenter* attribute and the value required by the controller. Then assign that role collection to the user of the controller.

For more information about defining attributes in the application security descriptor, see [Add Authentication and Functional Authorization Checks to Your Application](add-authentication-and-functional-authorization-checks-to-your-application-0a69484.md).

For instance-based authorizations, you build checks against these attributes into your coding. To help you understand authorization checks against attributes, check out our sample bulletin board application on Github.

For more information, see [https://github.com/SAP-samples/cloud-application-security-sample/tree/master/spring-security-basis](https://github.com/SAP-samples/cloud-application-security-sample/tree/master/spring-security-basis).

Once you've built in your authorization checks, you've a few ways to populate the attributes with values, for your code to check.



<a name="loio519965ca3f214a788c9d24eed3513119__section_zhf_4fx_z4b"/>

## How Attribute Values Are Set

Once you've defined attributes in your role templates, how are attribute values filled? There are a couple different ways.

-   Predefine the attribute values in role collections you deliver with your app.

    As a developer, you can define preconfigured role collections in your application security descriptor. When the role administrator assigns these role collections to users, the attribute values are hard-coded with the default values according to the role templates you define. These role collections enable a role administrator to get their users started quickly.

-   The administrator builds static roles from your role templates.

    The administrator builds the roles they need, based on the role templates you deliver. The administrator builds each role, setting the values for the attributes you defined in the role templates. The administrator can't add or subtract any attributes. The administrator can only set the values. The administrator then bundles these roles into role collections and assigns them to users.

-   The administrator builds dynamic roles from your role templates.

    The administrator builds the roles they need, based on the role templates you deliver. The administrator can decide to populate role values dynamically from the identity provider. When users log on, they receive a token with attributes defined by the identity provider. The manager of the identity provider controls the values a user has for given attributes, not the role administrator of the subaccount. This setup means that you as an application developer need to understand what kinds of attributes are available to the role administrator from the identity provider.


**Related Information**  


[Attributes](../50-administration-and-ops/attributes-713f52a.md "Attributes use information that is specific to the user, for example the user's country. If the application developer in the Cloud Foundry environment of SAP BTP has created a country attribute to a role, this restricts the data a business user can see based on this attribute.")

