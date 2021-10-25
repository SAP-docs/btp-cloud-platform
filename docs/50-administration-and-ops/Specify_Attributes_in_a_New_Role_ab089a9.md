<!-- loioab089a9bb3c541e798dd4c9111417246 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Specify Attributes in a New Role

As an administrator of the Cloud Foundry environment, you can specify attributes in a new role to refine authorizations of business users. Depending on these attributes, business users with this role have restricted access to data.



<a name="loioab089a9bb3c541e798dd4c9111417246__prereq_dm3_wjq_wcb"/>

## Prerequisites

You have maintained the attributes of the users in your identity provider if you want to use the identity provider as the source of the attributes.

> ### Note:  
> In Identity Authentication or any SAML identity provider, you find the attributes in the SAML 2.0 configuration.



<a name="loioab089a9bb3c541e798dd4c9111417246__steps_i2c_jgr_wcb"/>

## Procedure

1.  Open the SAP BTP cockpit.

2.  Go to your global account \(China \(Shanghai\) region\) orsubaccount. For more information, see [Navigate in the Cockpit](Navigate_in_the_Cockpit_0874895.md).

3.  Choose your space in *Cloud Foundry* \> *Spaces* or, in the case of subscriptions, see [Configure Application Roles and Assign Roles to Users](Configure_Application_Roles_and_Assign_Roles_to_Users_56a7153.md).

4.  Choose the application.

5.  Choose *Security* \> *Roles*.

6.  To create a new role, choose <span class="SAP-icons"></span> \(Add\) in the first row.

    A wizard guides you through the role creation process.

7.  Enter a name and a description of the new role.

8.  Select the role template you want to use.

9.  Choose *Next*.

10. To specify an attribute, choose the source of the attribute. The following sources are available:

    <a name="loioab089a9bb3c541e798dd4c9111417246__table_iyh_gps_5cb"/>Attribute Sources


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
    
11. Choose *Next*.

12. Select the role collections for your new role. For more information, see the related link.

13. Choose *Next* and *Finish*.

    You have now created a new role with attributes.


**Related Information**  


[Subscribe to Multitenant Applications Using the Cockpit](Subscribe_to_Multitenant_Applications_Using_the_Cockpit_7a3e396.md "Subscribe to multitenant applications from the Subscriptions page in the SAP BTP cockpit.")

[Maintain Role Collections](Maintain_Role_Collections_d5f1612.md "Role collections group together different roles that can be applied to the application users.")

[Attributes](Attributes_713f52a.md "Attributes use information that is specific to the user, for example the user's country. If the application developer in the Cloud Foundry environment of SAP BTP has created a country attribute to a role, this restricts the data a business user can see based on this attribute.")

