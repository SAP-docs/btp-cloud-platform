<!-- loio38b5744273324b60b782948afce5241a -->

# Event Consumer

In this topic, you can find information about how to enable the event consumption for an *Event Consumption Model* defined using the `ABAP Development Tools` and how to set up the corresponding communication arrangement.



The communication arrangement `SAP_COM_0092` defines the connection from SAP S/4HANA Cloud to the SAP Event Mesh instance. Via this communication arrangement, the ABAP environment receives events from the event queue and transfers the events to the *Event Consumption Model*, which then processes the event. The event is processed according to the logic implemented in the handle event method of the consumer extension class.

The following steps are required to configure the event consumer:

**Related Information**  


[Queue Subscriptions](queue-subscriptions-e859a14.md "Events published through an SAP S/4HANA Cloud instance can be consumed at the SAP Event Mesh. Events published to a queue defined in your SAP Event Mesh service instance can also be consumed in SAP S/4HANA Cloud. Queues can be used to buffer events until a consumer can process them. For the right events to arrive at a queue, the queue must be subscribed to the corresponding topics. A consumer can then subscribe to the queue.")

