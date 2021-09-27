<!-- loioec89f523d96a44f0b0a46adc21187ff2 -->

# CL\_BALI\_LOG\_FILTER \(Interface IF\_BALI\_LOG\_FILTER\)

Class `CL_BALI_LOG_FILTER` allows to define a filter which can be used if logs shall be read from the database and if the log handles are not known. The public interface of the instance methods is `IF_BALI_LOG_FILTER`.

**Public Methods**



Create an instance of the filter class:

<a name="loioec89f523d96a44f0b0a46adc21187ff2__table_g5t_khb_xlb"/>**CREATE \(static\)**


<table>
<tr>
<th>

Name



</th>
<th>

Description



</th>
</tr>
<tr>
<td colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td>

FILTER



</td>
<td>

Filter object: A reference to interface IF\_BALI\_LOG\_FILTER



</td>
</tr>
</table>



Set object, subobject and external identifier of the log. It overwrites all previous filter settings of object, subobject and external identifier:

<a name="loioec89f523d96a44f0b0a46adc21187ff2__table_pyx_h3b_xlb"/>**SET\_DESCRIPTOR**


<table>
<tr>
<th>

Name



</th>
<th>

Description



</th>
</tr>
<tr>
<td colspan="2">

**Importing parameters**



</td>
</tr>
<tr>
<td>

OBJECT



</td>
<td>

\(Optional\): Object of the log \(no wildcards\)



</td>
</tr>
<tr>
<td>

SUBOBJECT



</td>
<td>

\(Optional\): Subobject of the log \(wildcards allowed\)



</td>
</tr>
<tr>
<td>

SUBOBJECT\_TABLE



</td>
<td>

\(Optional\): Table with subobjects \(wildcards allowed\)



</td>
</tr>
<tr>
<td>

EXTERNAL\_ID



</td>
<td>

\(Optional\): External identifier of the log \(wildcards allowed\)



</td>
</tr>
<tr>
<td>

EXTERNAL\_ID\_TABLE



</td>
<td>

\(Optional\): Table with external identifiers \(wildcards allowed\)



</td>
</tr>
<tr>
<td colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td>

NEW\_FILTER



</td>
<td>

Reference to current filter object



</td>
</tr>
<tr>
<td colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**



</td>
</tr>
<tr>
<td>

CX\_BALI\_NOT\_POSSIBLE



</td>
<td>

ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>OBJECT\_NOT\_ALLOWED:

Access to the log object is not allowed



</td>
</tr>
</table>

> ### Note:  
> If parameter EXTERNAL\_ID is supplied and empty, the filter searches for logs with empty external identifier.
> 
> If parameters OBJECT or SUBOBJECT are supplied and empty, they are ignored



Set information about the log creation like the user. It overwrites all previous filter settings about the log creation:

<a name="loioec89f523d96a44f0b0a46adc21187ff2__table_qjc_s4b_xlb"/>**SET\_CREATE\_INFO**


<table>
<tr>
<th>

Name



</th>
<th>

Description



</th>
</tr>
<tr>
<td colspan="2">

**Importing parameters**



</td>
</tr>
<tr>
<td>

USER



</td>
<td>

\(Optional\): Log user \(wildcards allowed\)



</td>
</tr>
<tr>
<td>

USER\_TABLE



</td>
<td>

\(Optional\): Table with log users \(wildcards allowed\)



</td>
</tr>
<tr>
<td colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td>

NEW\_FILTER



</td>
<td>

Reference to current filter object



</td>
</tr>
</table>

> ### Note:  
> If parameter USER is supplied and empty, it is ignored.



Set the date and time interval of the log creation. It overwrites all previous filter settings of the time interval:

<a name="loioec89f523d96a44f0b0a46adc21187ff2__table_lvp_cpb_xlb"/>**SET\_TIME\_INTERVAL**


<table>
<tr>
<th>

Name



</th>
<th>

Description



</th>
</tr>
<tr>
<td colspan="2">

**Importing parameters**



</td>
</tr>
<tr>
<td>

START\_TIME



</td>
<td>

UTC time stamp of the start time of the time interval



</td>
</tr>
<tr>
<td>

END\_TIME



</td>
<td>

UTC time stamp of the end time of the time interval



</td>
</tr>
<tr>
<td colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td>

NEW\_FILTER



</td>
<td>

Reference to current filter object



</td>
</tr>
</table>



Set the maximum number of logs which are processed:

<a name="loioec89f523d96a44f0b0a46adc21187ff2__table_vxf_3pb_xlb"/>**SET\_MAXIMUM\_LOG\_NUMBER**


<table>
<tr>
<th>

Name



</th>
<th>

Description



</th>
</tr>
<tr>
<td colspan="2">

**Importing parameters**



</td>
</tr>
<tr>
<td>

MAX\_LOG\_NUMBER



</td>
<td>

Maximum number of logs which are processed \(0 = all logs are processed which is the default\)



</td>
</tr>
<tr>
<td colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td>

NEW\_FILTER



</td>
<td>

Reference to current filter object



</td>
</tr>
</table>



Get all filter values:

<a name="loioec89f523d96a44f0b0a46adc21187ff2__table_vml_npb_xlb"/>**GET\_ALL\_VALUES**


<table>
<tr>
<th>

Name



</th>
<th>

Description



</th>
</tr>
<tr>
<td colspan="2">

**Exporting parameters**



</td>
</tr>
<tr>
<td>

OBJECT\_TABLE



</td>
<td>

Table of objects \(no wildcards\)



</td>
</tr>
<tr>
<td>

SUBOBJECT\_TABLE



</td>
<td>

Table of subobjects \(wildcards allowed\)



</td>
</tr>
<tr>
<td>

EXTERNAL\_ID\_TABLE



</td>
<td>

Table of external identifiers \(wildcards allowed\)



</td>
</tr>
<tr>
<td>

USER\_TABLE



</td>
<td>



</td>
</tr>
<tr>
<td>

TIME\_INTERVAL



</td>
<td>

Date and time interval



</td>
</tr>
<tr>
<td>

MAX\_LOG\_NUMBER



</td>
<td>

Maximum number of logs processed



</td>
</tr>
</table>

