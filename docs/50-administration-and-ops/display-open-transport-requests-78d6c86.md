<!-- loio78d6c8669451423eb377865266a4fa38 -->

# Display Open Transport Requests

Displaying Open Transport Requests: Use this to easily view all open transport requests for a specific software component. It provides the unique identifier, description, owner, and last update of each request.





### Context

To view all open transport requests for the selected software component on the current system instance, follow these steps. Please note that open transport requests from other system instances will not be displayed.



### Procedure

1.  Open the **Manage Software Components** Fiori app.
2.  Select the software component you are interested in.
3.  Scroll down to the section **Open Transports** to display the table.



### Table Explanation


<table>
<tr>
<th valign="top">

Column

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Transport Request

</td>
<td valign="top">

ID of the ABAP transport request.

</td>
</tr>
<tr>
<td valign="top">

Description

</td>
<td valign="top">

Description of the ABAP transport request.

</td>
</tr>
<tr>
<td valign="top">

Owned By

</td>
<td valign="top">

The name of the ABAP user who currently owns the transport request.

</td>
</tr>
<tr>
<td valign="top">

Updated At

</td>
<td valign="top">

Date and time of the most recent change to the transport request.

</td>
</tr>
</table>



## Navigate from Transport Request to ABAP Development Tools for Eclipse

You can navigate to the open transport request in ABAP development tools for Eclipse by clicking on the transport request in the software components application table. This link opens up a popup.

Here, you can click on the *TransportRequest* button to diyplay the respective tansport request in ABAP development tools for Eclipse.

In case nothing opens up when clicking on *TransportRequest*, the following must be activated in ABAP development tools for Eclipse:

*ABAPDevelopmentTools* \> *Settings* \> *General* \> *Link Handlers* \> *enable ADT Scheme entry*. The link can then be opened.

