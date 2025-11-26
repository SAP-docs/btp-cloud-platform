<!-- loio4827f0bbe27d459fad8342896d4e569b -->

# Specify Attributes in a Role

As an administrator of the Cloud Foundry environment, you can specify attributes in roles to refine authorizations of the business users. Depending on these attributes, business users with this role have restricted access to data.



<a name="loio4827f0bbe27d459fad8342896d4e569b__prereq_dm3_wjq_wcb"/>

## Prerequisites

You have maintained the attributes of the users in your identity provider.

> ### Note:  
> In SAP Cloud Identity Services or any identity provider, you find the attributes in the configuration.



## Procedure

1.  Open the SAP BTP cockpit.

2.  Go to your subaccount.

    For more information, see [Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md).

3.  Choose your space in *Cloud Foundry* \> *Spaces* or, in the case of subscriptions, see  <?sap-ot O2O class="- topic/xref " href="56a71531fc154717bf221f9e293ba215.xml" text="" desc="" xtrc="xref:2" xtrf="file:/home/builder/src/dita-all/jjq1673438782153/loio2080d0faf9d84ce6aa14caa4caa32935_en-US/src/content/localization/en-us/4827f0bbe27d459fad8342896d4e569b.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> .

4.  Choose the application.

5.  Choose *Security* \> *Roles*.

6.  Select a role.

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

    Value/Attribute
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *Static* 
    
    </td>
    <td valign="top">
    
    Enter a static value, for example `USA` to refine the role depending on the country.

    > ### Remember:  
    > Follow entries with the [Enter\] key. Otherwise you can't save the role.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Identity Provider* 
    
    </td>
    <td valign="top">
    
    Enter an attribute as defined in your identity provider. Check in your identity provider for the exact syntax of the attribute identifier.

    For SAP Cloud Identity Services, you find the attribute identifier in the settings of the attributes of your identity provider under *Applications & Resources* \> *Applications* \> **<Application\_Name\>** \> *Trust* \> *Attributes*.

    > ### Example:  
    > To use the attribute for cost center, you must enter the value `cost_center`.


    
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

[Attributes](attributes-713f52a.md "Attributes use information that is specific to the user, for example the user's country. If the application developer in the Cloud Foundry environment of SAP BTP has created a country attribute to a role, this restricts the data a business user can see based on this attribute.")

