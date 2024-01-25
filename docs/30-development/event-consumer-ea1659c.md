<!-- loioea1659c689d849d3818d4a3a1ed342a4 -->

# Event Consumer

In this topic, you can find information about how to enable the event consumption for an event consumption model defined using the `ABAP Development Tools` and how to set up the corresponding communication arrangement.



The communication arrangements `SAP_COM_0092` or `SAP_COM_0492` define the connection from ABAP environment to the respective event exchange infrastructure. Via these communication arrangements, the ABAP environment receives events from the event queue and transfers the events to the event consumption model, which then processes the event. The event is processed according to the logic implemented in the method for handling the event in the consumer extension class.

The following steps are required to configure the event consumer:

**Related Information**  


[Queue Subscriptions](queue-subscriptions-d39f689.md "Events published through an ABAP environment instance can be consumed at the SAP Event Mesh. Events published to a queue defined in your SAP Event Mesh service instance can also be consumed in ABAP environment. Queues can be used to buffer events until a consumer can process them. For the right events to arrive at a queue, the queue must be subscribed to the corresponding topics. A consumer can then subscribe to the queue.")

