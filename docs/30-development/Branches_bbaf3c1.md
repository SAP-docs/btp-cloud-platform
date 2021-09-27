<!-- loiobbaf3c1d6d414c788d9410f0e9ee4cc2 -->

# Branches

**Resource path:** /sap/opu/odata/sap/MANAGE\_GIT\_REPOSITORY/Branches



<a name="loiobbaf3c1d6d414c788d9410f0e9ee4cc2__section_zps_1q4_bpb"/>

## Operations



### CRUD Operations

<a name="loiobbaf3c1d6d414c788d9410f0e9ee4cc2__table_kdm_fq4_bpb"/>


<table>
<tr>
<th>

HTTP Method



</th>
<th>

Operation



</th>
</tr>
<tr>
<td>

GET



</td>
<td>

[Read Branches](Read_Branches_e8e40c2.md)



</td>
</tr>
<tr>
<td>

POST



</td>
<td>

[Create Branch](Create_Branch_a9ce22e.md)



</td>
</tr>
<tr>
<td>

DELETE



</td>
<td>

[Delete Branches](Delete_Branches_425717b.md)



</td>
</tr>
</table>



### Custom Operations

<a name="loiobbaf3c1d6d414c788d9410f0e9ee4cc2__table_b1c_b54_bpb"/>


<table>
<tr>
<th>

HTTP Method



</th>
<th>

Operation Type



</th>
<th>

Operation



</th>
<th>

URI



</th>
</tr>
<tr>
<td>

POST



</td>
<td>

Action



</td>
<td>

[Checkout Branches](Checkout_Branches_069b979.md)



</td>
<td>

/sap/opu/odata/sap/MANAGE\_GIT\_REPOSITORY/checkout\_branch



</td>
</tr>
</table>



### Parameters

<a name="loiobbaf3c1d6d414c788d9410f0e9ee4cc2__table_c3l_hq4_bpb"/>


<table>
<tr>
<th>

Property



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

branch\_name



</td>
<td>

name of the branch



</td>
</tr>
<tr>
<td>

sc\_name



</td>
<td>

name of the software component



</td>
</tr>
<tr>
<td>

is\_active



</td>
<td>

indicates if the branch is active in the system



</td>
</tr>
<tr>
<td>

critivality



</td>
<td>



</td>
</tr>
<tr>
<td>

derived\_from



</td>
<td>

name of the original branch from which the branch was derived



</td>
</tr>
<tr>
<td>

created\_by



</td>
<td>

user who created the branch



</td>
</tr>
<tr>
<td>

created\_on



</td>
<td>

date when the branch was created



</td>
</tr>
<tr>
<td>

commit\_id



</td>
<td>

latest commit ID on the branch



</td>
</tr>
<tr>
<td>

commit\_message



</td>
<td>

commit message of the latest commit



</td>
</tr>
<tr>
<td>

last\_commit\_by



</td>
<td>

user who commited the last commit



</td>
</tr>
<tr>
<td>

last\_commit\_on



</td>
<td>

date of the latest commit



</td>
</tr>
</table>

-   **[Read Branches](Read_Branches_e8e40c2.md "")**  

-   **[Create Branch](Create_Branch_a9ce22e.md "")**  

-   **[Delete Branches](Delete_Branches_425717b.md "")**  

-   **[Checkout Branches](Checkout_Branches_069b979.md "")**  


