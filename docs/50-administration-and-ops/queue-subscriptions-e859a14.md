<!-- loioe859a1494f6d46748972377c93ee8705 -->

# Queue Subscriptions

Events published through an *SAP S/4HANA Cloud* instance can be consumed at the SAP Event Mesh. Events published to a queue defined in your SAP Event Mesh service instance can also be consumed in SAP S/4HANA Cloud. Queues can be used to buffer events until a consumer can process them. For the right events to arrive at a queue, the queue must be subscribed to the corresponding topics. A consumer can subscribe then to the queue.



## Context

Once a queue has been subscribed to the corresponding topic and you have subscribed to the queue, you can view the the list of applications and service instances. The SAP Event Mesh dashboard enables you to create queues and bind incoming message topics to such queues.

> ### Note:  
> Starting from *SAP S/4HANA Cloud* release 2008, the syntax used to compose topics and the payload for *SAP S/4HANA Cloud* business events will change to support the standardized *Cloud Events* format. For more information, see [Events on SAP API Business Hub](https://help.sap.com/docs/SAP_S4HANA_CLOUD/0f69f8fb28ac4bf48d2b57b9637e81fa/1e60f14bdc224c2c975c8fa8bcfd7f3f.html)
> 
> Ensure that the topic filter, to which the queue is subscribed, contains the following three parts:
> 
> -   Topic namespace: it contains three segments including the vendor, product information, and some technical identifier. The topic namespace originates from the namespace of the service key created for the respective SAP Event Mesh instance.
> 
>     > ### Note:  
>     > When defining the Service Descriptor for the service instance of the SAP Event Mesh service, make sure that the length of the *namespace* property does not exceed the maximum of 24 characters
> 
> -   Abbreviation `ce` for cloud events
> 
> -   Event Type: Event type as displayed in the value help in the previous *Outbound Topic Binding* configuration step.
> 
> 
> You can also use wildcards, such as <namespace\>/\*.
> 
> > ### Example:  
> > If you want to create a queue-topic subscription for the `sap/s4/beh/businesspartner/v1/BusinessPartner/Changed/v1` event type, you need to add the topic namespace and the 'ce' segment in the beginning of the topic: `<namespace>/ce/sap/s4/beh/businesspartner/v1/BusinessPartner/Changed/v1`.

For more information, see

-    [Manage Queue Subscriptions](https://help.sap.com/viewer/bf82e6b26456494cbdd197057c09979f/Cloud/en-US/753f4c9627f64a26ad349a982de5dcfe.html)

-   [Configure Event Publishing and Event Consumption Scenarios](configure-event-publishing-and-event-consumption-scenarios-978b039.md)

.

