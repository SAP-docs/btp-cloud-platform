<!-- loio0f9bb43ce217414f882f0fadd4516376 -->

# Function Runtime Deprecation Schedule

This document outlines the planned deprecation and end-of-life \(EOL\) dates for supported Function runtimes in Kyma Serverless.



<a name="loio0f9bb43ce217414f882f0fadd4516376__section_supported_runtimes"/>

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
<th valign="top">

Status

</th>
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
<td valign="top">

Deprecated

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
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Node.js 26

</td>
<td valign="top">

TBD

</td>
<td valign="top">

TBD

</td>
<td valign="top">

 

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
<td valign="top">

 

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
<td valign="top">

 

</td>
</tr>
</table>



<a name="loio0f9bb43ce217414f882f0fadd4516376__section_deprecation_history"/>

## Deprecation History


<dl>
<dt><b>

Node.js 22

</b></dt>
<dd>

`Status`: Deprecated

`Deprecation Version`: `v1.14.0`

Node.js 22 is deprecated. For more information, see [\#2681](https://github.com/kyma-project/serverless/issues/2681). Migrate to Node.js 24 or newer.



</dd><dt><b>

Node.js 20

</b></dt>
<dd>

`Status`: Removed

`Deprecation Version`: `v1.10.0`

`Removal Version`: `v1.14.0`

Node.js 20 reached end-of-life. For more information, see [\#2231](https://github.com/kyma-project/serverless/issues/2231) and [\#2682](https://github.com/kyma-project/serverless/issues/2682). Migrate to Node.js 22 or newer.



</dd>
</dl>

> ### Note:  
> The deprecation and EOL dates listed in this document are predictions based on current release cadence and Node.js/Python LTS schedules. These dates are subject to change and may be adjusted based on the following:
> 
> -   Changes in the Kyma Serverless release schedule
> -   Updates to upstream Node.js and Python LTS timelines
> -   Community feedback and requirements
> -   Security considerations
> 
> Always check the [release notes](https://github.com/kyma-project/serverless/releases) for announcements regarding runtime deprecations and EOL timelines.



<a name="loio0f9bb43ce217414f882f0fadd4516376__section_recommendations"/>

## Recommendations

-   Plan upgrades to newer runtimes well in advance of deprecation dates.
-   Monitor release notes for any changes to this schedule.
-   For Functions using deprecated runtimes, migrate before the EOL date to avoid service disruption.

