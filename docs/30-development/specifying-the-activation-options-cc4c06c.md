<!-- loiocc4c06ce643045298443e109108f9372 -->

# Specifying the Activation Options

The activation option *Activation Languages* can be customized if needed, or the default settings can be used. This indicates the languages in which the language-dependent contents of the business configuration set should be activated.

You can choose to activate the business configuration set with:

-   Default activation options: All active system languages are considered for the activation languages
-   Customized activation options: You can specify the languages in which the language-dependent contents are to be activated.

To customize the activation options, they can be accessed using the method `OPTIONS`, followed by calling the method `IF_SCPR_CD_BCSET_OPTNS_HANDLER~GET_ACTIVATE_OPTIONS( )`.

Method **`OPTIONS`**

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

Reference to instance of `IF_SCPR_CD_BCSET_OPTNS_HANDLER`

</td>
</tr>
</table>

Method **`IF_SCPR_CD_BCSET_OPTNS_HANDLER~GET_ACTIVATE_OPTIONS`**

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

Reference to instance of `IF_SCPR_CD_BCSET_ACTIV_OPTIONS`

</td>
</tr>
</table>

The method `IF_SCPR_CD_BCSET_ACTIV_OPTIONS~ADD_ACTIVATION_LANGUAGES` can be used to customize the activation languages.

Method **`IF_SCPR_CD_BCSET_ACTIV_OPTIONS~ADD_ACTIVATION_LANGUAGES`**

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

`IT_LANGUAGES`

</td>
<td valign="top">

List of activation languages \(corresponding key of the language\)

</td>
</tr>
</table>

The default or customized activation options can be set to the activation handler by calling the method `IF_SCPR_CD_BCSET_ACTIV_HANDLER~LOCAL( )` followed by a call to `IF_SCPR_CD_BCSET_ACTIV_ADD_OPT~ADD_ACTIVATION_OPTIONS( )`.

The call to method `IF_SCPR_CD_BCSET_ACTIV_HANDLER~LOCAL( )` indicates that the contents are deployed to the tables locally during activation and are not captured in a transport request.

> ### Sample Code:  
> ```abap
> 
> " Case 1) Default activation options
> DATA(lo_activate_handler) = cl_scpr_cd_bcset_activation=>of( ‘BCSET_NAME’ )->get_activate_handler( ).
> DATA(lo_activation_handler) = lo_activate_handler->local( )->add_activation_options( ).
> " Case 2) Customized activation options
> DATA(lo_activation_options) = cl_scpr_cd_bcset_activation=>options( )->get_activate_options( ).
> lo_activation_options->add_activation_languages( VALUE #( ( langu = 'E' ) ( langu = 'F' ) ) ).
> DATA(lo_activate_handler) = cl_scpr_cd_bcset_activation=>of( ‘BCSET_NAME’ )->get_activate_handler( ).
> DATA(lo_activation_handler) = lo_activate_handler->local( )->add_activation_options( lo_activation_options ).
> ```

