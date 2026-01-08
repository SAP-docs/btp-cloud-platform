<!-- loio7007c618a2f74bfaba8ac6e1bb2c1ecf -->

# Serverless Limitations



<a name="loio7007c618a2f74bfaba8ac6e1bb2c1ecf__section_opb_4wd_pdc"/>

## Controller Limitations

Function Controller does not serve time-critical requests from users. It reconciles Function custom resources \(CR\), stored at the Kubernetes API Server, and has no persistent state on its own.

Function Controller doesn't serve Functions using its allocated runtime resources. It delegates this work to the dedicated Kubernetes workloads.

Having this in mind, also remember that Function Controller does not require horizontal scaling. It scales vertically up to 160 Mi of memory and 500 m of CPU time.



<a name="loio7007c618a2f74bfaba8ac6e1bb2c1ecf__section_lkr_xdq_tdc"/>

## Namespace Setup Limitations

Be aware that if you apply [LimitRanges](https://kubernetes.io/docs/concepts/policy/limit-range/) in the target namespace where you create Functions, the limits also apply to the Function workloads and may prevent Functions from being run. In such cases, ensure that resources requested in the Function configuration are lower than the limits applied in the namespace.



<a name="loio7007c618a2f74bfaba8ac6e1bb2c1ecf__section_lkx_jxd_pdc"/>

## Limitation for the Number of Functions

There is no upper limit of Functions that you can run on Kyma. Once you define a Function, its runtime Pods are always requested by Function Controller. It's up to Kubernetes to schedule them based on the available memory and CPU time on the Kubernetes worker nodes. This is determined mainly by the number of the Kubernetes worker nodes \(and the node auto-scaling capabilities\) and their computational capacity.



<a name="loio7007c618a2f74bfaba8ac6e1bb2c1ecf__section_kn2_kyd_pdc"/>

## Runtime Phase Limitations

> ### Note:  
> All measurements were taken on Kubernetes with five AWS worker nodes of type m5.xlarge \(four CPU 3.1 GHz x86\_64 cores, 16 GiB memory\).

Functions serve user-provided logic wrapped in the web framework, Express for Node.js and Bottle for Python. Taking the user logic aside, those frameworks have limitations and depend on the selected [runtime profile](https://github.com/kyma-project/serverless/blob/main/docs/user/technical-reference/07-80-available-presets.md#functions-resources) and the Kubernetes nodes specification.

The following tables present the response times of the selected runtime profiles for a "Hello World" Function requested at 50 requests/second. This describes the overhead of the serving framework itself. Any user logic added on top of that adds extra milliseconds and must be profiled separately.



### Node.js

****


<table>
<tr>
<th valign="top">

 

</th>
<th valign="top">

XL

</th>
<th valign="top">

L

</th>
<th valign="top">

M

</th>
<th valign="top">

S

</th>
<th valign="top">

XS

</th>
</tr>
<tr>
<td valign="top">

response time \[average\]

</td>
<td valign="top">

~13 ms

</td>
<td valign="top">

13 ms

</td>
<td valign="top">

~15 ms

</td>
<td valign="top">

~60 ms

</td>
<td valign="top">

~400 ms

</td>
</tr>
<tr>
<td valign="top">

response time \[95 percentile\]

</td>
<td valign="top">

~20 ms

</td>
<td valign="top">

~30 ms

</td>
<td valign="top">

~70 ms

</td>
<td valign="top">

~200 ms

</td>
<td valign="top">

~800 ms

</td>
</tr>
<tr>
<td valign="top">

response time \[99 percentile\]

</td>
<td valign="top">

~200 ms

</td>
<td valign="top">

~200 ms

</td>
<td valign="top">

~220 ms

</td>
<td valign="top">

~500 ms

</td>
<td valign="top">

~1.25 ms

</td>
</tr>
</table>



### Python

****


<table>
<tr>
<th valign="top">

 

</th>
<th valign="top">

XL

</th>
<th valign="top">

L

</th>
<th valign="top">

M

</th>
<th valign="top">

S

</th>
</tr>
<tr>
<td valign="top">

response time \[average\]

</td>
<td valign="top">

~11 ms

</td>
<td valign="top">

12 ms

</td>
<td valign="top">

~12 ms

</td>
<td valign="top">

~14 ms

</td>
</tr>
<tr>
<td valign="top">

response time \[95 percentile\]

</td>
<td valign="top">

~25 ms

</td>
<td valign="top">

~25 ms

</td>
<td valign="top">

~25 ms

</td>
<td valign="top">

~25 ms

</td>
</tr>
<tr>
<td valign="top">

response time \[99 percentile\]

</td>
<td valign="top">

~175 ms

</td>
<td valign="top">

~180 ms

</td>
<td valign="top">

~210 ms

</td>
<td valign="top">

~280 ms

</td>
</tr>
</table>

The bigger the runtime profile, the more resources are available to serve the response quicker. Consider these limits of the serving layer as a baseline because this does not take your Function logic into account.



### Scaling

Function runtime Pods can be scaled horizontally from zero up to the limits of the available resources at the Kubernetes worker nodes. See the [Use External Scalers](https://kyma-project.io/#/serverless/user/tutorials/01-130-use-external-scalers) tutorial for more information.

