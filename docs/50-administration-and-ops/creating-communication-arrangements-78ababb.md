<!-- loio78ababbcfbf3403fb50f01c64f3e22e0 -->

# Creating Communication Arrangements

In this topic, a communication arrangement is created.



## Prerequisites

-   You have a subaccount in SAP BTP, Cloud Foundry environment. Refer to [Getting Started with a Trial Account in the Cloud Foundry Environment](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/e50ab7b423f04a8db301d7678946626e.html).

-   You have created a service instance for SAP Event Mesh. If you haven't created a service instance before, refer to [Creating an Enterprise Messaging Service Instance](https://help.sap.com/viewer/bf82e6b26456494cbdd197057c09979f/Cloud/en-US/d0483a9e38434f23a4579d6fcc72654b.html).

    > ### Note:  
    > When defining the *Service Descriptor* for the service instance of the SAP Event Mesh service, make sure that the length of the *namespace* property does not exceed the maximum of 24 characters.
    > 
    > For more information about the syntax, see [Syntax for Service Descriptor](https://help.sap.com/docs/SAP_EM/bf82e6b26456494cbdd197057c09979f/5696828fd5724aa5b26412db09163530.html).

-   The key user must have the business role `SAP_BR_ADMINISTRATOR` \(Administrator\) that contains the business catalog `SAP_CORE_BC_COM` \(Communication Management\).




## Context

Create a communication arrangement to enable the exchange of events.

> ### Note:  
> Events can only be published if the topic space matches the namespace of the SAP Event Mesh service.



## Procedure

1.  Log on to the SAP Fiori launchpad in the SAP S/4HANA Cloud system.

2.  In the *Communication Management* app, select the *Communication Arrangements* artifact.

3.  Choose *New* to create a new communication arrangement.

4.  Enter or select the *Scenario* `SAP_COM_0092` \(communication scenario ID\) for *Enterprise Eventing Integration*.

5.  Adapt the *Arrangement Name*.

6.  To specify additional properties, proceed as follows:

    -   You can either use the default values and can ignore the following substeps.
    -   To maintain additional properties, choose the *Additional Properties* button and see the following substeps.

    1.  Specify the *Channel* name. The *Channel* name is required in the next steps to configure topic bindings.

        > ### Note:  
        > Optional. If the *Channel* name is not specified, the *Channel* name equals the *Arrangement Name*. The channel name is used as a key in all enterprise event enablement SAP Fiori applications.

    2.  Enter a *Description*.

        > ### Note:  
        > Optional. If you don't enter a description, this field will be filled with a default description similar to `Channel CHANNEL_NAME for Enterprise Event Enablement`.

    3.  Enter the *Topic Space*.

        > ### Note:  
        > Optional. The *Topic Space* is extracted from the service key.

    4.  Enter the *QoS* \(Quality of Service\) value. The default QoS value is 1.

        > ### Note:  
        > Optional.
        > 
        > 
        > <table>
        > <tr>
        > <th valign="top">
        > 
        > 0
        > 
        > 
        > 
        > </th>
        > <th valign="top">
        > 
        > 1
        > 
        > 
        > 
        > </th>
        > </tr>
        > <tr>
        > <td valign="top">
        > 
        > At most once delivery.
        > 
        > 
        > 
        > </td>
        > <td valign="top">
        > 
        > At least once delivery.
        > 
        > 
        > 
        > </td>
        > </tr>
        > <tr>
        > <td valign="top">
        > 
        > The message is delivered according to the capabilities of the underlying network. No response is sent by the receiver and no retry is performed by the sender. The message arrives at the SAP Event Mesh either once or not at all.
        > 
        > 
        > 
        > </td>
        > <td valign="top">
        > 
        > This Quality of Service ensures that the message arrives at the SAP Event Mesh at least once.
        > 
        > 
        > 
        > </td>
        > </tr>
        > </table>

    5.  Enter the *Reconnect Attempts* value. The default value of the reconnection attempts is 0.

        > ### Note:  
        > Optional. The reconnect attempts value is the number of attempts the enterprise event enablement framework tries to reestablish the connection if the connection is lost.
        > 
        > If the value is 0, the framework tries to reconnect infinitely \(until the connection is reestablished\).
        > 
        > If any value greater than 0 is specified, the framework tries to reestablish the connection as many times as specified. If the connection is not established after reaching the specified reconnect attempts, the communication arrangement and the underlying channel are deactivated. You can reactivate the communication arrangement and channel by selecting the corresponding communication arrangement and choosing *Reactivate*.


    1.  Define the *Reconnect wait time\(sec\)*. The default wait time for reconnection is 10 seconds.

        > ### Note:  
        > Optional. The enterprise event enablement framework waits for the mentioned time \(in seconds\) and then tries to reconnect. The value entered here is the initial wait time. For all subsequent wait times, the enterprise event enablement framework increases the wait time according to the internal logic. If the attempts fail, the framework increases the wait time until the reconnect wait time \(1800 seconds\) is reached.


7.  Choose *Close* to confirm your entries.

8.  Select a *Communication User*.

    For information about how to create a communication user, see [Creating Technical Communication User](creating-technical-communication-user-a089d73.md).

9.  Enter the *Service Key*.

10. Choose *Create*.

    > ### Note:  
    > The connection is checked automatically. If the check fails, the communication arrangement is not created and the end user is informed about the failure reasons.

    The edit page is opened.

11. Optional: In the *Outbound Services* section, under *Delivery of Events*, you can unmark the *Active* checkbox to save the communication arrangement in status "inactive". This can be useful, for example, if you want to complete the allowlisting before activating the communication arrangement. To activate the communication arrangement at a later time, open the edit screen again and set the mark for the *Active* checkbox.

12. Choose *Save*.

    After saving the communication arrangement, the channel is activated and the connection is established. The result of the connection test is displayed in the message view on the bottom left.




## Results

You have created a communication arrangement.

