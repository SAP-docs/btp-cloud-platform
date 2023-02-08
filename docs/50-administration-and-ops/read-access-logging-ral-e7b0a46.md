<!-- loioe7b0a46a4bbf400e8a052dac277ab803 -->

# Read Access Logging \(RAL\)



With *Read Access Logging* \(RAL\) for events, you can monitor and log read access to sensitive data because of diverse data privacy regulations. The categorization of sensitive data can vary: it can depend on your country’s code of law or on your external or internal company policies. RAL thus helps you to find out who had access to sensitive data, in which way and at what time.

RAL is offered for different channels. A channel is a way for data to leave the system, for example dynpros of Web services. The enterprise event enablement is another channel that is supported in the central RAL monitor.

For more information on RAL in the context of SAP NetWeaver, see [Read Access Logging](https://help.sap.com/doc/saphelp_scm70/7.0/en-US/54/69bbeab2e94c93b9031584711d989d/frameset.htm).

> ### Note:  
> Using RAL requires system resources. This can have a strong impact on your system performance, depending on the number and type of logs.



Events can be logged for two scenarios:

-   Read access of events during support \(monitoring\)

    This is the case when the event monitor was opened by SAP support to check the payload of sent or consumed events.

-   Read access of events during sending \(runtime\)

    This is the case when an outbound binding exists and an event is to be sent to the SAP Event Mesh by the enterprise event enablement. For more information, refer to [Configuration of Event Publishing and Event Consumption Scenarios](configuration-of-event-publishing-and-event-consumption-scenarios-978b039.md).


You can define which properties of an event are to be logged to avoid that all events are logged. Consider this carefully as it may affect the system performance.

The following types can be logged once a corresponding configuration exists:


<table>
<tr>
<td valign="top" rowspan="3">

Channel Fields



</td>
<td valign="top">

Condition Fields



</td>
<td valign="top">

Access Context



</td>
</tr>
<tr>
<td valign="top">

Cloud Event Context Fields



</td>
<td valign="top">

-   Source
-   Type
-   Id
-   Time



</td>
</tr>
<tr>
<td valign="top">

Payload Types



</td>
<td valign="top">

Payload types of a selected producer or consumer. A producer or consumer is a set of event types belonging to a business entity.



</td>
</tr>
<tr>
<td valign="top" rowspan="3">

System Fields



</td>
<td valign="top" colspan="2">

User Name



</td>
</tr>
<tr>
<td valign="top" colspan="2">

Screen Title



</td>
</tr>
<tr>
<td valign="top" colspan="2">

Transaction code



</td>
</tr>
</table>

**Related Information**  


[Read Access Logging](read-access-logging-5688c3a.md "")





