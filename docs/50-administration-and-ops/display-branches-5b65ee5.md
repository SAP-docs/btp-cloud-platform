<!-- loio5b65ee5af8d041a0949bafaa25e01571 -->

# Display Branches





### Context

You want to view all branches of a software component, including both remote and local branches, regardless of the currently active branch. To display the list of branches, follow these steps:



### Procedure

1.  Open the **Manage Software Components** Fiori app.
2.  Select the software component you are interested in.
3.  Scroll down to the section **Branching** to display the table.



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

Branch

</td>
<td valign="top">

Name of the branch. The **main** branch is created by default.

</td>
</tr>
<tr>
<td valign="top">

Checked Out

</td>
<td valign="top">

Shows if the branch is currently active in the system. Only one branch of a software component can be active \(checked out\) in a system instance. Is either **Yes** or **No**.

</td>
</tr>
<tr>
<td valign="top">

Delta

</td>
<td valign="top">

This column indicates whether the currently active local branch is in sync with the remote repository. If it is up to date, it will display **No new commits**. If there are new commits, it will show a message similar to **2 commits behind**. To retrieve the latest changes from the remote repository, you can carry out a pull action. Please note that a pull includes all commits that occurred before the specified commit; there is no option for cherry-picking or skipping commits.

</td>
</tr>
<tr>
<td valign="top">

Last Remote Commit ID

</td>
<td valign="top">

The commit ID of the most recent commit on the branch of the remote repository.

</td>
</tr>
<tr>
<td valign="top">

Last Remote Commit Message

</td>
<td valign="top">

The commit message of the most recent commit on the branch of the remote repository.

</td>
</tr>
<tr>
<td valign="top">

Last Remote Commit

</td>
<td valign="top">

Relative date and time of the most recent commit pushed to the remote repository on this branch.

</td>
</tr>
<tr>
<td valign="top">

Last CommitON

</td>
<td valign="top">

Date and time of the most recent commit pushed to the remote repository on this branch.

</td>
</tr>
<tr>
<td valign="top">

Local Short Commit ID

</td>
<td valign="top">

The currently checked-out commit ID in short format.

</td>
</tr>
<tr>
<td valign="top">

Created By

</td>
<td valign="top">

Name of the user who created this branch. Note that this information is only available for SAP managed repositories and not for customer-managed repositories.

</td>
</tr>
<tr>
<td valign="top">

Created On

</td>
<td valign="top">

Date and time when this branch was created. Note that this information is only available for SAP managed repositories and not for customer-managed repositories.

</td>
</tr>
</table>

