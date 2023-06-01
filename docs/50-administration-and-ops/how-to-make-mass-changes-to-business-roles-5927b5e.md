<!-- copy5927b5ebd0944e399d90fdbb073cf939 -->

# How to Make Mass Changes to Business Roles



<a name="copy5927b5ebd0944e399d90fdbb073cf939__HowToMakeMassChangesBusinessRoles_context"/>

## Context

You can use the mass change wizard to change multiple business roles at once. This is helpful, for example, if you have switched from using custom spaces to SAP-delivered spaces or if you start using spaces. In that case, you can select all affected business roles and click *Assign SAP-Delivered Spaces*. The system then automatically assigns SAP-delivered spaces to all of the business roles in question. If you click *Remove Launchpad Spaces Already Assigned*, the custom spaces that were assigned to the business roles previously are automatically removed.

Select the business roles you want to change and click *Mass Change*. The *Mass Change Wizard* appears. It has the following pattern:



<a name="copy5927b5ebd0944e399d90fdbb073cf939__HowToMakeMassChangesBusinessRoles_steps"/>

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
    
        **Launchpad Space Assignment**


    
    </td>
    <td valign="top">
    
        Add Launchpad Spaces

    Remove Launchpad Spaces


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        **Assign SAP-Delivered Spaces**


    
    </td>
    <td valign="top">
    
        Assign SAP-Delivered Spaces to your business roles

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
    </table>
    
2.  Apply the required attributes to your business roles.

3.  Review and confirm your changes.

    Please note that some attributes might not be changeable if you have selected a combination of leading, non-leading and derived business roles. If you only select leading roles, all of the listed attributes are changeable.


**Related Information**  


[**Assigning an Existing Space to Several Business Roles**](https://help.sap.com/docs/SAP_S4HANA_CLOUD/4fc8d03390c342da8a60f8ee387bca1a/af2b6ad24bd94047bc5e0d84ecc7ebe3.html?version=latest)

