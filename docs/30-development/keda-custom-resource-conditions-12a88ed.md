<!-- loio12a88ed593044bc588783c4c7dc4afa2 -->

# Keda Custom Resource Conditions

This document describes the possible states of the Keda CR.

The following condition types are used:

-   `Installed`

-   `Deleted`


****


<table>
<tr>
<th valign="top">

No

</th>
<th valign="top">

CR State

</th>
<th valign="top">

Condition Type

</th>
<th valign="top">

Condition Status

</th>
<th valign="top">

Condition Reason

</th>
<th valign="top">

Remarks

</th>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

Ready

</td>
<td valign="top">

Installed

</td>
<td valign="top">

true

</td>
<td valign="top">

Verified

</td>
<td valign="top">

Server ready

</td>
</tr>
<tr>
<td valign="top">

2

</td>
<td valign="top">

Processing

</td>
<td valign="top">

Installed

</td>
<td valign="top">

unknown

</td>
<td valign="top">

Initialized

</td>
<td valign="top">

Initialized

</td>
</tr>
<tr>
<td valign="top">

3

</td>
<td valign="top">

Processing

</td>
<td valign="top">

Installed

</td>
<td valign="top">

unknown

</td>
<td valign="top">

Verification

</td>
<td valign="top">

Verification in progress

</td>
</tr>
<tr>
<td valign="top">

4

</td>
<td valign="top">

Error

</td>
<td valign="top">

Installed

</td>
<td valign="top">

false

</td>
<td valign="top">

ApplyObjError

</td>
<td valign="top">

Apply object error

</td>
</tr>
<tr>
<td valign="top">

5

</td>
<td valign="top">

Error

</td>
<td valign="top">

Installed

</td>
<td valign="top">

false

</td>
<td valign="top">

DeploymentUpdateErr

</td>
<td valign="top">

Deployment update error

</td>
</tr>
<tr>
<td valign="top">

6

</td>
<td valign="top">

Error

</td>
<td valign="top">

Installed

</td>
<td valign="top">

false

</td>
<td valign="top">

VerificationErr

</td>
<td valign="top">

Verification error

</td>
</tr>
<tr>
<td valign="top">

7

</td>
<td valign="top">

Error

</td>
<td valign="top">

Installed

</td>
<td valign="top">

false

</td>
<td valign="top">

KedaDuplicated

</td>
<td valign="top">

One instance of Keda is allowed

</td>
</tr>
<tr>
<td valign="top">

8

</td>
<td valign="top">

Deleting

</td>
<td valign="top">

Deleted

</td>
<td valign="top">

unknown

</td>
<td valign="top">

Deletion

</td>
<td valign="top">

Deletion in progress

</td>
</tr>
<tr>
<td valign="top">

9

</td>
<td valign="top">

Deleting

</td>
<td valign="top">

Deleted

</td>
<td valign="top">

true

</td>
<td valign="top">

Deleted

</td>
<td valign="top">

Keda module deleted

</td>
</tr>
<tr>
<td valign="top">

10

</td>
<td valign="top">

Error

</td>
<td valign="top">

Deleted

</td>
<td valign="top">

false

</td>
<td valign="top">

DeletionErr

</td>
<td valign="top">

Deletion failed

</td>
</tr>
</table>

