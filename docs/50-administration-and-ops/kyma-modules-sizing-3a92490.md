<!-- loio3a924906857b4f01969cb684ccd25309 -->

# Kyma Modules' Sizing

The following tables show the resource consumption, such as memory, CPU, and storage, of Kyma modules.



<a name="loio3a924906857b4f01969cb684ccd25309__section_istio"/>

## Istio

**Istio Module's Sizing**


<table>
<tr>
<th valign="top">

Infrastructure size

</th>
<th valign="top">

Memory

</th>
<th valign="top">

CPU

</th>
</tr>
<tr>
<td valign="top">

Small cluster minimum

</td>
<td valign="top">

352 Mi

</td>
<td valign="top">

0.08

</td>
</tr>
<tr>
<td valign="top">

Large cluster minimum

</td>
<td valign="top">

1984 Mi

</td>
<td valign="top">

0.61

</td>
</tr>
</table>



<a name="loio3a924906857b4f01969cb684ccd25309__section_api_gateway"/>

## API Gateway

**API Gateway Module's Sizing**


<table>
<tr>
<th valign="top">

Infrastructure size

</th>
<th valign="top">

Memory

</th>
<th valign="top">

CPU

</th>
</tr>
<tr>
<td valign="top">

Small cluster minimum

</td>
<td valign="top">

212 Mi

</td>
<td valign="top">

0.03

</td>
</tr>
<tr>
<td valign="top">

Large cluster minimum

</td>
<td valign="top">

416 Mi

</td>
<td valign="top">

0.34

</td>
</tr>
</table>



<a name="loio3a924906857b4f01969cb684ccd25309__section_sap_btp_operator"/>

## SAP BTP Operator

**SAP BTP Operator Module's Sizing**


<table>
<tr>
<th valign="top">

Infrastructure size

</th>
<th valign="top">

Memory

</th>
<th valign="top">

CPU

</th>
</tr>
<tr>
<td valign="top">

Minimum

</td>
<td valign="top">

53 Mi

</td>
<td valign="top">

0.02

</td>
</tr>
<tr>
<td valign="top">

Maximum

</td>
<td valign="top">

628 Mi

</td>
<td valign="top">

1.2

</td>
</tr>
</table>



<a name="loio3a924906857b4f01969cb684ccd25309__section_application_connector"/>

## Application Connector

**Application Connector Module's Sizing**


<table>
<tr>
<th valign="top">

Infrastructure size

</th>
<th valign="top">

Memory

</th>
<th valign="top">

CPU

</th>
</tr>
<tr>
<td valign="top">

Minimum

</td>
<td valign="top">

64-128 Mi

</td>
<td valign="top">

0.2-0.5

</td>
</tr>
</table>



<a name="loio3a924906857b4f01969cb684ccd25309__section_eventing"/>

## Eventing

**Eventing Manager's Sizing**


<table>
<tr>
<th valign="top">

Infrastructure size

</th>
<th valign="top">

Memory

</th>
<th valign="top">

CPU

</th>
</tr>
<tr>
<td valign="top">

Minimum

</td>
<td valign="top">

128 Mi

</td>
<td valign="top">

0.01

</td>
</tr>
<tr>
<td valign="top">

Maximum

</td>
<td valign="top">

512 Mi

</td>
<td valign="top">

0.5

</td>
</tr>
</table>

**Eventing Publisher Proxy's Sizing**


<table>
<tr>
<th valign="top">

Infrastructure size

</th>
<th valign="top">

Memory

</th>
<th valign="top">

CPU

</th>
<th valign="top">

Max Publisher instances

</th>
</tr>
<tr>
<td valign="top">

Low EPS \(up to 200 Events per second\)

</td>
<td valign="top">

64-512 Mi

</td>
<td valign="top">

0.04-0.5

</td>
<td valign="top">

2 \(second instance for high availability\)

</td>
</tr>
<tr>
<td valign="top">

High EPS \(up to 3000 Events per second\)

</td>
<td valign="top">

64-512 Mi

</td>
<td valign="top">

0.04-0.5

</td>
<td valign="top">

3

</td>
</tr>
</table>



<a name="loio3a924906857b4f01969cb684ccd25309__section_keda"/>

## Keda

**Keda Module's Sizing**


<table>
<tr>
<th valign="top">

Infrastructure size

</th>
<th valign="top">

Memory

</th>
<th valign="top">

CPU

</th>
</tr>
<tr>
<td valign="top">

Minimum

</td>
<td valign="top">

692 Mi

</td>
<td valign="top">

0.62

</td>
</tr>
<tr>
<td valign="top">

Maximum

</td>
<td valign="top">

928 Mi

</td>
<td valign="top">

1.8

</td>
</tr>
</table>



