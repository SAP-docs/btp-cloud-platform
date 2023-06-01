<!-- loio1e9d11c61d57430aac86ced6500d752b -->

# Configuring Subscriptions



## Prerequisites

-   You have established a connection through the configuration of the communication arrangement in the previous steps. For more information, refer to [Communication Arrangements](communication-arrangements-2144420.md).

-   The *Enterprise Event Enablement ‒ Configure Channel Bindings* app is visible.

    If the *Enterprise Event Enablement ‒ Configure Channel Bindings* app is not visible, add the *Enterprise Event Enablement* business catalog to the `SAP_BR_ADMINISTRATOR` role using the *Maintain Business Roles* app. The change in your role becomes effective after you have logged out and logged in again. For more information about adding catalogs to business roles, refer to [Maintain Business Roles](maintain-business-roles-8980ad0.md).




## Context

Subscriptions, which are based on a queue, provide all incoming events. These incoming events are forwarded to the corresponding consumer.

> ### Note:  
> Events are only forwarded to an event consumer when an inbound event topic binding exists for the related event topic.



## Procedure

1.  Log on to the SAP Fiori launchpad in the SAP S/4HANA Cloud system.

2.  In the *Communication Management* app, select the *Enterprise Event Enablement ‒ Configure Channel Binding* app.

3.  Choose a channel name \(created in [Creating Communication Arrangements](creating-communication-arrangements-78ababb.md)\).

4.  In the *Subscriptions* tab, you can do the following:


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
    
        **Create a new subscription.**


    
    </td>
    <td valign="top">
    
        1.  Choose *Create*.
    2.  Enter a valid subscription address that corresponds to the name of the queue created in the SAP Event Mesh.
    3.  Choose *Create* to save your entries.

    The new subscription is listed in the *Subscriptions* table.

    > ### Note:  
    > You can create a maximum of 10 subscriptions.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        **Delete an existing subscription.**


    
    </td>
    <td valign="top">
    
        1.  Select the checkbox of the subscription you want to delete.
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

Subscriptions must have a valid subscription address provided by the SAP Event Mesh. Both subscriptions and inbound bindings are required to consume events. For more information, refer to [Configuring Inbound Event Topic Bindings](configuring-inbound-event-topic-bindings-b62727d.md).

The *Subscriptions* table contains all subscriptions that exist for the selected channel. The different fields can have the following values:


<table>
<tr>
<td valign="top">

**Status: New**



</td>
<td valign="top">

Subscription was newly created and has not been acknowledged by the SAP Event Mesh service instance yet.



</td>
</tr>
<tr>
<td valign="top">

**Status: Acknowledged**



</td>
<td valign="top">

Subscription is active and acknowledged by the SAP Event Mesh service instance.



</td>
</tr>
<tr>
<td valign="top">

**Status: Rejected**



</td>
<td valign="top">

The channel has been deactivated and the subscription is rejected by the SAP Event Mesh service instance.



</td>
</tr>
<tr>
<td valign="top">

**Status: Inactive**



</td>
<td valign="top">

Subscription wasn't acknowledged by the SAP Event Mesh service instance.



</td>
</tr>
<tr>
<td valign="top">

**Subscription Address**



</td>
<td valign="top">

Depicts the current address.



</td>
</tr>
<tr>
<td valign="top">

**Type Kind**



</td>
<td valign="top">

Queue-Based Subscription



</td>
</tr>
</table>

