<!-- loiobf7a980559e44ddf91cbf6a0f6696387 -->

# Writing Change Documents

Write change documents

The `WRITE` method in the generated class `CL_<change document object name>_CHDO` creates change documents from the object-specific update for an object ID.

**Import Parameters**


<table>
<tr>
<th valign="top">

Parameter Name

</th>
<th valign="top">

Value Help

</th>
</tr>
<tr>
<td valign="top">

OBJECTID

</td>
<td valign="top">

Identifier of the changed application object

</td>
</tr>
<tr>
<td valign="top">

UTIME

</td>
<td valign="top">

Time of change

</td>
</tr>
<tr>
<td valign="top">

UDATE

</td>
<td valign="top">

Date of change

</td>
</tr>
<tr>
<td valign="top">

USERNAME

</td>
<td valign="top">

User name of the person responsible in change document

</td>
</tr>
<tr>
<td valign="top">

PLANNED\_CHANGE\_NUMBER

</td>
<td valign="top">

Planned change number \(only for writing planned changes\)

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_CHANGE\_INDICATOR

</td>
<td valign="top">

Type of Change to Application Object. Possible values are:

-   U - Change

-   I - Insert

-   D - Delete




</td>
</tr>
<tr>
<td valign="top">

PLANNED\_OR\_REAL\_CHANGES

</td>
<td valign="top">

You can use this parameter to control whether the changes to be logged are actual or planned changes.

Available values:

-   "R" actual \(real\) changes -"P" planned changes

-   if there is no plan number: actual change

    if there is a plan number: planned change




</td>
</tr>
<tr>
<td valign="top">

NO\_CHANGE\_POINTERS

</td>
<td valign="top">

‘X’: no change pointers will be written. Change pointers are used for Application Link Enabling \(ALE\) master data scenarios. Currently, this parameter is obsolete for SAP Business Technology Platform \(SAP BTP\), ABAP Environment.

</td>
</tr>
<tr>
<td valign="top">

ICDTXT\_<change document object name\>

</td>
<td valign="top">

In this structure, the change document-relevant texts are collected with the corresponding specifications:

-   TEILOBJID: Key of changed table row

-   TEXTART: Text type of changed text

-   TEXTSPR: Language Key

-   UPDKZ: Change flag for table row: D\(elete\), I\(nsert\) or U\(pdate\)




</td>
</tr>
<tr>
<td valign="top">

UPD\_ICDTXT\_<change document object name\>

</td>
<td valign="top">

Change flag for text table:

-   " " \(Space\): Table is not considered.

-   "U": Table is considered




</td>
</tr>
<tr>
<td valign="top">

O\_<table name\>

</td>
<td valign="top">

Object-specific parameter for single case tables with the same table structure as <table name\>. The workarea must contain the original data.

</td>
</tr>
<tr>
<td valign="top">

N\_<table name\>

</td>
<td valign="top">

Object-specific parameter for single case tables with the same table structure as <table name\>. The workarea must contain the original data.

</td>
</tr>
<tr>
<td valign="top">

Y<table name\>

</td>
<td valign="top">

Object-specific parameter for multiple case tables.

The table must contain the original version of the changed or deleted records. The structure consists of the table, as specified in the change document object definition under table name, a processing flag \(TYPE C, length 1\)

</td>
</tr>
<tr>
<td valign="top">

X<table name\>

</td>
<td valign="top">

The table must contain the current version of the changed or created records. The structure is the same as Y<table name\> \(see above\). Is is not necessary to set the processing flag to values <\> space for standard behavior. The following values for the processing flag exist:

-   "I" \(INSERT\)Records were created, or table records were deleted, then a record with the same key was created in the same transaction, and this is to be documented as "Delete" and "Create" \(special case\), not as "Change".

-   "U" or " " \(space\) \(UPDATE\)


The parameter UPD\_<table name \> \(see below\) initially determines whether the record is new or changed. The processing flag is only checked when - with the parameter value "U" - the following key comparison between the two tables x<table name\> and y<table name\> finds two records with the same key.

</td>
</tr>
<tr>
<td valign="top">

UPD\_<table name \>

</td>
<td valign="top">

With this flag, you determine the processing logic. The following values exist:

-   "D" \(DELETE\) A change document item is to be created for each record in Y<table name \>. X<table name\> is not processed.

-   "I" \(INSERT\)A change document item is to be created for each record in X<table name\>. Y<table name\> is not processed.

-   "U" \(UPDATE\)The keys of Y<table name\> and X<table name\> are compared. The following cases are distinguished:

    -   Record exists in Y<table name\> but not in X<table name\>: Change document items are to be created for the record in Y<table name\> which is to be deleted.

    -   Record exists in X<table name\> but not in Y<table name\>: A change document item is to be created for the records in X<table name\> which are to be flagged as created.

    -   Record exists in both Y<table name\> and X<table name\> and processing flag in X<table name\> record is "U" or space: A change document item is created for each changed field which is defined as change document-relevant in the dictionary.

    -   Record exists in both Y<table name\> and X<table name\> and processing flag in X<table name\> record is "I": Chage document item is to be created for the record in Y<table name\> which is to be deleted and change document item is to be created for the record in X<table name\> which is to be flagged as created.

    -   " " \(space, no processing\) X<table name\> and Y<table name\> are not processed by the `WRITE` method. \(If no changes have been made, the processing can be skipped to save time.\)





