<!-- loio4827f0bbe27d459fad8342896d4e569b -->

# Specify Attributes in a Role

As an administrator of the Cloud Foundry environment, you can specify attributes in roles to refine authorizations of the business users. Depending on these attributes, business users with this role have restricted access to data.



<a name="loio4827f0bbe27d459fad8342896d4e569b__prereq_dm3_wjq_wcb"/>

## Prerequisites

You have maintained the attributes of the users in your identity provider if you want to use the identity provider as the source of the attributes.

> ### Note:  
> In Identity Authentication or any SAML identity provider, you find the attributes in the SAML 2.0 configuration.



## Procedure

1.  Open the SAP BTP cockpit.

2.  Go to your global account \(cloud management tools feature set B \) orsubaccount \(cloud management tools feature set A\). For more information, see [Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md).

3.  Choose your space in *Cloud Foundry* \> *Spaces* or, in the case of subscriptions, see [Configure Application Roles and Assign Roles to Users](configure-application-roles-and-assign-roles-to-users-56a7153.md).

4.  Choose the application.

5.  Choose *Security* \> *Roles*.

6.  Choose ![](images/Edit_Icon_abfe424.png) \(Edit\).

    The role overview pane displays the attribute name and fields where you can select the source and enter a value.

7.  Choose *Edit*.

8.  To specify an attribute, choose the source of the attribute. The following sources are available:

    **Attribute Sources**


    <table>
    <tr>
    <th valign="top">

    Source


    
    </th>
    <th valign="top">

    Value/SAML Attribute


    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
         *Static* 


    
    </td>
    <td valign="top">
    
        Enter a static value, for example ***USA*** to refine the role depending on the country.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
         *Identity Provider \(SAML\)* 


    
    </td>
    <td valign="top">
    
        Enter an assertion attribute as defined in your identity provider. Check in your identity provider for the exact syntax of the assertion attribute identifier.

    In the case of an SAP Cloud Identity Services - Identity Authentication, you find the attribute identifier in the settings of the SAML assertion attributes of your SAML identity provider under *Applications & Resources* \> *Applications*.

    > ### Example:  
    > To use the assertion attribute for cost center, you must enter the value ***cost\_center***.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
         *Unrestricted* 


    
    </td>
    <td valign="top">
    
        In this case, you want to express that it is not necessary to set a specific value for this attribute. The behavior is the same as if the attribute would not exist for this role.


    
    </td>
    </tr>
    </table>
    
9.  Save your changes.


**Related Information**  


[Subscribe to Multitenant Applications Using the Cockpit](subscribe-to-multitenant-applications-using-the-cockpit-7a3e396.md "Subscribe to multitenant applications from the Subscriptions page in the SAP BTP cockpit.")

[Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

[Attributes](attributes-713f52a.md "Attributes use information that is specific to the user, for example the user's country. If the application developer in the Cloud Foundry environment of SAP BTP has created a country attribute to a role, this restricts the data a business user can see based on this attribute.")

