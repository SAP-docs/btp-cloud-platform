<!-- loioe859a1494f6d46748972377c93ee8705 -->

# Queue Subscriptions

Events published through an SAP S/4HANA Cloud instance can be consumed at the SAP Event Mesh. Events published to a queue defined in your SAP Event Mesh service instance can also be consumed in SAP S/4HANA Cloud. Queues can be used to buffer events until a consumer can process them. For the right events to arrive at a queue, the queue must be subscribed to the corresponding topics. A consumer can then subscribe to the queue.



## Context

Once a queue has been subscribed to the corresponding topic and you have subscribed to the queue, you can view the list of applications and service instances. The SAP Event Mesh dashboard enables you to create queues and bind incoming message topics to such queues.

> ### Note:  
> The syntax used to compose topics and the payload for SAP S/4HANA Cloud business events supports the standardized **CloudEvents** format \([https://cloudevents.io](https://cloudevents.io)\).

Ensure that the pattern of the topic, to which the queue is subscribed, consists of the following three parts:


<table>
<tr>
<th valign="top">

Name



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Topic namespace



</td>
<td valign="top">

-   Contains the three segments: vendor, product information, and a technical identifier.
-   The topic namespace originates from the namespace of the service key created for the respective SAP Event Mesh instance.

> ### Note:  
> When defining the *Service Descriptor* for the service instance of the SAP Event Mesh service, make sure that the length of the *namespace* property does not exceed the maximum of 24 characters.



</td>
</tr>
<tr>
<td valign="top">

Abbreviation



</td>
<td valign="top">

Value `ce` for cloud events



</td>
</tr>
<tr>
<td valign="top">

Event topic



</td>
<td valign="top">

Value as displayed in the value help in the previous *Outbound Topic Binding* configuration step.



</td>
</tr>
</table>

You can also use wildcards, such as `<namespace>/*`.

> ### Example:  
> If you want to create a queue-topic subscription for the `sap/s4/beh/businesspartner/v1/BusinessPartner/Changed/v1` event topic, you need to add the topic namespace and the `ce` abbreviation in the beginning of the topic: `<namespace>/ce/sap/s4/beh/businesspartner/v1/BusinessPartner/Changed/v1`.

**Related Information**  


[CloudEvents Context Attributes](cloudevents-context-attributes-823ed3e.md "Events published through the enterprise event enablement are compliant with the CloudEvents specification. Context attributes contained in events are listed in this topic.")



[Manage Queue Subscriptions](https://help.sap.com/docs/SAP_EM/bf82e6b26456494cbdd197057c09979f/753f4c9627f64a26ad349a982de5dcfe.html?version=Cloud "Manage Queue Subscriptions")

[Configuration of Event Publishing and Event Consumption Scenarios](configuration-of-event-publishing-and-event-consumption-scenarios-978b039.md "You can define which event types shall be published or consumed using a connection defined through the communication arrangement. Each event type is assigned to one topic. Topics form a logical tree to organize events, such as a folder hierarchy in a file system. Thus, the topics appear as strings that consist of multiple segments and are separated by one defined delimiter, similar to file paths.")

