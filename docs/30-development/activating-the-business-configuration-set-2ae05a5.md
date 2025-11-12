<!-- loio2ae05a5577154d15826dd15599b37392 -->

# Activating the Business Configuration Set

Once the activation options have been set, the method `IF_SCPR_CD_BCSET_ACTIV_START~START( )` can be used to trigger the activation.

Method **`IF_SCPR_CD_BCSET_ACTIV_START~START`**

**Returning Parameter**


<table>
<tr>
<th valign="top">

Parameter Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`RO_RESULT`

</td>
<td valign="top">

Reference to instance of `IF_SCPR_CD_BCSET_ACTIV_RESULT`

</td>
</tr>
</table>

> ### Sample Code:  
> ```abap
> " Activating a business configuration set with the default activation options
> TRY.
> DATA(lo_activate_handler) = cl_scpr_cd_bcset_activation=>of( ‘BCSET_NAME’ )->get_activate_handler( ).
> DATA(lo_activation_result) = lo_activate_handler->local( )->add_activation_options( )->start( ).
> CATCH cx_scpr_object_not_permitted INTO DATA(lo_exception).
> cc Process the exception
> DATA(lv_exception_message) = lo_exception->get_text( ).
> ENDTRY.
> 
> ```

