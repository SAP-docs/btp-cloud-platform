<!-- loioec89f523d96a44f0b0a46adc21187ff2 -->

# CL\_BALI\_LOG\_FILTER \(Interface IF\_BALI\_LOG\_FILTER\)

Class `CL_BALI_LOG_FILTER` allows to define a filter which can be used if logs shall be read from the database and if the log handles are not known. The public interface of the instance methods is `IF_BALI_LOG_FILTER`.

**Public Methods**



Create an instance of the filter class:

**CREATE \(static\)**


<table>
<tr>
<th valign="top">

Name



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td valign="top">

FILTER



</td>
<td valign="top">

Filter object: A reference to interface IF\_BALI\_LOG\_FILTER



</td>
</tr>
</table>



Set object, subobject and external identifier of the log. It overwrites all previous filter settings of object, subobject and external identifier:

**SET\_DESCRIPTOR**


<table>
<tr>
<th valign="top">

Name



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top" colspan="2">

**Importing parameters**



</td>
</tr>
<tr>
<td valign="top">

OBJECT



</td>
<td valign="top">

\(Optional\): Object of the log \(no wildcards\)



</td>
</tr>
<tr>
<td valign="top">

SUBOBJECT



</td>
<td valign="top">

\(Optional\): Subobject of the log \(wildcards allowed\)



</td>
</tr>
<tr>
<td valign="top">

SUBOBJECT\_TABLE



</td>
<td valign="top">

\(Optional\): Table with subobjects \(wildcards allowed\)



</td>
</tr>
<tr>
<td valign="top">

EXTERNAL\_ID



</td>
<td valign="top">

\(Optional\): External identifier of the log \(wildcards allowed\)



</td>
</tr>
<tr>
<td valign="top">

EXTERNAL\_ID\_TABLE



</td>
<td valign="top">

\(Optional\): Table with external identifiers \(wildcards allowed\)



</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td valign="top">

NEW\_FILTER



</td>
<td valign="top">

Reference to current filter object



</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**



</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_NOT\_POSSIBLE



</td>
<td valign="top">

ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>OBJECT\_NOT\_ALLOWED:

Access to the log object is not allowed



</td>
</tr>
</table>

> ### Note:  
> If parameter EXTERNAL\_ID is supplied and empty, the filter searches for logs with empty external identifier.
> 
> If parameters OBJECT, SUBOBJECT, SUBOBJECT\_TABLE, or EXTERNAL\_ID\_TABLE are supplied and empty, they are ignored



Set information about the log creation like the user. It overwrites all previous filter settings about the log creation:

**SET\_CREATE\_INFO**


<table>
<tr>
<th valign="top">

Name



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top" colspan="2">

**Importing parameters**



</td>
</tr>
<tr>
<td valign="top">

USER



</td>
<td valign="top">

\(Optional\): Log user \(wildcards allowed\)



</td>
</tr>
<tr>
<td valign="top">

USER\_TABLE



</td>
<td valign="top">

\(Optional\): Table with log users \(wildcards allowed\)



</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td valign="top">

NEW\_FILTER



</td>
<td valign="top">

Reference to current filter object



</td>
</tr>
</table>

> ### Note:  
> If parameters USER or USER\_TABLE are supplied and empty, they are ignored.



Set the date and time interval of the log creation. It overwrites all previous filter settings of the time interval:

**SET\_TIME\_INTERVAL**


<table>
<tr>
<th valign="top">

Name



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top" colspan="2">

**Importing parameters**



</td>
</tr>
<tr>
<td valign="top">

START\_TIME



</td>
<td valign="top">

UTC time stamp of the start time of the time interval



</td>
</tr>
<tr>
<td valign="top">

END\_TIME



</td>
<td valign="top">

UTC time stamp of the end time of the time interval



</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td valign="top">

NEW\_FILTER



</td>
<td valign="top">

Reference to current filter object



</td>
</tr>
</table>



Set the maximum number of logs which are processed:

**SET\_MAXIMUM\_LOG\_NUMBER**


<table>
<tr>
<th valign="top">

Name



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top" colspan="2">

**Importing parameters**



</td>
</tr>
<tr>
<td valign="top">

MAX\_LOG\_NUMBER



</td>
<td valign="top">

Maximum number of logs which are processed \(0 = all logs are processed which is the default\)



</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td valign="top">

NEW\_FILTER



</td>
<td valign="top">

Reference to current filter object



</td>
</tr>
</table>



Get all filter values:

**GET\_ALL\_VALUES**


<table>
<tr>
<th valign="top">

Name



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top" colspan="2">

**Exporting parameters**



</td>
</tr>
<tr>
<td valign="top">

OBJECT\_TABLE



</td>
<td valign="top">

Table of objects \(no wildcards\)



</td>
</tr>
<tr>
<td valign="top">

SUBOBJECT\_TABLE



</td>
<td valign="top">

Table of subobjects \(wildcards allowed\)



</td>
</tr>
<tr>
<td valign="top">

EXTERNAL\_ID\_TABLE



</td>
<td valign="top">

Table of external identifiers \(wildcards allowed\)



</td>
</tr>
<tr>
<td valign="top">

USER\_TABLE



</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

TIME\_INTERVAL



</td>
<td valign="top">

Date and time interval



</td>
</tr>
<tr>
<td valign="top">

MAX\_LOG\_NUMBER



</td>
<td valign="top">

Maximum number of logs processed



</td>
</tr>
</table>

