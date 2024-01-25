<!-- loio9d0c427605804b2184a6d66c6a363747 -->

# Glossary




<table>
<tr>
<th valign="top">

Term

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Central Check System

</td>
<td valign="top">

Backend system that provides and performs the SAP S/4HANA custom code checks for one or multiple SAP systems remotely.

</td>
</tr>
<tr>
<td valign="top">

Checked System

</td>
<td valign="top">

Represents a test or development system that includes the custom code to be checked.

</td>
</tr>
<tr>
<td valign="top">

Check Variant

</td>
<td valign="top">

A check variant consists of one or several check categories, which, in turn, consist of one or several individual checks. A check variant also includes the configuration of the checks.

</td>
</tr>
<tr>
<td valign="top">

CVA License

</td>
<td valign="top">

Remote security checks are only available for SAP customers with a Code Vulnerability Analyzer \(CVA\) license, that is, license for *SAP Code Vulnerability Analyzer* as a separate, fee-based product.

</td>
</tr>
<tr>
<td valign="top">

Exemption

</td>
<td valign="top">

If the checked code is not supposed to be corrected, the developer can request an exemption for a check, or an individual check message, for a single finding, or a number of findings within the same package or development object. Once approved by a quality manager, the finding does no longer appear as an open issue in the new ATC results.

</td>
</tr>
<tr>
<td valign="top">

Object Provider

</td>
<td valign="top">

An object provider defines the connection between the checked system and the central check system. While an ATC check run is executed, the ATC runtime uses this RFC connection to the checked system to extract a model from the custom code.

</td>
</tr>
<tr>
<td valign="top">

Remote-enabled ATC Check

</td>
<td valign="top">

Remote-enabled ATC checks can be run when a remote analysis is being performed in the central check system.

</td>
</tr>
<tr>
<td valign="top">

Remote-enabled Check Variant

</td>
<td valign="top">

The check variant is classified as remote-enabled if it consists of remote ATC checks only.

</td>
</tr>
<tr>
<td valign="top">

Remote Stubs \(RFC Stubs\)

</td>
<td valign="top">

*Remote Stubs* serve as an interface between the *Central Check System*and the *Checked Systems*. *Remote Stubs* extract a model from the custom code, which is used by the ATC check in the *Central Check System* to analyze the source code of the *Checked Systems*.

</td>
</tr>
<tr>
<td valign="top">

System Group

</td>
<td valign="top">

A system group subsumes multiple SAP systems \(typically, the productive system, the test system\(s\), and the development system\(s\)\), which all represent a part of a system landscape of one and the same SAP release

In central check systems, ATC exemptions are no more valid for all checks executed in the system, but for a *System Group* only:

-   Therefore, every *Object Provider* must be assigned to a *System Group*.

-   All checks executed on base of *Object Providers* that are assigned to the same *System Group* share the exemptions available for this group.




</td>
</tr>
</table>

