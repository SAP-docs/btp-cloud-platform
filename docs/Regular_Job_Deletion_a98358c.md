<!-- loioa98358cf3085452fa79abf13bd7a86f1 -->

# Regular Job Deletion

Get an overview of the regular job deletion



All jobs that are not removed by a user remain in the system until a technical cleaning job runs. The time when this job is run by the system depends on the periodic granularity of the jobs that should be deleted. Currently, the following timeframes apply:

<a name="loioa98358cf3085452fa79abf13bd7a86f1__table_qnb_sk1_ww"/>Regular Job Deletion


<table>
<tr>
<th>

Periodic Granularity of the Job to Be Deleted



</th>
<th>

Job is Automatically Deleted After



</th>
</tr>
<tr>
<td>

Not periodic



</td>
<td>

14 days



</td>
</tr>
<tr>
<td>

Minutes



</td>
<td>

7 days



</td>
</tr>
<tr>
<td>

Hours



</td>
<td>

14 days



</td>
</tr>
<tr>
<td>

Days



</td>
<td>

Periodic value\*24 days



</td>
</tr>
<tr>
<td>

Weeks



</td>
<td>

Periodic value\*7\*24 days



</td>
</tr>
<tr>
<td>

Months



</td>
<td>

Periodic value\*31\*24 days



</td>
</tr>
<tr>
<td>

Every X week in every Y month



</td>
<td>

Periodic value\*31\*24 days



</td>
</tr>
</table>



You have scheduled a job that runs every two weeks and ends after 20 runs. The first run starts in the calendar week 2 and ends in the calendar week 40. Each job run stays in the system for the certain retention time. Retention period is always set to 24 runs. Retention time=periodic value \* retention periods \* weekdays \[days\] = 2 \* 24 \*7 \[days\] = 336 \[days\] = 48 \[weeks\]. The first job run will be deleted a day after 48 weeks since this job run took place.

> ### Note:  
> This is the default behaviour. If the application chooses to have different schemes, this is documented in the application-specific documentation.

