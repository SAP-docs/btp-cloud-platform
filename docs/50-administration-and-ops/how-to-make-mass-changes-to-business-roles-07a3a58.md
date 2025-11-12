<!-- loio07a3a58ecdbb481cab76fc4e867811cb -->

# How to Make Mass Changes to Business Roles



<a name="loio07a3a58ecdbb481cab76fc4e867811cb__HowToMakeMassChangesBusinessRoles_context"/>

## Context

You can use the mass change wizard to change multiple business roles at once. This is helpful, for example, if you have switched from using custom spaces to predefined spaces or if you start using spaces. In that case, you can select all affected business roles and choose *Assign Space Templates*. The system then automatically assigns predefined spaces to all of the business roles in question. If you choose *Remove Launchpad Spaces Already Assigned*, the custom spaces that were previously assigned to the business roles are automatically removed.

> ### Note:  
> Please note that SAP-defined business roles can only be modified for business user assignment in the initial setup. Apart from this, they can be updated by SAP only. We recommend that you create your own business roles from templates so that you can modify them as required.

Select the business roles you want to change and click *Mass Change*. The *Mass Change Wizard* appears. The pattern of the wizard is described in the next section.

> ### Caution:  
> If you have selected a combination of leading, non-leading, and derived business roles, some attributes might not be selectable. For example, business catalogs in derived business roles can't be edited. Therefore, business catalogs are not included in the mass change if a derived business role is selected.
> 
> To change all of the listed attributes, select only leading business roles.



<a name="loio07a3a58ecdbb481cab76fc4e867811cb__HowToMakeMassChangesBusinessRoles_steps"/>

## Procedure

1.  Select the required attributes. You can make the following changes:


    <table>
    <tr>
    <th valign="top">

    Area
    
    </th>
    <th valign="top">

    Attributes
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    **Business Role Data**
    
    </td>
    <td valign="top">
    
    Role Group

    Expose to SAP BTP

    Inherit Spaces in Derived Business Roles
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Business User Assignment**
    
    </td>
    <td valign="top">
    
    Add Business Users

    Remove Business Users
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Business Catalog Assignment**
    
    </td>
    <td valign="top">
    
    Add Business Catalogs

    Remove Business Catalogs
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **IAM App Activation**
    
    </td>
    <td valign="top">
    
    Activate IAM Apps

    Deactivate IAM Apps
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Launchpad Space Assignment**
    
    </td>
    <td valign="top">
    
    Add Launchpad Spaces

    Remove Launchpad Spaces
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Assign Space Templates**
    
    </td>
    <td valign="top">
    
    Assign space templates to your business roles

    You see the results and can filter for error or success statuses in the *Mass Change Overview*.

    > ### Note:  
    > Please note that this option is only relevant for business roles that were created from business role templates.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Access Categories**
    
    </td>
    <td valign="top">
    
    Change access categories as required.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Restrictions**
    
    </td>
    <td valign="top">
    
    Select the required access category, such as *Value Help* and select the required restriction change, such as *Add Restrictions*.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Copy Restrictions**
    
    </td>
    <td valign="top">
    
    1.  Click *Add Restrictions* or *Remove Restrictions*.

    2.  Copy the required restrictions using the*Copy Restriction Values From*and the *Copy Restriction Values To* value help.
    3.  Select additional access categories if needed.

    > ### Note:  
    > You can use this option in case a restriction type is deprecated to copy restrictions from the deprecated restriction type to the successor restriction type\(s\). You can either add the copied restriction values in the fields to existing ones or remove all and replace them with the copied restrictions.


    
    </td>
    </tr>
    </table>
    
2.  Apply the required attributes to your business roles.

3.  Review and confirm your changes.


**Related Information**  


[Assigning Spaces to Several Business Roles at Once](https://help.sap.com/docs/SAP_S4HANA_CLOUD/4fc8d03390c342da8a60f8ee387bca1a/af2b6ad24bd94047bc5e0d84ecc7ebe3.html?version=latest)

 <?sap-ot O2O class="- topic/link " href="376bdf15d848467da5b2383454d53a24.xml" text="" desc="" xtrc="link:2" xtrf="file:/home/builder/src/dita-all/jjq1673438782153/loio2080d0faf9d84ce6aa14caa4caa32935_en-US/src/content/localization/en-us/07a3a58ecdbb481cab76fc4e867811cb.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 

