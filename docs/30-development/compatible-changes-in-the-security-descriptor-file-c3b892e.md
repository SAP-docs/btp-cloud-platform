<!-- loioc3b892e703174badb93f1ab35f76c354 -->

# Compatible Changes in the Security Descriptor File

If you update a service instance, you can add, change, and/or delete scopes, attributes, and role templates. Whenever you change role templates, you adapt roles that are derived from the changed role template.



**Compatible Changes in xs-security.json**


<table>
<tr>
<th valign="top">

Security Artifacts in the xs-security.json File



</th>
<th valign="top">

Action



</th>
</tr>
<tr>
<td valign="top">

Scope



</td>
<td valign="top">

-   Add

-   Delete

-   Change

    -   `description`

    -   `granted-apps`




</td>
</tr>
<tr>
<td valign="top">

Attribute



</td>
<td valign="top">

-   Add

-   Delete

-   Change

    -   `description`



> ### Note:  
> Do not change the `valueType` of the attribute.



</td>
</tr>
<tr>
<td valign="top">

Role template



</td>
<td valign="top">

-   Add

-   Delete

-   Change

    -   `description`

    -   `scope-references`
    -   `attribute-references` \(can be deleted only\)


> ### Restriction:  
> When you define or update role templates and attributes, observe the following configuration restrictions in [**Relationship Between ***default-values*** of ***attribute-references*** and ***valueRequired*****](https://help.sap.com/docs/btp/sap-business-technology-platform/application-security-descriptor-configuration-syntax#loio517895a9612241259d6941dbf9ad81cb__section_c1n_jfd_tkb).



</td>
</tr>
</table>

