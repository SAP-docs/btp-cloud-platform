<!-- loio578c4de3c21a4f6a9c9658d2fce72290 -->

# Email Address Check



## Email Address Validation

The class `CL_MAIL_ADDRESS` implements the interface`IF_MAIL_ADDRESS` and enables the user to validate the provided email address. This class checks whether the provided email address is syntactically valid according to the RFC 5322 standard.



<a name="loio578c4de3c21a4f6a9c9658d2fce72290__section_qhl_2sw_wvb"/>

## Create an E-Mail Address instance

****


<table>
<tr>
<th valign="top">

Method

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Create\_instance

</td>
<td valign="top">

Provides an email address instance.

</td>
</tr>
<tr>
<td valign="top">

validate

</td>
<td valign="top">

Validates whether a string is a syntactic valid mail address \(according to RFC 5322 Standard\).

</td>
</tr>
</table>



<a name="loio578c4de3c21a4f6a9c9658d2fce72290__section_xhz_lsw_wvb"/>

## Methods

> ### Sample Code:  
> ```abap
> Try.
>         Data(lo_mail_address) = cl_mail_address=>create_instance( iv_address_string = ‘testmail@ok.com’ ).
>     Catch cx_bcs_mail into data(lx_err).
>         "exception handling
> endtry.
> ```
> 
> <code><code>Data(lv_address_valid) = lo_mail_address-&gt;validate( ).</code></code>

