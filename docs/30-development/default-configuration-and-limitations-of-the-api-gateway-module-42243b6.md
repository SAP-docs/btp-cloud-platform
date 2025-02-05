<!-- loio42243b6fd8cf4bd7b78249866f09f6a8 -->

# Default Configuration and Limitations of the API Gateway Module



## APIRule Controller Limitations

APIRule Controller relies on Istio and Ory custom resources \(CRs\) to provide routing capabilities. In terms of persistence, the controller depends only on APIRules stored in the Kubernetes cluster. In terms of the resource configuration, the following requirements are set on APIGateway Controller:

-   CPU Requests: 10 m
-   CPU Limits: 100 m
-   Memory Requests: 64 Mi
-   Memory Limits: 128 Mi

You can create an unlimited number of APIRule CRs.



<a name="loio42243b6fd8cf4bd7b78249866f09f6a8__section_jmf_crn_xdc"/>

## Ory Resources' Configuration

The configuration of Ory resources depends on the cluster capabilities. If your cluster has fewer than 5 total virtual CPU cores or its total memory capacity is less than 10 gigabytes, the default setup for resources is lighter. If your cluster exceeds both of these thresholds, the higher resource configuration is applied.

The default configuration for larger clusters includes the following settings for the Ory components’ resources:

**Ory Resources' Configuration**


<table>
<tr>
<th valign="top">

Component

</th>
<th valign="top">

CPU Requests

</th>
<th valign="top">

CPU Limits

</th>
<th valign="top">

Memory Requests

</th>
<th valign="top">

Memory Limits

</th>
</tr>
<tr>
<td valign="top">

Oathkeeper

</td>
<td valign="top">

100 m

</td>
<td valign="top">

10000 m

</td>
<td valign="top">

64 Mi

</td>
<td valign="top">

512 Mi

</td>
</tr>
<tr>
<td valign="top">

Oathkeeper Maester

</td>
<td valign="top">

10 m

</td>
<td valign="top">

400 m

</td>
<td valign="top">

32 Mi

</td>
<td valign="top">

1 Gi

</td>
</tr>
</table>

The default configuration for smaller clusters includes the following settings for the Ory components’ resources:

**Ory Resources' Configuration**


<table>
<tr>
<th valign="top">

Component

</th>
<th valign="top">

CPU Requests

</th>
<th valign="top">

CPU Limits

</th>
<th valign="top">

Memory Requests

</th>
<th valign="top">

Memory Limits

</th>
</tr>
<tr>
<td valign="top">

Oathkeeper

</td>
<td valign="top">

10 m

</td>
<td valign="top">

100 m

</td>
<td valign="top">

64 Mi

</td>
<td valign="top">

128 Mi

</td>
</tr>
<tr>
<td valign="top">

Oathkeeper Maester

</td>
<td valign="top">

10 m

</td>
<td valign="top">

100 m

</td>
<td valign="top">

20 Mi

</td>
<td valign="top">

50 Mi

</td>
</tr>
</table>



<a name="loio42243b6fd8cf4bd7b78249866f09f6a8__section_fcf_4rn_xdc"/>

## Autoscaling Configuration

The default configuration in terms of autoscaling of Ory components is as follows:

**Ory Resources' Configuration**


<table>
<tr>
<th valign="top">

Component

</th>
<th valign="top">

Min Replicas

</th>
<th valign="top">

Max Replicas

</th>
</tr>
<tr>
<td valign="top">

Oathkeeper

</td>
<td valign="top">

3

</td>
<td valign="top">

10

</td>
</tr>
<tr>
<td valign="top">

Oathkeeper Maester

</td>
<td valign="top">

3

</td>
<td valign="top">

10

</td>
</tr>
</table>

Oathkeeper Maester is a separate container running in the same Pod as Oathkeeper. Because of that, the autoscaling configuration of the Oathkeeper and Oathkeeper Master components is similar. The autoscaling configuration is based on CPU utilization, with HorizontalPodAutoscaler set up for 80% average CPU request utilization.

