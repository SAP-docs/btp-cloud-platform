<!-- loio7007c618a2f74bfaba8ac6e1bb2c1ecf -->

# Serverless Limitations



<a name="loio7007c618a2f74bfaba8ac6e1bb2c1ecf__section_opb_4wd_pdc"/>

## Controller Limitations

Function Controller does not serve time-critical requests from users. It reconciles Function custom resources \(CR\), stored at the Kubernetes API Server, and has no persistent state on its own.

Function Controller doesn't build or serve Functions using its allocated runtime resources. It delegates this work to the dedicated Kubernetes workloads. It schedules \(build-time\) jobs to build the Function Docker image and runtime Pods to serve them once the image is built.

Having this in mind, also remember that Function Controller does not require horizontal scaling. It scales vertically up to 160 Mi of memory and 500 m of CPU time.



<a name="loio7007c618a2f74bfaba8ac6e1bb2c1ecf__section_lkr_xdq_tdc"/>

## Namespace Setup Limitations

Be aware that if you apply [LimitRanges](https://kubernetes.io/docs/concepts/policy/limit-range/) in the target namespace where you create Functions, the limits also apply to the Function workloads and may prevent Functions from being built and run. In such cases, ensure that resources requested in the Function configuration are lower than the limits applied in the namespace.



<a name="loio7007c618a2f74bfaba8ac6e1bb2c1ecf__section_lkx_jxd_pdc"/>

## Limitation for the Number of Functions

There is no upper limit of Functions that you can run on Kyma. Once you define a Function, its build jobs and runtime Pods are always requested by Function Controller. It's up to Kubernetes to schedule them based on the available memory and CPU time on the Kubernetes worker nodes. This is determined mainly by the number of the Kubernetes worker nodes \(and the node auto-scaling capabilities\) and their computational capacity.



<a name="loio7007c618a2f74bfaba8ac6e1bb2c1ecf__section_mlm_nxd_pdc"/>

## Build Phase Limitation

> ### Note:  
> All measurements were taken on Kubernetes with five AWS worker nodes of type m5.xlarge \(four CPU 3.1 GHz x86\_64 cores, 16 GiB memory\).

The time necessary to build a Function depends on the following elements:

-   Selected [build profile](https://github.com/kyma-project/serverless/blob/main/docs/user/technical-reference/07-80-available-presets.md#build-jobs-resources) that determines the requested resources \(and their limits\) for the build phase

-   Number and size of dependencies that must be downloaded and bundled into the Function image

-   Cluster nodes specification




### Node.js

****


<table>
<tr>
<th valign="top">

 

</th>
<th valign="top">

local-dev

</th>
<th valign="top">

no profile \(no limits for resource\)

</th>
</tr>
<tr>
<td valign="top">

no dependencies

</td>
<td valign="top">

24 sec

</td>
<td valign="top">

15 sec

</td>
</tr>
<tr>
<td valign="top">

2 dependencies

</td>
<td valign="top">

26 sec

</td>
<td valign="top">

16 sec

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

local-dev

</th>
<th valign="top">

no profile \(no limits for resource\)

</th>
</tr>
<tr>
<td valign="top">

no dependencies

</td>
<td valign="top">

30 sec

</td>
<td valign="top">

16 sec

</td>
</tr>
<tr>
<td valign="top">

2 dependencies

</td>
<td valign="top">

32 sec

</td>
<td valign="top">

20 sec

</td>
</tr>
</table>

The shortest build time \(the limit\) is approximately 15 seconds and requires no limitation of the build job resources and a minimum number of dependencies that are pulled in during the build phase.

Running multiple Function build jobs at once \(especially with no limits\) may drain the cluster resources. To mitigate such risk, there is an additional limit of 5 simultaneous Function builds. If a sixth one is scheduled, it is built once there is a vacancy in the build queue.



<a name="loio7007c618a2f74bfaba8ac6e1bb2c1ecf__section_kn2_kyd_pdc"/>

## Runtime Phase Limitations

> ### Note:  
> All measurements were taken on Kubernetes with five AWS worker nodes of type m5.xlarge \(four CPU 3.1 GHz x86\_64 cores, 16 GiB memory\).

Functions serve user-provided logic wrapped in the web framework, Express for Node.js and Bottle for Python. Taking the user logic aside, those frameworks have limitations and depend on the selected [runtime profile](https://github.com/kyma-project/serverless/blob/main/docs/user/technical-reference/07-80-available-presets.md#functions-resources) and the Kubernetes nodes specification.

The following table present the response times of the selected runtime profiles for a "Hello World" Function requested at 50 requests/second. This describes the overhead of the serving framework itself. Any user logic added on top of that adds extra milliseconds and must be profiled separately.



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

response time \[avarage\]

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

response time \[avarage\]

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

Function runtime Pods can be scaled horizontally from zero up to the limits of the available resources at the Kubernetes worker nodes. See the [Use External Scalers](https://kyma-project.io/#/serverless-manager/user/tutorials/01-130-use-external-scalers) tutorial for more information.



<a name="loio7007c618a2f74bfaba8ac6e1bb2c1ecf__section_vy1_xzd_pdc"/>

## In-Cluster Docker Registry

Serverless comes with an in-cluster Docker registry for the Function images. For more information on the Docker registry configuration, see [Configuring Docker Registry](configuring-serverless-b40a119.md#loiob40a11952da84394b430118082754e6c__task_obs_wwq_rfc).

