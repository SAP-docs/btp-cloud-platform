<!-- loioff688591ae914d67bffce58bb04c4d99 -->

# Categories of Audit Relevant Events

Find explained the four categories of Audit Relevant Events.




<table>
<tr>
<th valign="top">

Category

</th>
<th valign="top">

Description

</th>
<th valign="top">

Examples

</th>
</tr>
<tr>
<td valign="top">

Log read access to sensitive personal data

</td>
<td valign="top">

Use a data-accesses audit log record for the cases where an access to personal data is executed. The audit log contains information on the accessed personal data, as well as the full information of the user that is accessing the personal data, the owner of the personal data \(the Data Subject\), and the identifier of the place where the access to the personal data have been executed \(the Object\).

</td>
<td valign="top">

Examples of personal data access events are all the read accesses sensitive personal data, which means information on racial or ethnic origin, political opinions, religious or philosophical beliefs, trade-union membership, health or sex life, bank account and credit card data, genetic data and bio-metric data for the purpose of uniquely identifying a natural person.

</td>
</tr>
<tr>
<td valign="top">

Log changes to personal data

</td>
<td valign="top">

Use a data-modification audit log record for the events that are related to modification of personal data. The audit log contains information on the modified personal data, as well as the full information of the user that is accessing the personal data, the owner of the personal data \(the Data Subject\), and the identifier of the place where the access to the personal data have been executed \(the Object\).

</td>
<td valign="top">

Examples of personal data modification events are writing, deleting, or changes on an address, e-mail address, phone number, and any other data that can lead to a persona identification.

</td>
</tr>
<tr>
<td valign="top">

Security event log

</td>
<td valign="top">

Log security data for all events that might have an impact over the system security.

</td>
<td valign="top">

Examples for such events are successful and non-successful login and logout events, changes in access control permissions, changes in credentials, changes in sensitive configurations, and so on.

</td>
</tr>
<tr>
<td valign="top">

Configuration change log

</td>
<td valign="top">

Use the configuration change audit log events for various changes in configurations. The audit log contains the changed configuration parts with old and new value. Log only the changed parts with the old and new value. If old or new value doesn't exist in case of adding a new property or deleting one respectively, skip the missing values or set them as null.

</td>
<td valign="top">

Examples of configuration change events are creation/deletion of service instances, binding/unbinding service instances, software update, changes in configurations, and so on.

</td>
</tr>
</table>

