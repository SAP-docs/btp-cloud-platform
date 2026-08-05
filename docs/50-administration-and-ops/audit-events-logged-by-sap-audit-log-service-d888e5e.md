<!-- loiod888e5e5de0a4fab9179add2fa1aecf1 -->

# Audit Events Logged by SAP Audit Log service

The SAP Audit Log service records specific audit events related to data access and security activities when interacting with the Retrieval API.

**Audit Events**


<table>
<tr>
<th valign="top">

Audit Log Type

</th>
<th valign="top">

Type

</th>
<th valign="top">

When

</th>
<th valign="top">

Message

</th>
</tr>
<tr>
<td valign="top">

`data-access`

</td>
<td valign="top">

Data read event

</td>
<td valign="top">

Logged on every audit log retrieval attempt, regardless of whether records were returned, including whether the read was successful.

</td>
<td valign="top">

Attribute with name “data read event” was read/not read successfully. The attribute is a part of an object with type “data read event” and ID consisting of: tenant\_id “*<subaccount\_id\>*”. It belongs to a subject with type “account”, role “account”, and ID consisting of: id “*<uua-client-id\>*”.

</td>
</tr>
<tr>
<td valign="top">

`security-events`

</td>
<td valign="top">

Successful login

</td>
<td valign="top">

Logged each time a successful authentication is made against the Retrieval API.

</td>
<td valign="top">

Security event message “successful login event” on *<timestamp\>*. Security event was related to user “*<uua-client-id\>*”.

</td>
</tr>
<tr>
<td valign="top">

`security-events`

</td>
<td valign="top">

Unsuccessful login

</td>
<td valign="top">

Logged on failed authentication attempts.

</td>
<td valign="top">

Security event message “unsuccessful login event” on *<timestamp\>*. Security event was related to user “*<uua-client-id\>*”.

</td>
</tr>
</table>

