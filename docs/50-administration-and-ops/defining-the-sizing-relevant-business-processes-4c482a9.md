<!-- loio4c482a90192e4fa6beb1fceca5e5623b -->

# Defining the Sizing-Relevant Business Processes

Before the actual sizing, identify sizing-relevant business processes and determine the throughput requirements for each of these business processes.



## Context

> ### Note:  
> Examples used in this sizing documentation refer to the ABAP flight reference scenario of the ABAP RESTful Programming Model. For more information, see [Downloading the ABAP Flight Reference Scenario](https://help.sap.com/viewer/923180ddb98240829d935862025004d6/Cloud/en-US/def316685ad14033b051fc4b88db07c8.html).



## Procedure

1.  Identify the main business processes of the application as well as their variable dimensions.

    The main business processes included processes that are critical for the company, for example, from revenue, reputation, or legal perspective.

    Examples of variable dimensions are the number of items in a sales order, or the number and size of documents uploaded by a user. It's unavoidable to make some assumption on these variables to limit the complexity of the resulting sizing model. As an example, it can be sufficient to assume an average of 10 items per sales order, instead of making items per sales order an input parameter of the sizing model.

2.  Determine throughput requirements for each sizing-relevant business process, with its distribution over a typical business day. Determining throughput requirements also includes the separation of business processes that are time-critical from those processes that can be postponed to times of low load. For example, a background job performing some reporting activity can be shifted into non-business hours.




<a name="loio4c482a90192e4fa6beb1fceca5e5623b__result_et4_4st_tqb"/>

## Results

The resulting overview of sizing-relevant business processes can look as follows, for example:

**Flight Reference Example: Sizing-Relevant Business Processes**


<table>
<tr>
<th valign="top">

Business Process

</th>
<th valign="top">

Load Type

</th>
<th valign="top">

Process Executions per Minute

</th>
<th valign="top">

Criticality

</th>
<th valign="top">

Variable Dimensions

</th>
</tr>
<tr>
<td valign="top">

Creation of a new travel request

</td>
<td valign="top">

HTTPS / User-driven

</td>
<td valign="top">

160 per minute during main business hours \(8 am to 7 pm\)

</td>
<td valign="top">

High

</td>
<td valign="top">

Number of bookings per travel

</td>
</tr>
<tr>
<td valign="top">

Approval of a travel request

</td>
<td valign="top">

HTTPS / User-driven

</td>
<td valign="top">

160 per minute during main business hours \(8 am to 7 pm\)

</td>
<td valign="top">

High

</td>
<td valign="top">

\--

</td>
</tr>
<tr>
<td valign="top">

Calculation and sending of metrics for reporting

</td>
<td valign="top">

Batch Job / Scheduled

</td>
<td valign="top">

Once a day

</td>
<td valign="top">

Low

</td>
<td valign="top">

Number of travel requests created per day

</td>
</tr>
</table>

In this example, variable dimensions have been turned into assumptions to simplify the sizing model and to reduce complexity of the overall sizing procedure. For the flight reference example, we can assume an average of 2 bookings per travel \(inbound and outbound flight\). With eliminating this variable dimension, the only remaining input parameter of the respective business process is the number of process executions expected per minute.

