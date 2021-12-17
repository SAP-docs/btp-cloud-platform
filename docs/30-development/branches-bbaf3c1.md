<!-- loiobbaf3c1d6d414c788d9410f0e9ee4cc2 -->

# Branches

**Resource path:** /sap/opu/odata/sap/MANAGE\_GIT\_REPOSITORY/Branches



<a name="loiobbaf3c1d6d414c788d9410f0e9ee4cc2__section_zps_1q4_bpb"/>

## Operations



### CRUD Operations

<a name="loiobbaf3c1d6d414c788d9410f0e9ee4cc2__table_kdm_fq4_bpb"/>


<table>
<tr>
<th valign="top">

HTTP Method



</th>
<th valign="top">

Operation



</th>
</tr>
<tr>
<td valign="top">

GET



</td>
<td valign="top">

[Read Branches](read-branches-e8e40c2.md)



</td>
</tr>
<tr>
<td valign="top">

POST



</td>
<td valign="top">

[Create Branch](create-branch-a9ce22e.md)



</td>
</tr>
<tr>
<td valign="top">

DELETE



</td>
<td valign="top">

[Delete Branches](delete-branches-425717b.md)



</td>
</tr>
</table>



### Custom Operations

<a name="loiobbaf3c1d6d414c788d9410f0e9ee4cc2__table_b1c_b54_bpb"/>


<table>
<tr>
<th valign="top">

HTTP Method



</th>
<th valign="top">

Operation Type



</th>
<th valign="top">

Operation



</th>
<th valign="top">

URI



</th>
</tr>
<tr>
<td valign="top">

POST



</td>
<td valign="top">

Action



</td>
<td valign="top">

[Checkout Branches](checkout-branches-069b979.md)



</td>
<td valign="top">

/sap/opu/odata/sap/MANAGE\_GIT\_REPOSITORY/checkout\_branch



</td>
</tr>
</table>



### Parameters

<a name="loiobbaf3c1d6d414c788d9410f0e9ee4cc2__table_c3l_hq4_bpb"/>


<table>
<tr>
<th valign="top">

Property



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

branch\_name



</td>
<td valign="top">

name of the branch



</td>
</tr>
<tr>
<td valign="top">

sc\_name



</td>
<td valign="top">

name of the software component



</td>
</tr>
<tr>
<td valign="top">

is\_active



</td>
<td valign="top">

indicates if the branch is active in the system



</td>
</tr>
<tr>
<td valign="top">

critivality



</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

derived\_from



</td>
<td valign="top">

name of the original branch from which the branch was derived



</td>
</tr>
<tr>
<td valign="top">

created\_by



</td>
<td valign="top">

user who created the branch



</td>
</tr>
<tr>
<td valign="top">

created\_on



</td>
<td valign="top">

date when the branch was created



</td>
</tr>
<tr>
<td valign="top">

commit\_id



</td>
<td valign="top">

latest commit ID on the branch



</td>
</tr>
<tr>
<td valign="top">

commit\_message



</td>
<td valign="top">

commit message of the latest commit



</td>
</tr>
<tr>
<td valign="top">

last\_commit\_by



</td>
<td valign="top">

user who commited the last commit



</td>
</tr>
<tr>
<td valign="top">

last\_commit\_on



</td>
<td valign="top">

date of the latest commit



</td>
</tr>
</table>