</td>
</tr>
</table>

**Export Parameter**


<table>
<tr>
<th valign="top">

Parameter Name

</th>
<th valign="top">

Value Help

</th>
</tr>
<tr>
<td valign="top">

CHANGENUMBER

</td>
<td valign="top">

Change number of the document

</td>
</tr>
</table>

> ### Sample Code:  
> ```abap
> 
> " example for change document object ZTEST_1
>   " with tables
>   " ZTEST_1 single case and
>   " ZTEST_2 multiple case
> 
>   " Start of default parameter part
>   DATA: objectid        TYPE if_chdo_object_tools_rel=>ty_cdobjectv,
>   	  utime           TYPE if_chdo_object_tools_rel=>ty_cduzeit,
>         udate           TYPE if_chdo_object_tools_rel=>ty_cddatum,
>         username        TYPE if_chdo_object_tools_rel=>ty_cdusername,
>         cdoc_upd_object TYPE if_chdo_object_tools_rel=>ty_cdchngindh VALUE 'U'.
>   DATA: cdchangenumber  TYPE if_chdo_object_tools_rel=>ty_cdchangenr.
>   " End of default parameter part
> 
>   " Begin of dynamic DATA part for class ZCL_ZTEST_1_CHDO
>   " declaration for the long text : ICDTXT_ZTEST_1
>   DATA icdtxt_ztest_1 TYPE if_chdo_object_tools_rel=>ty_cdtxt_tab.
>   " update indicator for the long text
>   DATA upd_icdtxt_ztest_1 TYPE if_chdo_object_tools_rel=>ty_cdchngindh.
> 
>   " workaera_old of ZTABLE_1
>   DATA os_ztable_1 TYPE ztable_1.
>   " workaera_new of ZTABLE1
>   DATA ns_ztable_1 TYPE ztable_1.
>   " change indicator for ZTABLE_1
>   DATA upd_ztable_1 TYPE if_chdo_object_tools_rel=>ty_cdchngindh.
> 
>   " table with the NEW content of: ZTABLE_2
>   DATA xztable_2 TYPE zcl_ztest_1_chdo=>tt_ztable_2.
>   " table with the OLD content of: ZTABLE_2
>   DATA yztable_2 TYPE zcl_ztest_1_chdo=>tt_ztable_2.
>   " change indicator for table: ZTABLE_2
>   DATA upd_ztable_2 TYPE if_chdo_object_tools_rel=>ty_cdchngindh.
> 
>   " Change Number of Document
>   DATA changenumber TYPE if_chdo_object_tools_rel=>ty_cdchangenr.
> 
> * save old values before change
> 
> 
> * do some application changes to ZTABLE_1 and ZTABLE_2.
> 
> " set the change indicator for tables ('U', 'D', 'I')
> " upd_ztable_1 = 'U'.
> " upd_ztable_2 = 'U'.
> 
> " set change document application object identifier (objectid, date, time and user)
> " objectid				 = 'Testobject'.
> " utime				    = 'hhmmss'.
> " udate	   			 = 'ddmmyyyy'.
> " username				 = 'Testusername'.
> " set change indicator for change document header
>   cdoc_upd_object = 'U'.
> 
> " prepare old and new tables
>   SORT yztable_2.
>   DELETE ADJACENT DUPLICATES FROM yztable_2.
>   SORT xztable_2.
>   DELETE ADJACENT DUPLICATES FROM xztable_2.
> 
>   " Begin of method call part
>   " define needed DATA for error handling
>    DATA err_ref TYPE REF TO cx_chdo_write_error.
>    DATA err_action TYPE string.
> 
>     TRY.
>  	   CALL METHOD zcl_ztest_1_chdo=>write
>  	     EXPORTING
> "  Begin of default method call part
> 		    objectid = objectid
> 		    utime = utime
> 		    udate = udate
> 		    username = username
> 		    object_change_indicator = cdoc_upd_object
> "  End of default method call part
> 
> "  Begin of dynamic part for method call
>  	   "  declaration for the long text : ICDTXT_ZTEST_1
>  		  icdtxt_ztest_1 = icdtxt_ztest_1
>  	   "  update indicator for the long text
>  		  upd_icdtxt_ztest_1 = upd_icdtxt_ztest_1
> 
>  	   " workaera_old of ZTABLE_1
>  		 o_ztable_1 = os_ztable_1
>  	   " workaera_new of ZTABLE_1
> 		  n_ztable_1 = ns_ztable_1
> 	    " change indicator for ZTABLE_1
> 		  upd_ztable_1 = upd_ztable_1
> 
>  	   " table with the NEW content of: ZTABLE_2
>  		 xztable_2 = xztable_2
>  	   " table with the OLD content of: ZTABLE_2
> 		  yztable_2 = yztable_2
> 	    " change indicator for table: ZTABLE_2
> 		  upd_ztable_2 = upd_ztable_2
> " End of dynamic part for method call
> 	  " Change Number of Document
> 	    IMPORTING
> 		  changenumber = changenumber.
> 	 CATCH cx_chdo_write_error INTO err_ref.
> 		 out->write( |Exception occurred: { err_ref->get_text( ) }| ).
>     ENDTRY.
> 
> ...
> ```

