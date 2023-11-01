<!-- loiof647ef4602dc461488cc82444141b51a -->

# Class and Interface of the PDF Merger API

Class `CL_RSPO_PDF_MERGER` uses interface `IF_RSPO_PDF_MERGER`. Find out which public methods it contains.



<a name="loiof647ef4602dc461488cc82444141b51a__section_ifh_qrn_1xb"/>

## Context

The following public methods exist in interface `IF_RSPO_PDF_MERGER` :



### CREATE\_INSTANCE \(static\)

Create an instance of the PDF merger class.


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**

</td>
</tr>
<tr>
<td valign="top">

`MERGER_INSTANCE`

</td>
<td valign="top">

PDF merger instance: A reference to interface `IF_RSPO_PDF_MERGER`

</td>
</tr>
</table>



### ADD\_DOCUMENT

Add a PDF document to the list of files that you want to merge.


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top" colspan="2">

**Importing parameter**

</td>
</tr>
<tr>
<td valign="top">

`DOCUMENT`

</td>
<td valign="top">

Data of the PDF document that you want to merge \(type `XSTRING`\)

</td>
</tr>
</table>



### MERGE\_DOCUMENTS

Merge all PDF documents into a single PDF file.


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**

</td>
</tr>
<tr>
<td valign="top">

`MERGED_DOCUMENT`

</td>
<td valign="top">

Data of the merged document \(type `XSTRING`\)

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Exceptions**

</td>
</tr>
<tr>
<td valign="top">

`CX_RSPO_PDF_MERGER`

</td>
<td valign="top">

Exceptions of the PDF merger

</td>
</tr>
</table>

**Related Information**  


[PDF Merger API](pdf-merger-api-57013a7.md "You can use a class-based API to merge the content of different PDF files into a single PDF file. The result file contains all pages of the source files in the sequence of the original files.")

