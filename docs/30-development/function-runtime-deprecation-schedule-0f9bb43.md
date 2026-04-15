<!-- loio0f9bb43ce217414f882f0fadd4516376 -->

# Function Runtime Deprecation Schedule

Learn about the planned deprecation and end-of-life \(EOL\) dates for the supported Function runtimes in Kyma Serverless.



## Supported Runtimes and Deprecation Timeline


<table>
<tr>
<th valign="top">

Runtime

</th>
<th valign="top">

Planned Deprecation

</th>
<th valign="top">

Estimated EOL

</th>
</tr>
<tr>
<td valign="top">

Node.js 20

</td>
<td valign="top">

February 2026

</td>
<td valign="top">

April 2026

</td>
</tr>
<tr>
<td valign="top">

Node.js 22

</td>
<td valign="top">

July 2026

</td>
<td valign="top">

November 2026

</td>
</tr>
<tr>
<td valign="top">

Node.js 24

</td>
<td valign="top">

TBD

</td>
<td valign="top">

TBD

</td>
</tr>
<tr>
<td valign="top">

Python 3.12

</td>
<td valign="top">

September 2026

</td>
<td valign="top">

March 2027

</td>
</tr>
<tr>
<td valign="top">

Python 3.14

</td>
<td valign="top">

TBD

</td>
<td valign="top">

TBD

</td>
</tr>
</table>



## Deprecation History



### Node.js 20

-   **Status**: deprecated
-   **Deprecation version**: v1.10.0
-   **Details**: Node.js 20 runtime was deprecated starting with version 1.10.0. For more information, see [this issue](https://github.com/kyma-project/serverless/issues/2231).

> ### Note:  
> The deprecation and EOL dates listed in this document are **predictions based on current release cadence and Node.js/Python LTS schedules**. These dates are subject to change and may be adjusted based on the following:
> 
> -   Changes in the Kyma Serverless release schedule
> -   Updates to upstream Node.js and Python LTS timelines
> -   Community feedback and requirements
> -   Security considerations
> 
> Always check the [What's New notes](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?locale=en-US&clear=all&Valid_as_Of=2022-01-01:2028-12-31&q=serverless) for announcements regarding runtime deprecations and EOL timelines.



## Recommendations

To ensure uninterrupted service, consider the following best practices:

-   Plan upgrades to newer runtimes well in advance of deprecation dates.
-   Monitor the What's New notes for any changes to this schedule.
-   For Functions using deprecated runtimes, migrate before the EOL date.

