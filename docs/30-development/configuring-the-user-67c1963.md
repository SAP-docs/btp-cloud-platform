<!-- loio67c19637847049fb9d7c023af00e5f62 -->

# Configuring the User



In the **checked system**, the RFC user needs the following authorizations:

****


<table>
<tr>
<th valign="top">

Authorization Object Value

</th>
<th valign="top">

Parameter

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top" rowspan="3">

`S_RFC`

</td>
<td valign="top">

`ACTVT`

</td>
<td valign="top">

`16` \(Execute\)

</td>
</tr>
<tr>
<td valign="top">

`RFC_TYPE`

</td>
<td valign="top">

`FUGR`

</td>
</tr>
<tr>
<td valign="top">

`RFC_NAME`

</td>
<td valign="top">

`SCA_REMOTE_DATA_ACCESS`

`SABP_COMP_PROCS_E`

`SYCM_APS_REMOTE`

`SYST`

`S_CODE_INSPECTOR_TESTS`

`IQAPI_QUERY_CONTENT`

`IQAPI_INFOSET_CONTENT`

`IQAPI_CHECK_INFOSET`

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

`S_RFC`

</td>
<td valign="top">

`ACTVT`

</td>
<td valign="top">

`16` \(Execute\)

</td>
</tr>
<tr>
<td valign="top">

`RFC_TYPE`

</td>
<td valign="top">

`FUNC`

</td>
</tr>
<tr>
<td valign="top">

`RFC_NAME`

</td>
<td valign="top">

`FUNCTION_EXISTS`

`REPOSITORY_ENVIRONMENT_ALL`

`RFC_GET_NAMETAB`

`SVRS_GET_VERSION_DIRECTORY_46`

`RFCPING`

`SLINRMT_RUN`

`TRINT_PROGRESS_INDICATOR`

`TRINT_TP_UPDATE_TPSTAT`

</td>
</tr>
<tr>
<td valign="top" rowspan="5">

`S_DEVELOP`

</td>
<td valign="top">

`ACTVT`

</td>
<td valign="top">

`03` \(Display\)

</td>
</tr>
<tr>
<td valign="top">

`DEVCLASS`

</td>
<td valign="top">

`*`

</td>
</tr>
<tr>
<td valign="top">

`OBJNAME`

</td>
<td valign="top">

`*`

</td>
</tr>
<tr>
<td valign="top">

`OBJTYPE`

</td>
<td valign="top">

`*`

</td>
</tr>
<tr>
<td valign="top">

`P_GROUP`

</td>
<td valign="top">

`*`

</td>
</tr>
<tr>
<td valign="top" rowspan="4">

`S_SYS_RWBO`

</td>
<td valign="top">

`ACTVT`

</td>
<td valign="top">

`01` \(Create or generate\)

`02` \(Change\)

`03` \(Display\)

</td>
</tr>
<tr>
<td valign="top">

`DOMAIN`

</td>
<td valign="top">

`*`

</td>
</tr>
<tr>
<td valign="top">

`DESTSYS`

</td>
<td valign="top">

`*`

</td>
</tr>
<tr>
<td valign="top">

`TTYPE`

</td>
<td valign="top">

`TRAN`

</td>
</tr>
<tr>
<td valign="top" rowspan="2">

`S_TRANSPRT`

</td>
<td valign="top">

`ACTVT`

</td>
<td valign="top">

`01` \(Create or generate\)

`02` \(Change\)

`03` \(Display\)

</td>
</tr>
<tr>
<td valign="top">

`TTYPE`

</td>
<td valign="top">

`TRAN`

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

`S_DATASET`

</td>
<td valign="top">

`ACTVT`

</td>
<td valign="top">

`34` \(Write\)

</td>
</tr>
<tr>
<td valign="top">

`FILENAME`

</td>
<td valign="top">

`*`

</td>
</tr>
<tr>
<td valign="top">

`PROGRAM`

</td>
<td valign="top">

`SAPLSABC`

`SAPLSTRF`

</td>
</tr>
</table>



In the **Central Check System**, you need the following user to use transaction `ATC` to perform custom code checks:


<table>
<tr>
<th valign="top">

User Role

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`SAP_SATC_ADMIN` 

</td>
<td valign="top">

Authorization for setting up ABAP Test Cockpit \(ATC\) for central quality checking

</td>
</tr>
</table>

In addition, you need the following authorization object for importing the Simplification Database into the Central Check System:


<table>
<tr>
<th valign="top">

Name of Authorization Object

</th>
<th valign="top">

Name of the Authorization Field

</th>
<th valign="top">

Value of the Authorization Field

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top" rowspan="2">

`S_YCM` 

</td>
<td valign="top">

`SYCM_AREA` 

</td>
<td valign="top">

`SDB` 

</td>
<td valign="top" rowspan="2">

Authorization for importing the Simplification Database

</td>
</tr>
<tr>
<td valign="top">

`ACTVT` 

</td>
<td valign="top">

`UL` 

</td>
</tr>
</table>

