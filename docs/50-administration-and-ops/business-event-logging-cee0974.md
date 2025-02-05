<!-- loiocee09744c9584649ac1d6d05473c6e56 -->

# Business Event Logging

Business Event Logging enables you to log business events that are raised by SAP S/4HANA applications when business processes run in the local system.

You can activate Business Event Logging using configuration activities for each object, such as Sales Order, Outbound Delivery, and so on. Business event is a message that is sent to notify a consumer that an object has changed. These events are defined in the SAP Business Accelerator Hub. Events are triggered during the execution of business activities. For example, you can find events such as **created**, **changed**, and **deleted** for `Sales Order`.

The business event logs give you insights into the way processes run in the local system. You can get an overview of all the logged business events, the number of events triggered, and the types of business events triggered.

This graphic displays the components of Business Event Logging:

![](images/BEL_ABAP_c8e837b.png)



<a name="loiocee09744c9584649ac1d6d05473c6e56__section_hrk_qtd_yqb"/>

## Benefits

With Business Event Logging, you can collect records of these business events, irrespective of whether the event is subscribed to or not, to get insights into the way business processes run in the local system. You can either store the default information or the complete business event data, depending on your configuration settings.

Essential properties of an event are stored by default. These properties are:

-   Objects
-   Object components
-   Business object key
-   Date of event
-   Event type \(corresponding to performed action\)
-   User who performed the action
-   Relevant field changes
-   Qualifiers \(for generic events\)

In addition, field changes are recorded as long as they are defined in the business events.

