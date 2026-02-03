<!-- loio67c19637847049fb9d7c023af00e5f62 -->

# Configuring the User



You can either apply SAP Note [3548772](https://me.sap.com/notes/3548772) in the **checked system** to get all relevant authorizations for your RFC user or, alternatively, check the table below.

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

`SUSG_API`

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

`SLDAG_GET_SYSTEM_NAME`

`CVA_BSP_RUN`

`IDOCTYPE_COLLECT_ATC_INFOS`

`IQAPI_QUERY_CONTENT`

`IQAPI_INFOSET_CONTENT`

`IQAPI_CHECK_INFOSET`

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

> ### Note:  
> To launch **ABAP unit tests**, you need the following authorizations:
> 
> -   `S_DEVELOP` with ACTVT = 'EU' \(Automated Tests\) or ACTVT = '16' \(Execute\).
> -   If a language version check is active in your system, you also need: `S_ABPLNGVS` with ABP\_LNG\_VS = '5' and ACTVT = 'EU' or ACTVT = '16'.



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

