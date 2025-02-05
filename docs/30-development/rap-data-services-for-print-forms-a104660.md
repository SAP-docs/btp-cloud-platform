<!-- loioa104660468324090b601ee2969a54d99 -->

# RAP Data Services for Print Forms

The XML data for print form rendering can be obtained from the RAP Business Services. The data model can be defined just as well as the *RAP Service Definition*. For more information, see [Service Definition](https://help.sap.com/docs/btp/sap-abap-restful-application-programming-model/service-definition?version=Cloud).

The `CL_FP_FDP_SERVICES` class provides the ABAP API to receive the following:

-   data in xml format for the use in print forms

-   XML Schema Definition \(XSD\) used for the design of print forms in the *Adobe LiveCycle Designer*.




<a name="loioa104660468324090b601ee2969a54d99__section_xpz_c5v_pqb"/>

## Initiate Business Data Reader

To supply the rendering operation with business data, a reuse service can be applied. Beforehand, a service definition needs to be created.

> ### Note:  
> The service definition doesn't need a binding for RAP Data Services for print forms.

1.  Initiate the reuse utility by specifying the service definition: `data(lo_fdp_api) = cl_fp_fdp_services=>get_instance( `FP_FDP_AUNIT_SO` )`.

2.  Specify the key parameters. This is required to read the data for a specific item. The reuse utility offers the following functionality to retrieve all key fields for the service definition: `data(lt_keys) = lo_fdp_api->get_keys( ).`

3.  Once you have retrieved the array with key values, assign the keys that fit to the document you want to output: `lt_keys[ name = 'UUID' ]-value = 'FA163EE47BDD1ED9A682A2E6F1ECF696'`.


> ### Sample Code:  
> ```
> 
> DATA(lo_fdp_api) = cl_fp_fdp_services=>get_instance( `FP_FDP_SERVICE_EX1` ).
> DATA(lt_keys)    = lo_fdp_api->get_keys( ).
> 
>   lt_keys[ name = 'UUID' ]-value = 'FA163EE47BDD1ED9A682A2E6F1ECF696'.
> ```



<a name="loioa104660468324090b601ee2969a54d99__section_ljl_3vv_pqb"/>

## Retrieve XML Data from Service Definition

The `READ_TO_XML` method retrieves the data structure of the service definition for a specific item. It has the following Importing parameters:

**Importing Paramaters**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Definition

</th>
</tr>
<tr>
<td valign="top">

`IT_SELECT` 

</td>
<td valign="top">

Key parameters

</td>
</tr>
<tr>
<td valign="top">

`IV_LANGUAGE` \(Optional\)

</td>
<td valign="top">

Overwrites the locale language \(useful if you want to control how dynamic values \(e.g. unites\) are resolved

</td>
</tr>
</table>

The `READ_TO_XML` method has the following returning parameters:

**Returning Paramaters**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Definition

</th>
</tr>
<tr>
<td valign="top">

`RV_XML` 

</td>
<td valign="top">

Resulting XML as XSTRING

</td>
</tr>
</table>

> ### Sample Code:  
> ```
> 
> TRY.
>     DATA(lt_keys)    = lo_fdp_api->get_keys(  ).
>     lt_keys[ name = 'UUID' ]-VALUE = 'FA163EE47BDD1ED9A682A2E6F1ECF696'.
>     DATA(lv_data) = lo_fdp_api->read_to_xml( lt_keys ).
>  CATCH cx_fp_fdp_error INTO DATA(lo_exception).
> ENDTRY.
> 
> ```



<a name="loioa104660468324090b601ee2969a54d99__section_w5r_cwv_pqb"/>

## Retrieve XML Schema Definition from Service Definition

The `GET_XSD` method retrieves the XML Schema Definition \(XSD\) for the service definition. It has the following returning parameters:

**Returning Paramaters**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Definition

</th>
</tr>
<tr>
<td valign="top">

`RV_XML` 

</td>
<td valign="top">

Resulting XSD as XSTRING

</td>
</tr>
</table>

> ### Sample Code:  
> ```
> 
> TRY.
>    DATA(lv_xml)     = lo_fdp_api->get_xsd(  ).
>  CATCH cx_fp_fdp_error INTO DATA(lo_exception).
> ENDTRY.
> 
> ```

