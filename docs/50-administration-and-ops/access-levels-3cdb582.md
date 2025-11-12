<!-- loio3cdb582583b342fd82b3caf3f3763af8 -->

# Access Levels

Authorizations of SAP support users



Access levels define the authorizations of SAP support users when accessing customer systems.

**Access Levels**


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Use

</th>
</tr>
<tr>
<td valign="top">

*SUPPORT\_DEFAULT* \(Platform Analysis, Display Configuration, No Business Authorization\)

</td>
<td valign="top">

The *SUPPORT\_DEFAULT* access level provides display access to ABAP Platform transactions, display of Customizing tables and views, display of system tables with content delivered by SAP or transported in customer systems. It also provides authorization to display, activate and deactivate transient logs and traces without access to payload data. It grants authorization for the debugging of the own user and external debugging of other users. Authorization to change values of variables or to alter the code flow in the debugger is not granted. In case business authorizations are required for support, they are agreed in customer support cases and are copied from a specific customer business user or customer communication user as additional authorization.

</td>
</tr>
<tr>
<td valign="top">

*SUPPORT\_DEFAULT\_APP* \(Platform Analysis, Display Configuration, Display Business Data\)

</td>
<td valign="top">

The *SUPPORT\_DEFAULT\_APP* access level inherits all the authorizations from the *SUPPORT\_DEFAULT* access level. Additionally, it grants display access to application tables and selected business transactions that enable analysis. It includes display of most business application logs as well as display, activation and deactivation of transient traces with access to payload data. Authorization to change customer data is not granted.

</td>
</tr>
<tr>
<td valign="top">

*SUPPORT\_EXTENDED* \(Platform Analysis, Limited Administration, Full Business Authorization\)

</td>
<td valign="top">

The *SUPPORT\_EXTENDED* access level inherits all the authorizations from the *SUPPORT\_DEFAULT\_APP* access level. Additionally, it grants full business application authorization. It includes all backend transactions and reports of the application layer. It grants limited ABAP Platform administration authorization, such as deletion of caches. Authorization to change system configuration, Customizing data, or development objects is not granted.

</td>
</tr>
<tr>
<td valign="top">

*SUPPORT\_CUSTOMIZING* \(Limited Platform Customizing, Full Business Customizing\)

</td>
<td valign="top">

The *SUPPORT\_CUSTOMIZING* access level inherits all the authorizations from the *SUPPORT\_DEFAULT\_APP* access level. Additionally, it grants authorization to maintain selected ABAP Platform Customizing as well as unrestricted business application Customizing.

</td>
</tr>
<tr>
<td valign="top">

*SUPPORT\_CONTENT\_ACT* \(Content Activation\)

</td>
<td valign="top">

The *SUPPORT\_CONTENT\_ACT* access level inherits all the authorizations from the *SUPPORT\_EXTENDED* and the *SUPPORT\_CUSTOMIZING* access levels. Additionally, it grants administrative authorization to the content framework which manages the Customizing content lifecycle.

</td>
</tr>
<tr>
<td valign="top">

*SUPPORT\_DEVELOP\_LOCAL* \(Local Development\)

</td>
<td valign="top">

The *SUPPORT\_DEVELOP\_LOCAL* access level inherits all the authorizations from the *SUPPORT\_EXTENDED* access level. Additionally, it grants authorization to create and execute local development objects. This access level may need to be used to support frameworks that generate local development objects in the customer name space \(such as extensibility or data migration\). It allows to test execute all function modules and static methods. It also allows changing field values and altering the code flow in the debugger. Authorizations to modify development objects delivered by SAP are not granted.

</td>
</tr>
<tr>
<td valign="top">

*SUPPORT\_DEVELOP* \(Unrestricted Development\)

</td>
<td valign="top">

The *SUPPORT\_DEVELOP* access level inherits all the authorizations from the *SUPPORT\_DEVELOP\_LOCAL* access level. Additionally, it grants authorization to modify development objects delivered by SAP. Standard procedure for such changes is a hotfix or an emergency patch. This access level may only be used in emergency situations where that process is not applicable.

</td>
</tr>
<tr>
<td valign="top">

*SUPPORT\_USER\_ADMIN* \(User and Role Administration\)

</td>
<td valign="top">

The *SUPPORT\_USER\_ADMIN* access level inherits all the authorizations from the *SUPPORT\_DEFAULT* access level. Additionally, it grants authorization for local user and role administration. This access level may be used for support cases related to business user or communication user management.

</td>
</tr>
<tr>
<td valign="top">

*SUPPORT\_SYSTEM\_CONFIG* \(System Configuration\)

</td>
<td valign="top">

The *SUPPORT\_SYSTEM\_CONFIG* access level inherits all the authorizations from the *SUPPORT\_EXTENDED* access level. Additionally, it grants authorization to manually configure SAP managed communication scenarios. Automatic setup is mandatory for such communication scenarios in customer systems. This access level is used in situations where automatic setup failed.

</td>
</tr>
<tr>
<td valign="top">

*SUPPORT\_SYSTEM\_ADMIN* \(Unrestricted System Administration\)

</td>
<td valign="top">

The *SUPPORT\_SYSTEM\_ADMIN* access level grants unrestricted administrative access. It includes authorization profile SAP\_ALL. Cloud operations may need to use it for system lifecycle management. Support teams may need to request it as the final escalation of privileges for support cases that cannot be resolved with other access levels. Root case analysis is mandated for such support cases. The root cause must be resolved.

</td>
</tr>
</table>

**Related Information**  


[SAP Support User Request Log](sap-support-user-request-log-934a027.md "The SAP Support User Request Log is part of the Display Technical Users app.")

[Access Categories](access-categories-7dbdd05.md "")

