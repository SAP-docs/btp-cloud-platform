<!-- loio3198c2ac3a11467686920c303d14df78 -->

# Pull

**Resource path:** /sap/opu/odata/sap/MANAGE\_GIT\_REPOSITORY/Pull



<a name="loio3198c2ac3a11467686920c303d14df78__section_zps_1q4_bpb"/>

## Operations



### CRUD Operations

<a name="loio3198c2ac3a11467686920c303d14df78__table_kdm_fq4_bpb"/>


<table>
<tr>
<th>

HTTP Method



</th>
<th>

Description



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

Read pull



</td>
<td>

 



</td>
</tr>
<tr>
<td>

POST



</td>
<td>

Trigger a pull job



</td>
<td>

 



</td>
</tr>
</table>



### Custom Operations

<a name="loio3198c2ac3a11467686920c303d14df78__table_b1c_b54_bpb"/>


<table>
<tr>
<th>

HTTP Method



</th>
<th>

Description



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

GET



</td>
<td>

Associationl



</td>
<td>

 



</td>
<td>

/sap/opu/odata/sap/MANAGE\_GIT\_REPOSITORY /Pull\(guid’UUID’\)/to\_Executiong\_log



</td>
</tr>
<tr>
<td>

GET



</td>
<td>

Associationl



</td>
<td>

 



</td>
<td>

/sap/opu/odata/sap/MANAGE\_GIT\_REPOSITORY /Pull\(guid’UUID’\)/to\_Transport\_log



</td>
</tr>
</table>



### Parameters

<a name="loio3198c2ac3a11467686920c303d14df78__table_c3l_hq4_bpb"/>


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

uuid



</td>
<td>

ID of the job



</td>
</tr>
<tr>
<td>

sc\_name



</td>
<td>

Name of the software component



</td>
</tr>
<tr>
<td>

branch\_name



</td>
<td>

Name of the branch



</td>
</tr>
<tr>
<td>

commit\_id



</td>
<td>

Commit ID



</td>
</tr>
<tr>
<td>

import\_type



</td>
<td>

Type of import



</td>
</tr>
<tr>
<td>

status



</td>
<td>

Status of the job



</td>
</tr>
<tr>
<td>

status\_descr



</td>
<td>

Status description



</td>
</tr>
<tr>
<td>

user\_name



</td>
<td>

Name of the user who triggered the action



</td>
</tr>
<tr>
<td>

start\_time



</td>
<td>

Start time of the job



</td>
</tr>
<tr>
<td>

change\_time



</td>
<td>

Last update of the job



</td>
</tr>
</table>

-   **[Read Pull](Read_Pull_5de83f9.md "")**  

-   **[Create Pull](Create_Pull_c4b8a97.md "")**  


