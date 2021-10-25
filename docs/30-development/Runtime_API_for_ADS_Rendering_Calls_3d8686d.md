<!-- loio3d8686d312bc426d8b2aa323473996b0 -->

# Runtime API for ADS Rendering Calls

The `CL_FP_ADS_UTIL` class provides the ABAP Runtime API for *Adobe Document Service* \(ADS\) rendering calls. It contains the following *Public* methods to be used for the corresponding functions:

<a name="loio3d8686d312bc426d8b2aa323473996b0__table_fcg_fcv_pqb"/>Public Methods


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

 `RENDER_PDF` 



</td>
<td valign="top">

Rendering PDF



</td>
</tr>
<tr>
<td valign="top">

 `RENDER_4_PQ` 



</td>
<td valign="top">

Rendering for Print Queue



</td>
</tr>
</table>

The PDF rendering process on ADS creates the PDF file to be printed \(or print output format\) using the following both formats:

-   XDP form template file

-   Data for the form filling in XML format, for example, data from the [RAP Data Services for Print Forms](RAP_Data_Services_for_Print_Forms_a104660.md).


The XDP form template file is a description of the form layout design in Adobe XFA format. The supported data binding type is an XML data schema.

The *Adobe LiveCycle Designer for SAP solutions* is the tool for visual design XDP form templates from Adobe Inc. It can be downloaded using the *Install Additional Software* app, which contains the download link to the SAP ONE Support Launchpad.

The data XML file contains the data that corresponds to the used data schema in the XDP form template.



<a name="loio3d8686d312bc426d8b2aa323473996b0__section_iwl_vdv_pqb"/>

## Rendering PDF

The `RENDER_PDF` method calls the ADS to render print PDF using the XDP form file and the XML data file. It has the following importing/exporting parameters:

<a name="loio3d8686d312bc426d8b2aa323473996b0__table_jbr_c2v_pqb"/>Importing Parameters


<table>
<tr>
<th valign="top">

Parameter



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `IV_XML_DATA` 



</td>
<td valign="top">

XML data



</td>
</tr>
<tr>
<td valign="top">

 `IV_XDP_LAYOUT` 



</td>
<td valign="top">

Adobe XDP form template



</td>
</tr>
<tr>
<td valign="top">

 `IV_LOCALE` 



</td>
<td valign="top">

Locale for rendering the language: `language_COUNTRY`, for example en\_US



</td>
</tr>
<tr>
<td valign="top">

 `IS_OPTIONS` 



</td>
<td valign="top">

PDF rendering parameters \(optional\)



</td>
</tr>
</table>

<a name="loio3d8686d312bc426d8b2aa323473996b0__table_y1v_w2v_pqb"/>Exporting Parameters


<table>
<tr>
<th valign="top">

Parameter



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `EV_PDF` 



</td>
<td valign="top">

PDF rendering result



</td>
</tr>
<tr>
<td valign="top">

 `EV_PAGES` 



</td>
<td valign="top">

Number of pages



</td>
</tr>
<tr>
<td valign="top">

 `EV_TRACE_STRING` 



</td>
<td valign="top">

Trace string



</td>
</tr>
</table>

> ### Sample Code:  
> ```
> 
> TRY.
> * Simple render pdf
>     cl_fp_ads_util=>render_pdf( EXPORTING iv_xml_data      = gv_xml_data 
>                                           iv_xdp_layout    = gv_xdp
>                                           iv_locale        = 'de_DE'
>                                           is_options       = lv_options
>                                 IMPORTING ev_pdf           = ev_pdf
>                                           ev_pages         = ev_pages
>                                           ev_trace_string  = ev_trace_string
>                                           ).
>   CATCH cx_fp_ads_util INTO lx_fp_ads_util.
> 
>   ENDTRY.
> 
> ```



<a name="loio3d8686d312bc426d8b2aa323473996b0__section_wxw_gfv_pqb"/>

## Rendering for Print Queue

The `RENDER_4_PQ` method calls the ADS to render the print output format required for the target print queue. The support of the *Print Definition Language* \(PDL\) print queue format will be taken from print queue properties.

<a name="loio3d8686d312bc426d8b2aa323473996b0__table_g3h_pfv_pqb"/>Importing Parameters


<table>
<tr>
<th valign="top">

Parameter



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `IV_XML_DATA` 



</td>
<td valign="top">

XML data



</td>
</tr>
<tr>
<td valign="top">

 `IV_XDP_LAYOUT` 



</td>
<td valign="top">

Adobe XDP form template



</td>
</tr>
<tr>
<td valign="top">

 `IV_LOCALE` 



</td>
<td valign="top">

Locale for rendering the language: `language_COUNTRY`, for example en\_US



</td>
</tr>
<tr>
<td valign="top">

 `IV_PQ_NAME` 



</td>
<td valign="top">

 `Print Queue name` 



</td>
</tr>
<tr>
<td valign="top">

 `IS_OPTIONS` 



</td>
<td valign="top">

PDF rendering parameters \(optional\)



</td>
</tr>
</table>

<a name="loio3d8686d312bc426d8b2aa323473996b0__table_y21_wfv_pqb"/>Exporting Parameters


<table>
<tr>
<th valign="top">

Parameter



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `EV_PDL` 



</td>
<td valign="top">

PDF rendering result



</td>
</tr>
<tr>
<td valign="top">

 `EV_PAGES` 



</td>
<td valign="top">

Number of pages



</td>
</tr>
<tr>
<td valign="top">

 `EV_TRACE_STRING` 



</td>
<td valign="top">

Trace string



</td>
</tr>
</table>

> ### Sample Code:  
> ```
> 
> TRY.
>     cl_fp_ads_util=>render_4_pq( EXPORTING iv_xml_data      = gv_xml_data
>                                            iv_xdp_layout    = gv_xdp
>                                            iv_locale        = 'en_US'
>                                            iv_pq_name       = 'PQ1'
>                                            is_options       = lv_options
>                                  IMPORTING ev_pdl           = ev_pdl
>                                            ev_pages         = ev_pages
>                                            ev_trace_string  = ev_trace_string
>                                            ).
>     CATCH cx_fp_ads_util INTO lx_fp_ads_util.
> 
>     ENDTRY.
> 
> ```

