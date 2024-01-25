<!-- loio18aea20dad1744bdb6e8f3e6fa1078ac -->

# Maintain Filters for Outbound Event Topics

You can filter the events that should be sent via a channel by defining filters per channel and topic.



## Prerequisites

-   You have created an outbound event topic as described here: [Maintain Outbound Event Topics](maintain-outbound-event-topics-4c3ad44.md)



## Context

You can define filters for context and extension context attributes defined for the corresponding event type. In the *RESTful Application Programming* framework \(RAP\), you can define a custom context attribute for your RAP business object with the CDS annotation *@event.context.attribute*.

For more information on the CDS annotation, see: [Event Annotations](https://help.sap.com/docs/abap-cloud/abap-rap/event-annotations)

The custom defined context attribute is then available as a property in the event filter creation wizard in the *Enterprise Event Enablement ‒ Configure Channel Binding* app.



## Procedure

1.  Log on to the SAP Fiori launchpad in the ABAP environment system.

2.  In the *Communication Management* app, select the *Enterprise Event Enablement ‒ Configure Channel Binding* app.

3.  Choose a channel.

    In the *Outbound Topics* table, the column *Has Event Filters* indicates whether filters are defined for the outbound topic.

4.  Open an *Outbound Topic*.

    Choose the *Event Filter* tab to display existing filters for the outbound topic.

5.  To add a filter to the outbound topic, choose *Create Event Filter*.

6.  On the *Create Event Filter* dialog box, proceed as follows:

    1.  Select a *Property* from the dropdown menu. The properties available in the dropdown menu are defined by the extension attributes.

    2.  Choose an *Option* from the dropdown menu to define the filter behavior.

    3.  Define a *Low Value*. You can use the value help, if available for the respective property.

    4.  If applicable, define a *High Value*.

    5.  Choose *Create Event Filter*.

        The new filter is added to the outbound topic. In accordance with exisiting filters, the new filter is added with an *OR* logic for inclusive options such as *EQUALS*. New filters are added with an *AND* logic for exclusive options such as *NOT EQUALS*. Different Properties are always *AND* connected.

        To delete a filter from an outbound event topic, select one or more filters and choose the *Delete* button.

        > ### Note:  
        > For more information on the usage of event filters, refer to [3343266](https://me.sap.com/notes/3343266).



