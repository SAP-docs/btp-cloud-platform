<!-- loio1fd787382ccf472082b0be08a2790323 -->

# Mapping the Identity Provider Group Developers to the Neo Group

Map the developer group of the identity provider to the Neo developer group with the Web IDE `DiDeveloper` role.



<a name="loio1fd787382ccf472082b0be08a2790323__context_nfj_pmd_r2b"/>

## Context

> ### Note:  
> The following steps are only relevant if your developers will use SAP Web IDE in the Neo environment for UI development.

The mapping is part of the trust configuration to the SAML identity provider. For more information, see [Configure Trust to the SAML Identity Provider](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/dc618538d97610148155d97dcd123c24.html#loiob6cfc4bb4bff4ace90afc71b0962fcb5).



## Procedure

1.  Log on to the SAP BTP cockpit \(Neo account\) as Neo administration user.

2.  In the navigation area, choose *Security* \> *Trust*.

3.  Choose the *Application Identity Provider* tab.

4.  Choose the link for the custom identity authentication service tenant.

5.  Choose the *Groups* tab.

6.  If no group for Neo developers exists, choose *Add Assertion-Based Group*.

7.  Enter the following data:


    <table>
    <tr>
    <th valign="top">

    Option
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *Group*
    
    </td>
    <td valign="top">
    
    Select *Developers.*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Mapping Rules* \(part 1\)
    
    </td>
    <td valign="top">
    
    Enter *Groups*.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Mapping Rules* \(part 2\)
    
    </td>
    <td valign="top">
    
    Select

    *equals*.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Mapping Rules* \(part 3\)
    
    </td>
    <td valign="top">
    
    Enter the developer group name from the Identity Authentication service that was created by the administrator for the Identity Authentication service, for example, *Developers*.

    If you are not the responsible administrator for the Identity Authentication service, make sure that you are informed about the group name \(see also [Creating an Identity Provider Group for Developers](creating-an-identity-provider-group-for-developers-2f72082.md)\).
    
    </td>
    </tr>
    </table>
    
8.  Choose *Save*.


