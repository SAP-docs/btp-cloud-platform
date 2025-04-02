<!-- loiod3fd620a58d74ecc9e89e54aeb79aa95 -->

# Business Event Logging

Business Event Logging enables you to log business events that are raised by SAP S/4HANA applications when business processes run in the local system. Business event is a message that is sent to notify a consumer that an object has changed. These events are listed in the SAP Business Accelerator Hub. Events are triggered during the execution of business activities. For example, you can find events such as **created**, **changed**, and **deleted** for `Sales Order`.

You can activate Business Event Logging using configuration activities for each object, such as Sales Order, Outbound Delivery, and so on. Business event is a message that is sent to notify a consumer that an object has changed.

The business event logs give you insights into the way processes run in the local system and how objects change. You can get an overview of all the logged business events, the number of events triggered, the types of business events triggered, and information on changes to fields.

This graphic displays the components of Business Event Logging:

![](images/BEL_ABAP_c8e837b.png)



<a name="loiod3fd620a58d74ecc9e89e54aeb79aa95__section_hrk_qtd_yqb"/>

## Benefits

With Business Event Logging, you can collect records of these business events, irrespective of whether the consumer has subscribed to the event, to get insights into the way business processes run in the local system. You can either store the default information or the complete business event data, depending on your configuration settings.

Essential properties of an event are stored by default. These properties are:

-   Objects
-   Object components
-   Business object key
-   Date of event
-   Event type \(corresponding to performed action\)
-   User who performed the action
-   Relevant field changes
-   Qualifiers \(for generic events\)

Field changes are also recorded as long as they are defined in the business events.

