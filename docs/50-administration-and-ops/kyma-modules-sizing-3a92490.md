<!-- loio3a924906857b4f01969cb684ccd25309 -->

# Kyma Modules' Sizing

The following tables show the resource consumption, such as memory, CPU, and storage, of Kyma modules.



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

212Mi

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

416Mi

</td>
<td valign="top">

0.34

</td>
</tr>
</table>



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

352Mi

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

1984Mi

</td>
<td valign="top">

0.61

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

64-128Mi

</td>
<td valign="top">

0.2-0.5

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

53Mi

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

328Mi

</td>
<td valign="top">

0.45

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

692Mi

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

928Mi

</td>
<td valign="top">

1.8

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

400Mi

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

2300Mi

</td>
<td valign="top">

1.7

</td>
<td valign="top">

Up to 20000Mi \(for PVC for internal Docker registry\)

</td>
</tr>
</table>



<a name="loio3a924906857b4f01969cb684ccd25309__section_telemetry"/>

## Telemetry

Using the Telemetry module without further API usage results in the Telemetry Manager running with the footprint of:

****


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

5Mi

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

100Mi

</td>
<td valign="top">

0.1

</td>
</tr>
</table>

Activation of the first LogPipeline will cause the deployment of the log agent running an instance per node:

****


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

50Mi

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

1000Mi

</td>
<td valign="top">

1

</td>
</tr>
</table>

Activation of the first TracePipeline will cause the deployment of the trace gateway running with two replicas:

****


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

2\*250Mi

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

2\*2000Mi

</td>
<td valign="top">

2\*1.2

</td>
</tr>
</table>

Activation of the first MetricPipeline will cause the deployment of the metric gateway running with two replicas and the metric agent running per node:

****


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

2\*30Mi + 50Mi per node

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

2\*1000Mi + 1200Mi per node

</td>
<td valign="top">

2\*1.00 + 1 per node

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

64Mi

</td>
<td valign="top">

0.04

</td>
<td valign="top">

1000Mi

</td>
</tr>
<tr>
<td valign="top">

Maximum

</td>
<td valign="top">

1000Mi

</td>
<td valign="top">

0.5

</td>
<td valign="top">

1000Mi

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

128Mi

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

512Mi

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

64-512Mi

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

64-512Mi

</td>
<td valign="top">

0.04-0.5

</td>
<td valign="top">

3

</td>
</tr>
</table>

**Related Information**  


[Sizing](https://help.sap.com/viewer/8cc4e6b957be41d0b7a07680d1d9bb07/Cloud/en-US/48461639e27242feb3171f4fca696ec8.html "Compare the sizing for SAP BTP, Kyma runtime and SAP BTP, Cloud Foundry runtime.") :arrow_upper_right:

