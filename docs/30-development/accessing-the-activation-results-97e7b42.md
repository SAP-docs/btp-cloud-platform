<!-- loio97e7b4231685456b8f9f7f1ee3d92672 -->

# Accessing the Activation Results

Upon activation of the business configuration set, the instance returned from method `START( )` can be used to check if the activation was successful, using the method `IF_SCPR_CD_BCSET_ACTIV_RESULT~IS_BCSET_ACTIVATION_SUCCESSFUL( )`.

The log messages from the activation can be accessed using the method `IF_SCPR_CD_BCSET_ACTIV_RESULT~GET_MESSAGES( )`.

Method **`IF_SCPR_CD_BCSET_ACTIV_RESULT~IS_BCSET_ACTIVATION_SUCCESSFUL`**

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

`RV_RESULT`

</td>
<td valign="top">

`ABAP_TRUE` if the activation was successful, else `ABAP_FALSE`

</td>
</tr>
</table>

Method **`IF_SCPR_CD_BCSET_ACTIV_RESULT~GET_MESSAGES`**

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

`RT_MESSAGES`

</td>
<td valign="top">

Log messages from the activation – of type `BAPIRETTAB`

</td>
</tr>
</table>

> ### Sample Code:  
> ```abap
> " lo_result is the instance returned from calling IF_SCPR_CD_BCSET_ACTIV_START->START( )
> " Check if activation was successful
> DATA(lv_status) = lo_result->is_bcset_activation_successful( ).
> " Get the activation log messages
> DATA(lt_activation_messages) = lo_result->get_messages( ).
> 
> ```

