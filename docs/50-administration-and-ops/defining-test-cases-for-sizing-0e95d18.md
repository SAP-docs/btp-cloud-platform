<!-- loio0e95d189e6454141bc184d03674e752e -->

# Defining Test Cases for Sizing

After you've identified the sizing-relevant business processes, define test cases for each business process for baseline measurements.

It's important that these test cases are self-contained and idempotent, which means they're repeatable and return the same resource requirements after each repetition. Such a careful design of test cases is important to avoid side effects because, for example, data volume processed by SAP HANA increases during query execution \(empty table versus table with high volume of irrelevant data\).

Furthermore, make sure that each test case is limited to a single business process. For example, split the creation and the approval of a travel request into two test cases because creation and approval are performed by different users and at different points in time.



<a name="loio0e95d189e6454141bc184d03674e752e__section_typ_ztt_tqb"/>

## Example

A test case description for the business process *Creating a new travel request* can look as follows:

<a name="loio0e95d189e6454141bc184d03674e752e__table_xng_vxt_tqb"/>Test Case Example: Travel Request


<table>
<tr>
<th valign="top">

Step ID



</th>
<th valign="top">

Description



</th>
<th valign="top">

Input Fields



</th>
<th valign="top">

Input Values



</th>
</tr>
<tr>
<td valign="top" colspan="4">

**Preparation Steps \(Not Measured\)**



</td>
</tr>
<tr>
<td valign="top">

SystemLogon



</td>
<td valign="top">

Link to SAP Fiori launchpad



</td>
<td valign="top">

User

Password



</td>
<td valign="top">

*<tester name\>*, *<tester password\>*



</td>
</tr>
<tr>
<td valign="top" colspan="4">

**Test Case \(Measured\)**



</td>
</tr>
<tr>
<td valign="top">

OpenApp



</td>
<td valign="top">

Open the travel management app from the launchpad \(or using the Fiori Elements preview\).



</td>
<td valign="top">

\--



</td>
<td valign="top">

\--



</td>
</tr>
<tr>
<td valign="top">

CreateTravel\_1a



</td>
<td valign="top">

Choose *Create* from the table toolbar of the travel overview.



</td>
<td valign="top">

\--



</td>
<td valign="top">

\--



</td>
</tr>
<tr>
<td valign="top">

CreateTravel\_1b



</td>
<td valign="top">

1.  Open the search help of field *Customer ID*.

2.  Choose *Go* without entering any search data.

3.  Select an arbitrary entry from the persons listed.




</td>
<td valign="top">

Customer ID



</td>
<td valign="top">

*<arbitrary, using search help\>*



</td>
</tr>
<tr>
<td valign="top">

CreateTravel\_1c



</td>
<td valign="top">

1.  Open the search help of field *Agency ID*.

2.  Choose *Go* without entering any search data.

3.  Select an arbitrary entry from the agencies listed.




</td>
<td valign="top">

Agency ID



</td>
<td valign="top">

*<arbitrary, using search help\>*



</td>
</tr>
<tr>
<td valign="top">

CreateTravel\_1d



</td>
<td valign="top">

1.  Open the search help of the currency field next to *Total Price*.

2.  In the *Currency* field, enter ***EUR*** and choose *Go*.

3.  Select *EUR*.




</td>
<td valign="top">

Currency



</td>
<td valign="top">

EUR



</td>
</tr>
<tr>
<td valign="top">

CreateTravel\_1e



</td>
<td valign="top">

Enter the remaining input and choose *Save*.



</td>
<td valign="top">

Starting date

End date

Total price

Booking fee

Status

Description



</td>
<td valign="top">

*<arbitrary\>*

*<arbitrary\>*

0

9.99

O

*<optional\>*



</td>
</tr>
<tr>
<td valign="top" colspan="4">

**Cleanup Steps \(Not Measured\)**



</td>
</tr>
<tr>
<td valign="top">

DeleteTravel



</td>
<td valign="top">

Delete the created travel from either the travel overview or the travel details.



</td>
<td valign="top">

\--



</td>
<td valign="top">

\--



</td>
</tr>
</table>

