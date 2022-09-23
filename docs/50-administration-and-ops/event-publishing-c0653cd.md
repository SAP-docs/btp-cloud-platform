<!-- loioc0653cddfdb1478a90ec1ecbb3e5a65b -->

# Event Publishing



<a name="loioc0653cddfdb1478a90ec1ecbb3e5a65b__section_kph_rbm_rnb"/>

## **Outbound Event Topic Bindings for Event Publishing**

You can configure outbound event topic bindings for publishing events. To do so, proceed as follows:

1.  Log on to the SAP Fiori launchpad.
2.  Click the *Enterprise Event Enablement - Configure Channel Bindings* tile from the *Enterprise Event Enablement* apps group.
3.  Choose the channel name \(created in the *Create, Maintain and Delete Communication Arrangements* area\).

On the *Outbound Topic Bindings* tab, you can do the following:

-   Create a new topic

    Press *Create*, enter a topic name and press *Create* again. The new topic will be listed in the *Topic* table.

-   Delete an existing topic

    Select a topic from the list and press*Delete*.

-   Define table parameters

    Press *Settings* to define the table parameters.


> ### Note:  
> Events reside in an internal queue of the *Enterprise Event Enablement*. Once the processing of an event is finalized, it is deleted from the queue. The processing of an event is finalized if:
> 
> -   Status: Performed successfully. The event has been successfully published according to the chosen quality of service.
> 
> -   Status: Failed. The *Enterprise Event Enablement* failed to publish the event after 5 attempts.

> ### Note:  
> Once you have chosen a channel, you can use the *Copy Bindings From Previous Version* option. This is relevant for you if you have maintained the Event-Bindings in the past in a configuration UI for the Event Enablement which was made available through the *Manage My Solution* app. If you do so, the topics defined for the selected channel in the previous product version will be migrated to the current version. All topic bindings migrated will be listed in the topic table.

For more information, see [Queue Subscriptions](queue-subscriptions-e859a14.md)

