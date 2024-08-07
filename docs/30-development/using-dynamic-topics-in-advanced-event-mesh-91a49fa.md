<!-- loio91a49fa087e3438b996ec75d97f3548b -->

# Using Dynamic Topics in Advanced Event Mesh

You can use dynamic topics for routing and filtering outbound events in the *Advanced Event Mesh* \(AEM\) .



<a name="loio91a49fa087e3438b996ec75d97f3548b__prereq_ry2_c1h_mbc"/>

## Prerequisites

> ### Note:  
> Dynamic topics are available in the *Advanced Event Mesh* \(AEM\) only.
> 
> For more information about the use of events in the context of AEM, see [Understanding Topics](https://help.pubsub.em.services.cloud.sap/Get-Started/what-are-topics.htm).

-   You have created an outbound event topic as described here: [Maintain Outbound Event Topics](maintain-outbound-event-topics-4c3ad44.md)
-   You have implemented `event.context.attribute` annotations to define dynamic topic segments for the given event type, as described in [Event Annotations](https://help.sap.com/docs/abap-cloud/abap-rap/event-annotations).
-   In addition, you have implemented `event.context.position` annotations to specify the position of the corresponding dynamic topic segment relative to the other dynamic segments.



## Context

Dynamic topics make use of the context attribute annotations to extend the corresponding event topic with further dynamic segments, derived from the corresponding annotated payload field. Dynamic topics enable detailed event filtering and routing, ensuring that events are delivered only to the relevant components, improving efficiency and reducing unnecessary processing.

The *Enterprise Event Enablement* framework \(EEE\) enables the usage of dynamic topics for the *Advanced Event Mesh* integration \(AEM\). A possible example for such a dynamic topic would be as follows:

`sap/custom/MySalesOrder/v1/{companyCode}/{SalesOrderID}`

```
--------------- properties ------------------------------
					to: sap.custom.MySalesOrder.Created.v1.de.10002    
					content-type: application/cloudevents+json; charset=utf-8
					
					----------- application-properties ----------------------
					
					------------- application-data --------------------------
					{
					"specversion" : "1.0",
					"type": "sap.custom.MySalesOrder.Created.v1"
					"xsapcompanycode": "de"
					"xsapsalesorder": 1002,
					"data": { ... }
					}
```

> ### Note:  
> Note that the dynamic topic segment values are also part of the CloudEvent header as defined in the `event.context.attribute` annotation.



## Procedure

To enable dynamic topics, proceed as follows:

1.  Log on to the SAP Fiori launchpad.

2.  In the *Communication Management* app,open the *Enterprise Event Enablement ‒ Configure Channel Binding* app.

3.  Select the corresponding AEM event channel.

4.  Choose the *Enable Dynamic Topics* button on the top right.

    > ### Note:  
    > When you enable dynamic topics, topics containing wildcards will be resolved, as dynamic segments are specific to a single event topic.

    In the *Outbound Topic Bindings* section, the outbound topic bindings are now displayed with the derived dynamic attributes in curly brackets.

    > ### Example:  
    > `sap/custom/MySalesOrder/v1/{companyCode}/{SalesOrderID}`

    The *Use Dynamic Topics* indicator on the top left changes to *Yes*.

5.  To disable dynamic topics, choose the *Disable Dynamic Topics* button on the top right.