<a name="loio3a924906857b4f01969cb684ccd25309__section_nats"/>

## NATS

By default, the NATS module creates a NATS-cluster with three nodes for data safety reasons. The values are given per NATS-cluster node:

**NATS Module's Sizing**


<table>
<tr>
<th valign="top">

Infrastructure size

</th>
<th valign="top">

Memory

</th>
<th valign="top">

CPU

</th>
<th valign="top">

Storage

</th>
</tr>
<tr>
<td valign="top">

Minimum

</td>
<td valign="top">

64 Mi

</td>
<td valign="top">

0.04

</td>
<td valign="top">

1000 Mi

</td>
</tr>
<tr>
<td valign="top">

Maximum

</td>
<td valign="top">

1000 Mi

</td>
<td valign="top">

0.5

</td>
<td valign="top">

1000 Mi

</td>
</tr>
</table>



<a name="loio3a924906857b4f01969cb684ccd25309__section_serverless"/>

## Serverless

**Serverless Module's Sizing**


<table>
<tr>
<th valign="top">

Infrastructure size

</th>
<th valign="top">

Memory

</th>
<th valign="top">

CPU

</th>
<th valign="top">

Storage

</th>
</tr>
<tr>
<td valign="top">

Minimum

</td>
<td valign="top">

400 Mi

</td>
<td valign="top">

0.03

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Maximum

</td>
<td valign="top">

2300 Mi

</td>
<td valign="top">

1.7

</td>
<td valign="top">

Up to 20000 Mi \(for PVC for internal Docker registry\)

</td>
</tr>
</table>



<a name="loio3a924906857b4f01969cb684ccd25309__section_telemetry"/>

## Telemetry

Resource consumption depends on the APIs \(pipelines\) you are using. For details, see [Module Lifecycle](../30-development/telemetry-manager-04d79d5.md#loio04d79d5517204da68029f43b9f052396__section_telemetry_module_lifecycle).

Using the Telemetry module without activating any pipelines results in the Telemetry Manager running with the following footprint:


<table>
<tr>
<th valign="top">

Infrastructure size

</th>
<th valign="top">

Memory

</th>
<th valign="top">

CPU

</th>
</tr>
<tr>
<td valign="top">

Minimum

</td>
<td valign="top">

5 Mi

</td>
<td valign="top">

0.01

</td>
</tr>
<tr>
<td valign="top">

Maximum

</td>
<td valign="top">

100 Mi

</td>
<td valign="top">

0.1

</td>
</tr>
</table>

Activation of the first `LogPipeline` causes the deployment of the log agent running an instance per node:


<table>
<tr>
<th valign="top">

Infrastructure size

</th>
<th valign="top">

Memory

</th>
<th valign="top">

CPU

</th>
</tr>
<tr>
<td valign="top">

Minimum per node

</td>
<td valign="top">

50 Mi

</td>
<td valign="top">

0.1

</td>
</tr>
<tr>
<td valign="top">

Maximum per node

</td>
<td valign="top">

1000 Mi

</td>
<td valign="top">

1

</td>
</tr>
</table>

Activation of the first `TracePipeline` causes the deployment of the trace gateway running with two replicas:


<table>
<tr>
<th valign="top">

Infrastructure size

</th>
<th valign="top">

Memory

</th>
<th valign="top">

CPU

</th>
</tr>
<tr>
<td valign="top">

Minimum

</td>
<td valign="top">

2\*32 Mi

</td>
<td valign="top">

2\*0.2

</td>
</tr>
<tr>
<td valign="top">

Maximum

</td>
<td valign="top">

2\*2000 Mi

</td>
<td valign="top">

2\*1.2

</td>
</tr>
</table>

Activation of the first `MetricPipeline` causes the deployment of the metric gateway running with two replicas and the metric agent running per node:


<table>
<tr>
<th valign="top">

Infrastructure size

</th>
<th valign="top">

Memory

</th>
<th valign="top">

CPU

</th>
</tr>
<tr>
<td valign="top">

Minimum

</td>
<td valign="top">

2\*30 Mi + 50 Mi per node

</td>
<td valign="top">

2\*0.01 + 0.01 per node

</td>
</tr>
<tr>
<td valign="top">

Maximum

</td>
<td valign="top">

2\*1000 Mi + 1200 Mi per node

</td>
<td valign="top">

2\*1.00 + 1 per node

</td>
</tr>
</table>

**Related Information**  


[Sizing](https://help.sap.com/viewer/8cc4e6b957be41d0b7a07680d1d9bb07/Cloud/en-US/48461639e27242feb3171f4fca696ec8.html "Compare the sizing for SAP BTP, Kyma runtime and SAP BTP, Cloud Foundry runtime.") :arrow_upper_right:

