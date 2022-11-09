<!-- loio214442004da34f738a97f7e924db7fed -->

# Create, Maintain and Delete Communication Arrangements

A communication arrangement is required for the event exchange between *SAP S/4 HANA Cloud* and the SAP BTP, Cloud Foundry environment.



<a name="loio214442004da34f738a97f7e924db7fed__prereq_g2t_2wf_llb"/>

## Prerequisites

-   You have created a service instance for SAP Event Mesh. For more information, see [Create an Enterprise Messaging Service Instance](https://help.sap.com/viewer/bf82e6b26456494cbdd197057c09979f/Cloud/en-US/d0483a9e38434f23a4579d6fcc72654b.html).

-   The service instance contains all information required to establish a connection inside the service key. This required information, such as endpoints and credentials, are extracted from the service key. The *Enterprise Event Enablement* creates the corresponding destination and OAuth 2.0 client configuration automatically.

-   When defining the Service Descriptor for the service instance of the SAP Event Mesh service, make sure that the length of the *namespace* property doesn't exceed the maximum of 24 characters.


*Service Key*

The service key, created in SAP Event Mesh, contains all information required to establish a connection. This information is extracted and used to create a destination and an OAuth 2.0 configuration. By using the service key while creating a communication arrangement, the administrator saves manual steps on the *S/4HANA Cloud* system. These required configurations are created automatically by the *Enterprise Event Enablement* framework.



<a name="loio214442004da34f738a97f7e924db7fed__context_cnl_cdg_llb"/>

## Context

*Create a Communication Arrangement*

1.  Log on to the SAP Fiori launchpad in the *SAP S/4HANA Cloud* system.

2.  Under the *Communication Management* section, select the *Communication Arrangement* tile.

3.  Choose *New* to create a new communication arrangement.

4.  Select *SAP\_COM\_0092* \(Communication scenario ID\) for *Enterprise Eventing Integration*.

5.  Adapt the *Arrangement Name*.

    > ### Note:  
    > If the channel name is not specified in the *Additional Properties* section, the channel name equals the arrangement name.

6.  Press the *Additional Properties* button.

    1.  Add *Channel* as additional property and specify the channel name. The channel name is required in the next steps to configure topic bindings.

    2.  Enter a description.

        > ### Note:  
        > Optional. If you don't enter a description, this field will be filled with a default description.

    3.  Enter the *QoS* value.

        > ### Note:  
        > QoS is quality of service.
        > 
        > QoS=0, at most once delivery.
        > 
        > The message is delivered according to the capabilities of the underlying network. No response is sent by the receiver and no retry is performed by the sender. The message arrives at SAP Event Mesh either once or not at all.
        > 
        > QoS=1, at least once delivery. This quality of service ensures that the message arrives at SAP Event Mesh at least once.

    4.  Enter the *Reconnect Attempts* value.

        > ### Note:  
        > The attempts value is the number of attempts the *Enterprise Event Enablement* framework tries to reestablish the connection if the connection is lost. If the value is 0, the framework tries to reconnect infinitely \(until the connection is reestablished\).
        > 
        > If any value \> 0 is specified, the framework tries to reestablish the connection as many times as specified. If the connection is not established after reaching reconnect attempts, the communication arrangement and the underlying channel is deactivated.

    5.  Define the *Reconnect Waittime*.

        > ### Note:  
        > The *Enterprise Event Enablement* framework waits for the mentioned time \(in seconds\) and then tries to reconnect. The value entered here is the initial waittime. For all subsequent waittimes, the *Enterprise Event Enablement* framework increases the waittime according to the internal logic. If the attempts fail, the framework increases the waittime until the reconnect waittime \(1800 seconds\) is reached. The default reconnect waittime is 10 seconds.


7.  Press *Save* to save your entries.

8.  Choose *Communication User* \(the communication user has been created in the previous step\).

9.  Enter the service key.

10. Choose *Create*. The connection is checked automatically. If the check fails, the communication arrangement is not created and the end-user is informed about the failure reasons.


*Maintain a Communication Arrangement*

You can still change parameters, either via service key or by entering parameters manually. This can be used to change the default values for QoS, the number of reconnect attempts, the reconnect waittime, and the topic space.

> ### Note:  
> Events can only be published if the topic space matches the namespace of the SAP Event Mesh service.

1.  To change connection details, press the *Update via Service Key* button.

2.  Enter the service key with the new connection details.

3.  Press *Update* to save your entries.

4.  To change additional properties, press *Edit*.

5.  Press *Close*.


*Delete a Communication Arrangement*

To delete a communication arrangement, proceed as follows:

1.  Log on to the SAP Fiori launchpad in the *SAP S/4HANA Cloud* system.

2.  Under the *Communication Management* section, select the *Communication Arrangement* tile.

3.  Choose a communication arrangement from the list.

4.  Press the *Delete* button.


> ### Note:  
> When a communication arrangement is deleted, all events belonging to the channel - including those that have not yet been successfully published to the SAP Event Mesh service - are deleted from the event queue.

