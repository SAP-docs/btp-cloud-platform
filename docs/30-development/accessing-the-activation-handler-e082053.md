<!-- loioe082053e2c8947a4bf1f9674fa592981 -->

# Accessing the Activation Handler

You can access the activation handler by specifying the name of the business configuration set.

Instantiate the class using the method `OF` and provide the name of the *Business Configuration Set* to be activated. If the specified business configuration set does not exist or the checks based on the object restrictions and language version fail, the exception `CX_SCPR_OBJECT_NOT_PERMITTED` is raised.

Method **`OF`**

**Importing Parameter**


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

`IV_BCSET`

</td>
<td valign="top">

Name of the business configuration Sst

</td>
</tr>
</table>

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

Reference to instance of `IF_SCPR_CD_BCSET_AVTIVATION`

</td>
</tr>
</table>

Use the instance method `IF_SCPR_CD_BCSET_ACTIV_START~GET_ACTIVATE_HANDLER( )` to access the activation handler.

Method **`IF_SCPR_CD_BCSET_ACTIVATION~GET_ACTIVATE_HANDLER`**

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

Reference to instance of `IF_SCPR_CD_BCSET_ACTIV_HANDLER`

</td>
</tr>
</table>

> ### Sample Code:  
> ```abap
> 
> TRY. 
> DATA(lo_bcset_activate) = cl_scpr_cd_bcset_activation=>of( 'BUSINESS_CONFIGURATION_SET_NAME’ ). 
> DATA(lo_activation_handler) = lo_bcset_activate->get_activate_handler( ).
> CATCH cx_scpr_object_not_permitted INTO DATA(lo_exception). 
> " Process the exception 
> DATA(lv_exception_message) = lo_exception->get_text( ). 
> ENDTRY.
> 
> ```

