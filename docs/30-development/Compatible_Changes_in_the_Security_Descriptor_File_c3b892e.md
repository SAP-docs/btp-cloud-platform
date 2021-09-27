<!-- loioc3b892e703174badb93f1ab35f76c354 -->

# Compatible Changes in the Security Descriptor File

If you update a service instance, you can add, change, and/or delete scopes, attributes, and role templates. Whenever you change role templates, you adapt roles that are derived from the changed role template.



<a name="loioc3b892e703174badb93f1ab35f76c354__table_y45_p3b_z5"/>Compatible Changes in `xs-security.json`


<table>
<tr>
<th>

Security Artifacts in the xs-security.json File



</th>
<th>

Action



</th>
</tr>
<tr>
<td>

Scope



</td>
<td>

-   Add

-   Delete

-   Change

    -   `description`

    -   `granted-apps`



</td>
</tr>
<tr>
<td>

Attribute



</td>
<td>

-   Add

-   Delete

-   Change

    -   `description`


> ### Note:  
> Do not change the `valueType` of the attribute.



</td>
</tr>
<tr>
<td>

Role template



</td>
<td>

-   Add

-   Delete

-   Change

    -   `description`

    -   `scope-references`
    -   `attribute-references` \(can be deleted only\)



</td>
</tr>
</table>

