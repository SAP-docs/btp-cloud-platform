<!-- loioc0653cddfdb1478a90ec1ecbb3e5a65b -->

# Event Publishing



## Prerequisites

-   You have established a connection through the configuration of the communication arrangement in the previous steps. For more information, refer to [Communication Arrangements](communication-arrangements-2144420.md).

-   The *Enterprise Event Enablement ‒ Configure Channel Bindings* app is visible.

    If the *Enterprise Event Enablement ‒ Configure Channel Bindings* app is not visible, add the *Enterprise Event Enablement* business catalog to the `SAP_BR_ADMINISTRATOR` role using the *Maintain Business Roles* app. The change in your role becomes effective after you have logged out and logged in again. For more information about adding catalogs to business roles, refer to [Maintain Business Roles](maintain-business-roles-8980ad0.md).




## Context

You can configure outbound event topic bindings for publishing events.



## Procedure

1.  Log on to the SAP Fiori launchpad in the SAP S/4HANA Cloud system.

2.  In the *Communication Management* app, select the *Enterprise Event Enablement ‒ Configure Channel Binding* app.

3.  Choose a channel name \(created in [Creating Communication Arrangements](creating-communication-arrangements-78ababb.md)\).

4.  In the *Outbound Topic Bindings* tab, you can do the following:


    <table>
    <tr>
    <th valign="top">

    Option


    
    </th>
    <th valign="top">

    Description


    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
        **Create a new topic.**


    
    </td>
    <td valign="top">
    
        1.  Choose *Create*.
    2.  Enter a topic name.
    3.  Choose *Create* to save your entries.

    The new topic will be listed in the *Topic* table.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        **Delete an existing topic.**


    
    </td>
    <td valign="top">
    
        1.  Select the checkbox of the topic you want to delete.
    2.  Choose *Delete*.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        **Define table parameters.**


    
    </td>
    <td valign="top">
    
        Press the gear icon to define the table parameters.


    
    </td>
    </tr>
    </table>
    



## Next Steps

Events reside in an internal queue of the enterprise event enablement. Once the processing of an event is finalized, it is deleted from the queue. The processing of an event is finalized if:


<table>
<tr>
<td valign="top">

**Status: Ok**



</td>
<td valign="top">

The event has been successfully published according to the chosen quality of service.



</td>
</tr>
<tr>
<td valign="top">

**Status: Failed**



</td>
<td valign="top">

The enterprise event enablement failed to publish the event after 5 attempts.



</td>
</tr>
</table>

**Related Information**  


[Queue Subscriptions](queue-subscriptions-e859a14.md "Events published through an SAP S/4HANA Cloud instance can be consumed at the SAP Event Mesh. Events published to a queue defined in your SAP Event Mesh service instance can also be consumed in SAP S/4HANA Cloud. Queues can be used to buffer events until a consumer can process them. For the right events to arrive at a queue, the queue must be subscribed to the corresponding topics. A consumer can then subscribe to the queue.")

