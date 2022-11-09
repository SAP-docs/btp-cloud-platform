<!-- loio7dbdd05b6d164ddba14768a563a84bd2 -->

# Access Categories



Access categories classify the purpose of SAP support user access to customer systems.

**Access Categories**


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

 *Operations*



</td>
<td valign="top">

The *Operations* access category is used for system access by central cloud operations teams for system lifecycle management, reactive system management and proactive system management. Such access is not based on individual support cases. Taking over authorization from customer business users or customer communication users is not possible.



</td>
</tr>
<tr>
<td valign="top">

*Customer Support*



</td>
<td valign="top">

The *Customer Support* access category is used for system access based on support cases raised by the customer. The purpose of the system access is documented in a customer support case and can be reviewed in customer service management.System access is restricted to a processor of a customer case that is not completed. Support cases created for productive systems also allow access to non-productive systems. Support cases created for non-productive systems do not allow system access to productive systems. System access to a productive system requires a case for that specific system.Customers may allow the processor to copy authorizations from one specific customer business user or customer communication user. Consent to that is documented in the customer support case. The processor of the case can then copy these authorizations in addition to a support access level. The *SUPPORT\_DEFAULT* and*SUPPORT\_DEFAULT\_APP* support access levels are automatically approved for processors of customer support cases to access customer systems. The *SUPPORT\_EXTENDED* support access level is also automatically approved for processors of customer support cases to access non-productive customer systems. To access productive customer systems using the *SUPPORT\_EXTENDED* support access level, an SAP internal approval process is in place for SAP S/4HANA Cloud as well as SAP BTP ABAP environment. Any requests for higher privileged support access levels in customer systems enforce the principle of dual control using SAP internal approval processes.



</td>
</tr>
<tr>
<td valign="top">

*Health Check Support*



</td>
<td valign="top">

The *Health Check Support* access category is used for system access based on support incidents raised internally by automatic health checks. The purpose of the system access is documented by SAP internally via the incidents. Procedures for approval of access levels match the procedures of the *Customer Support* access category. The same is true for restrictions of access to productive systems versus non-productive systems.



</td>
</tr>
<tr>
<td valign="top">

*Emergency Support*



</td>
<td valign="top">

Support user access is controlled by a platform for central cloud management. The *Emergency Support* access category is used for locally created support users in situations where the connection to the central cloud management is interrupted. The purpose of the emergency support access is documented in a customer support case and can be reviewed in customer service management.



</td>
</tr>
<tr>
<td valign="top">

*SAP Internal Support*



</td>
<td valign="top">

The*SAP Internal Support* access category is used for system access to SAP internal test or demo systems. It is not intended for system access to customer systems. We recommend that you create an incident for cloud operations to validate the configuration of support user access if there is any such access in customer systems.



</td>
</tr>
</table>

**Related Information**  


[SAP Support User Request Log](sap-support-user-request-log-934a027.md "")

[Access Levels](access-levels-3cdb582.md "Authorizations of SAP support users")

