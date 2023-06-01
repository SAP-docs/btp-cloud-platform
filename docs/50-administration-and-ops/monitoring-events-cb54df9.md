<!-- loiocb54df9dfc9d4278a3f65eb232dc167d -->

# Monitoring Events



## Prerequisites

-   You have established a connection through the configuration of the communication arrangement in the previous steps. For more information, refer to [Communication Arrangements](communication-arrangements-2144420.md).

-   The *Enterprise Event Enablement ‒ Event Monitor* app is visible.

    If the *Enterprise Event Enablement ‒ Event Monitor* app is not visible, add the *Enterprise Event Enablement* business catalog to the `SAP_BR_ADMINISTRATOR` role using the *Maintain Business Roles* app. The change in your role becomes effective after you have logged out and logged in again. For more information about adding catalogs to business roles, refer to [Maintain Business Roles](maintain-business-roles-8980ad0.md).




## Context

Using the *Enterprise Event Enablement ‒ Event Monitor* app, you can monitor events by status and access the payload.



## Procedure

1.  Log on to the SAP Fiori launchpad in the SAP S/4HANA Cloud system.

2.  In the *Communication Management* app, select the *Enterprise Event Enablement ‒ Event Monitor* app.

    You will see an overview of all configured channels. The columns filled with numbers correspond to the number of events for a given status.

3.  Choose a channel name \(created in [Creating Communication Arrangements](creating-communication-arrangements-78ababb.md)\) to access detailed information.

    The *Inbound Events* and *Outbound Events* tabs contain all inbound or outbound events by topic and status.

4.  Select a *Topic*.

    All events for the given topic and status are listed.

5.  Select an event to access detailed information.

    The detailed view of a consumer inbound event contains:


    <table>
    <tr>
    <td valign="top">
    
        *Times*


    
    </td>
    <td valign="top">
    
        -   *Publish Time*

    -   *Arrival Time*

    -   *Consume Time*

    -   *Fail Time*



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        *Event Data*


    
    </td>
    <td valign="top">
    
        -   *Cloud Event Source*

    -   *Cloud Event ID*

    -   *Quality of Service*



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        *Consumed by*


    
    </td>
    <td valign="top">
    
        -   *Consumer ID*

    -   *Consumer Version*



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        *Payload*


    
    </td>
    <td valign="top">
    
        -   *Payload*

    -   *Size \(kB\)*



    
    </td>
    </tr>
    </table>
    



Events reside in an internal queue of the enterprise event enablement. Once the processing of an event is finalized, it is deleted from the queue after a certain time period. Processing an event is finalized if the status is acknowledged or failed.


<table>
<tr>
<th valign="top">

Deletion timeline



</th>
<th valign="top">

Event status



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Hourly before the current full hour



</td>
<td valign="top">

Acknowledged



</td>
<td valign="top">

The event has been successfully published or consumed according to the chosen quality of service. An hourly background job deletes all acknowledged events from the event monitor.



</td>
</tr>
<tr>
<td valign="top">

After 24 hours



</td>
<td valign="top">

Failed



</td>
<td valign="top">

The enterprise event enablement either failed to publish the event after 5 attempts or the event could not be consumed by the corresponding consumer.



</td>
</tr>
<tr>
<td valign="top">

No deletion



</td>
<td valign="top">

Not processed yet



</td>
<td valign="top">

All events that have a different status than acknowledged or failed are not deleted since they are not yet fully processed.



</td>
</tr>
</table>

The timeline for deleting is subject to change.

