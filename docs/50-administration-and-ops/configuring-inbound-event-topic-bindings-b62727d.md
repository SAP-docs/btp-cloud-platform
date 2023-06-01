<!-- loiob62727d018e84a499c5ef5837a6d9263 -->

# Configuring Inbound Event Topic Bindings



## Prerequisites

-   You have established a connection through the configuration of the communication arrangement in the previous steps. For more information, refer to [Communication Arrangements](communication-arrangements-2144420.md).

-   The *Enterprise Event Enablement ‒ Configure Channel Bindings* app is visible.

    If the *Enterprise Event Enablement ‒ Configure Channel Bindings* app is not visible, add the *Enterprise Event Enablement* business catalog to the `SAP_BR_ADMINISTRATOR` role using the *Maintain Business Roles* app. The change in your role becomes effective after you have logged out and logged in again. For more information about adding catalogs to business roles, refer to [Maintain Business Roles](maintain-business-roles-8980ad0.md).




## Context

You can configure event consumers delivered by SAP manually.



## Procedure

1.  Log on to the SAP Fiori launchpad in the SAP S/4HANA Cloud system.

2.  In the *Communication Management* app, select the *Enterprise Event Enablement ‒ Configure Channel Binding* app.

3.  Choose a channel name \(created in [Creating Communication Arrangements](creating-communication-arrangements-78ababb.md)\).

4.  In the *Inbound Topic Bindings* tab, you can do the following:


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

    The new topic is listed in the *Inbound Topics* table.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        **Delete an existing topic created by an end user.**


    
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

The *Inbound Topics* table contains all inbound event topic bindings that exist for the selected channel and communication arrangement. The fields can have the following values:


<table>
<tr>
<td valign="top">

**Status: Ok**



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

**Status: Incomplete**



</td>
<td valign="top">

No topic consumer exists for current topic binding.



</td>
</tr>
<tr>
<td valign="top">

**Status: Invalid**



</td>
<td valign="top">

The current topic binding is invalid for at least one topic consumer. This means either the topic filter doesn't exist or the corresponding destination is incorrect.



</td>
</tr>
<tr>
<td valign="top">

**Topic**



</td>
<td valign="top">

Is the topic presentation.



</td>
</tr>
<tr>
<td valign="top">

**Maintained by: End User**



</td>
<td valign="top">

The event inbound topic binding was created manually by an user.



</td>
</tr>
<tr>
<td valign="top">

**Maintained by: Communication Management**



</td>
<td valign="top">

The event inbound topic binding was created automatically during the configuration of a generated *Event Consumption Model*.



</td>
</tr>
</table>

> ### Note:  
> In case invalid bindings maintained by an end user exist, you can delete this binding by:
> 
> -   choosing *Delete invalid bindings* on top of the page or
> -   selecting the respective topic and choose *Delete*.

> ### Note:  
> To enable the consumption of events, the `AMQP` protocol replaces the `MQTT` protocol. New communication arrangements use the `AMQP` protocol by default. Existing communication arrangements can be updated via service key. To do so, refer to [Maintaining Communication Arrangements](maintaining-communication-arrangements-8fb8dab.md)

