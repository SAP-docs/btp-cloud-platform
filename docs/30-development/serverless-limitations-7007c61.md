<!-- loio7007c618a2f74bfaba8ac6e1bb2c1ecf -->

# Serverless Limitations



<a name="loio7007c618a2f74bfaba8ac6e1bb2c1ecf__section_opb_4wd_pdc"/>

## Controller Limitations

Function Controller does not serve time-critical requests from users. It reconciles Function custom resources \(CRs\) stored at the Kubernetes API Server, and has no persistent state on its own.

Function Controller doesn't serve Functions using its allocated runtime resources. It delegates this work to the dedicated Kubernetes workloads. Refer to the [architecture](https://kyma-project.io/external-content/serverless/docs/user/technical-reference/04-10-architecture.html) diagram for more details.

Having this in mind, also remember that Function Controller does not require horizontal scaling. It scales vertically up to `1Gi` of memory and `500m` of CPU time.



<a name="loio7007c618a2f74bfaba8ac6e1bb2c1ecf__section_lkr_xdq_tdc"/>

## Namespace Setup Limitations

Be aware that if you apply [LimitRanges](https://kubernetes.io/docs/concepts/policy/limit-range/) in the target namespace where you create Functions, the limits also apply to the Function workloads and may prevent Functions from being run. In such cases, ensure that resources requested in the Function configuration are lower than the limits applied in the namespace.



<a name="loio7007c618a2f74bfaba8ac6e1bb2c1ecf__section_lkx_jxd_pdc"/>

## Limitation for the Number of Functions

There is no upper limit of Functions that you can run on Kyma. Once you define a Function, its runtime Pods are always requested by Function Controller. It's up to Kubernetes to schedule them based on the available memory and CPU time on the Kubernetes worker nodes. This is determined mainly by the number of the Kubernetes worker nodes \(and the node auto-scaling capabilities\) and their computational capacity.



<a name="loio7007c618a2f74bfaba8ac6e1bb2c1ecf__section_kn2_kyd_pdc"/>

## Runtime Phase Limitations

> ### Note:  
> All measurements were taken on Kubernetes with three Azure worker nodes of type Standard\_D2s\_v5 \(two vCPU amd64 cores, ~8 GiB memory\), distributed across availability zones westeurope-1, westeurope-2, and westeurope-3, running Garden Linux 1877.10 with kernel `6.12.66-cloud-amd64` and Kubernetes `v1.34.3`.
> 
> The values in the following tables are averages from three test runs. Last updated: 2026-04-02.

Functions serve user-provided logic wrapped in the web framework, Express for Node.js and Bottle for Python. Taking the user logic aside, those frameworks have limitations and depend on the selected [runtime profile](https://github.com/kyma-project/serverless/blob/main/docs/user/technical-reference/07-80-available-presets.md#functions-resources) and the Kubernetes nodes specification.

The following tables present the response times of the selected runtime profiles for a "Hello World" Function across three load scenarios. This describes the overhead of the serving framework itself. Any user logic added on top of that adds extra milliseconds and must be profiled separately.

Tests are implemented using [k6](https://k6.io/) and consist of the following scenarios:

-   **Constant load** — 50 virtual users send one request per second each \(with a 1-second sleep between calls\) for 2 minutes. Represents a steady, moderate traffic baseline.

-   **Max load** — 100 virtual users send requests as fast as possible \(no sleep\) for 2 minutes. Represents sustained high concurrency.




### Constant Load

**Node.js 22**


<table>
<tr>
<th valign="top">

response time \[ms\]

</th>
<th valign="top">

XS

</th>
<th valign="top">

S

</th>
<th valign="top">

M

</th>
<th valign="top">

L

</th>
<th valign="top">

XL

</th>
</tr>
<tr>
<td valign="top">

median

</td>
<td valign="top">

1.7

</td>
<td valign="top">

1.4

</td>
<td valign="top">

1.3

</td>
<td valign="top">

0.9

</td>
<td valign="top">

1.2

</td>
</tr>
<tr>
<td valign="top">

95 percentile

</td>
<td valign="top">

4.9

</td>
<td valign="top">

4.4

</td>
<td valign="top">

4.4

</td>
<td valign="top">

3.7

</td>
<td valign="top">

4.8

</td>
</tr>
<tr>
<td valign="top">

99 percentile

</td>
<td valign="top">

93

</td>
<td valign="top">

61

</td>
<td valign="top">

22

</td>
<td valign="top">

12

</td>
<td valign="top">

12

</td>
</tr>
</table>

**Node.js 24**


<table>
<tr>
<th valign="top">

response time \[ms\]

</th>
<th valign="top">

XS

</th>
<th valign="top">

S

</th>
<th valign="top">

M

</th>
<th valign="top">

L

</th>
<th valign="top">

XL

</th>
</tr>
<tr>
<td valign="top">

median

</td>
<td valign="top">

1.5

</td>
<td valign="top">

1.6

</td>
<td valign="top">

1.3

</td>
<td valign="top">

1.3

</td>
<td valign="top">

1.8

</td>
</tr>
<tr>
<td valign="top">

95 percentile

</td>
<td valign="top">

3.7

</td>
<td valign="top">

4.1

</td>
<td valign="top">

3.4

</td>
<td valign="top">

3.2

</td>
<td valign="top">

4.1

</td>
</tr>
<tr>
<td valign="top">

99 percentile

</td>
<td valign="top">

13

</td>
<td valign="top">

12

</td>
<td valign="top">

7.2

</td>
<td valign="top">

5.4

</td>
<td valign="top">

7.7

</td>
</tr>
</table>

**Python 3.12**


<table>
<tr>
<th valign="top">

response time \[ms\]

</th>
<th valign="top">

XS

</th>
<th valign="top">

S

</th>
<th valign="top">

M

</th>
<th valign="top">

L

</th>
<th valign="top">

XL

</th>
</tr>
<tr>
<td valign="top">

median

</td>
<td valign="top">

2.5

</td>
<td valign="top">

2.4

</td>
<td valign="top">

3.7

</td>
<td valign="top">

3.4

</td>
<td valign="top">

3.7

</td>
</tr>
<tr>
<td valign="top">

95 percentile

</td>
<td valign="top">

16

</td>
<td valign="top">

7.6

</td>
<td valign="top">

9.8

</td>
<td valign="top">

9.2

</td>
<td valign="top">

9.4

</td>
</tr>
<tr>
<td valign="top">

99 percentile

</td>
<td valign="top">

147

</td>
<td valign="top">

47

</td>
<td valign="top">

21

</td>
<td valign="top">

30

</td>
<td valign="top">

20

</td>
</tr>
</table>



### Max Load

**Node.js 22**


<table>
<tr>
<th valign="top">

response time \[ms\]

</th>
<th valign="top">

XS

</th>
<th valign="top">

S

</th>
<th valign="top">

M

</th>
<th valign="top">

L

</th>
<th valign="top">

XL

</th>
</tr>
<tr>
<td valign="top">

median

</td>
<td valign="top">

104

</td>
<td valign="top">

97

</td>
<td valign="top">

50

</td>
<td valign="top">

18

</td>
<td valign="top">

15

</td>
</tr>
<tr>
<td valign="top">

95 percentile

</td>
<td valign="top">

300

</td>
<td valign="top">

204

</td>
<td valign="top">

104

</td>
<td valign="top">

57

</td>
<td valign="top">

28

</td>
</tr>
<tr>
<td valign="top">

99 percentile

</td>
<td valign="top">

390

</td>
<td valign="top">

293

</td>
<td valign="top">

156

</td>
<td valign="top">

69

</td>
<td valign="top">

40

</td>
</tr>
</table>

**Node.js 24**


<table>
<tr>
<th valign="top">

response time \[ms\]

</th>
<th valign="top">

XS

</th>
<th valign="top">

S

</th>
<th valign="top">

M

</th>
<th valign="top">

L

</th>
<th valign="top">

XL

</th>
</tr>
<tr>
<td valign="top">

median

</td>
<td valign="top">

86

</td>
<td valign="top">

12

</td>
<td valign="top">

8.2

</td>
<td valign="top">

6.8

</td>
<td valign="top">

6.3

</td>
</tr>
<tr>
<td valign="top">

95 percentile

</td>
<td valign="top">

100

</td>
<td valign="top">

93

</td>
<td valign="top">

65

</td>
<td valign="top">

23

</td>
<td valign="top">

17

</td>
</tr>
<tr>
<td valign="top">

99 percentile

</td>
<td valign="top">

191

</td>
<td valign="top">

102

</td>
<td valign="top">

73

</td>
<td valign="top">

31

</td>
<td valign="top">

27

</td>
</tr>
</table>

**Python 3.12**


<table>
<tr>
<th valign="top">

response time \[ms\]

</th>
<th valign="top">

XS

</th>
<th valign="top">

S

</th>
<th valign="top">

M

</th>
<th valign="top">

L

</th>
<th valign="top">

XL

</th>
</tr>
<tr>
<td valign="top">

median

</td>
<td valign="top">

902

</td>
<td valign="top">

699

</td>
<td valign="top">

384

</td>
<td valign="top">

137

</td>
<td valign="top">

119

</td>
</tr>
<tr>
<td valign="top">

95 percentile

</td>
<td valign="top">

1157

</td>
<td valign="top">

846

</td>
<td valign="top">

397

</td>
<td valign="top">

213

</td>
<td valign="top">

163

</td>
</tr>
<tr>
<td valign="top">

99 percentile

</td>
<td valign="top">

1540

</td>
<td valign="top">

1100

</td>
<td valign="top">

585

</td>
<td valign="top">

300

</td>
<td valign="top">

228

</td>
</tr>
</table>

The bigger the runtime profile, the more resources are available to serve the response quicker. Consider these limits of the serving layer as a baseline because this does not take your Function logic into account.



### Scaling

Function runtime Pods can be scaled horizontally from zero up to the limits of the available resources at the Kubernetes worker nodes. See the [Use External Scalers](https://kyma-project.io/#/serverless/user/tutorials/01-130-use-external-scalers) tutorial for more information.

