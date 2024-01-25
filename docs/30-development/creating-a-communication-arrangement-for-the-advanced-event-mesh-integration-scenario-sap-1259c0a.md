<!-- loio1259c0a0ad9848ca94e50d886ed8323f -->

# Creating a Communication Arrangement for the `Advanced Event Mesh Integration Scenario (SAP_COM_0492)`



## Context

This communication arrangement is the prerequisite for the `AEM Validation Service (SAP_COM_0493)`.



<a name="loio1259c0a0ad9848ca94e50d886ed8323f__steps_cmv_www_mzb"/>

## Procedure

To create a communication arrangement, proceed as follows:

1.  Log on to the SAP Fiori launchpad in the ABAP environment system.

2.  In the *Communication Management* app, select the *Communication Arrangements* artifact.

3.  Choose *New*.

4.  Enter or select the *Scenario* `SAP_COM_0492` \(communication scenario ID\) for *SAP Integration Suite, Advanced Mesh Integration*.

5.  Adapt the *Arrangement Name*.

6.  Choose *Create*.

    1.  Specify the *Channel* name. The *Channel* name is required in the next steps to configure topic bindings.

    2.  Enter a *Description*.

        > ### Note:  
        > Optional.

    3.  Enter the *Topic Space*. The topic space is the identifier for events that originate from the same source.

        > ### Tip:  
        > You can enable a sender verification for your*Advanced Event Mesh* instance by configuring the access control per client in the *SAP Integration Suite, advanced event mesh*. The following steps are required in your *Advanced Event Mesh* instance:
        > 
        > 1.  Choose *Access Control* \> *ACL Profiles*.
        > 
        > 2.  Select the client profile for which you want to configure the ACL profile.
        > 
        > 3.  Choose *Publish Topic*.
        > 
        > 4.  Select *Disallow* as *Publish Default Action*.
        > 5.  Choose the *\+ Exception* button.
        > 6.  Enter the topic space of your event channel in ABAP environment and a wildcard. For example: topic space/\> with SMF or topic space/\# with MQTT.
        > 
        > For more information, refer to [Using Client Profiles and Client Usernames](https://help.pubsub.em.services.cloud.sap/Cloud/client-profiles.htm).

        > ### Note:  
        > Mandatory. The topic space has to match regex: \[A-Za-z0-9\]\{1,\}\(/\[A-Za-z0-9\\-.\]\{1,\}\)\{2\}
        > 
        > -   Segments: exactly three \(firstSegment/secondSegment/thirdSegment\)
        > -   Allowed characters:
        >     -   First segment: \[a-zA-Z0-9\]
        >         -   Hyphens and dots aren't allowed.
        >         -   Recommended value: Default.
        > 
        >     -   Second segment: \[a-zA-Z0-9-.\]
        >         -   Starts with a character or number.
        >         -   Followed by . or -
        >         -   Must contain at least one character or number before or after the period or hyphen.
        > 
        >     -   Third segment: \[a-zA-Z0-9-.\]
        >     -   Use the same guidelines given for the second segment.
        >     -   Max Length: 24

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
        > </th>
        > <th valign="top">
        > 
        > 1
        > 
        > </th>
        > </tr>
        > <tr>
        > <td valign="top">
        > 
        > At most once delivery.
        > 
        > </td>
        > <td valign="top">
        > 
        > At least once delivery.
        > 
        > </td>
        > </tr>
        > <tr>
        > <td valign="top">
        > 
        > The message is delivered according to the capabilities of the underlying network. No response is sent by the receiver and no retry is performed by the sender. The message arrives at the SAP AEM broker either once or not at all.
        > 
        > </td>
        > <td valign="top">
        > 
        > This Quality of Service ensures that the message arrives at the SAP AEM broker at least once.
        > 
        > </td>
        > </tr>
        > </table>

    5.  Enter the *Number of Publish Connections*. Defines the number of available parallel connections to the SAP AEM broker for this channel. The default value is 1, the maximum value is 10.

        > ### Note:  
        > Optional.

    6.  Enter the *Reconnect Attempts* value. The default value of the reconnection attempts is 0.

        > ### Note:  
        > Optional. The reconnect attempts value is the number of attempts the enterprise event enablement framework tries to reestablish the connection if the connection is lost.
        > 
        > If the value is 0, the framework tries to reconnect infinitely \(until the connection is reestablished\).
        > 
        > If any value greater than 0 is specified, the framework tries to reestablish the connection as many times as specified. If the connection is not established after reaching the specified reconnect attempts, the communication arrangement and the underlying channel are deactivated. You can reactivate the communication arrangement and channel by selecting the corresponding communication arrangement and choosing *Reactivate*.

    7.  Enter the *Reconnect wait time* in seconds.

        > ### Note:  
        > Optional. The default time is 10 seconds.



To create a communication system, proceed as follows:

7.  In the *Common Data* section, press *New* to create a *Communication System*.

8.  In the *New Communication System* dialog box, proceed as follows:

    1.  Enter the *System ID*.

    2.  Enter the *System Name*.

    3.  Choose *Create*.


9.  In the *General* tab, in the *Host Name* field, enter the host name of the AMQP connectivity endpoint specified in the cluster manager of the broker instance.

    In your *AEM UI Console*, open the *Connect* tab. Find the destination URL under *Connection Details* \> *Secured AMQP Host* Copy the **host name** only.

    > ### Example:  
    > In this destination URL example:
    > 
    > `amqps://mr-connection-demo4xyz.messaging.solace.cloud:1234`
    > 
    > The host name is: `mr-connection-demo4xyz.messaging.solace.cloud`

10. Copy the digits from end part of the URL into the *Port* field.

    > ### Example:  
    > In the above mentioned destination URL example, the port number is `1234`.

11. In the *Users for Inbound Communication* tab, press *\+*.

    This user is used to run the background process that keeps the connection up and running.

12. In the *New Inbound Communication User* dialog box, proceed as follows:

    1.  Choose the *Authentication Method* *User Name and Password*.

    2.  Enter the *User Name*.

    3.  Enter a *Description*.

    4.  Choose the *Propose Password* button.

        > ### Note:  
        > The password is optional. You can leave the field empty.

    5.  Choose *Create*.

    6.  Choose *OK*.


13. In the *Users for Outbound Communication* tab, press *\+*.

14. In the *New Outbound User* dialog box, proceed as follows:

    1.  Choose the *Authentication Method* *SSL Client Certificate*.

    2.  Choose the *Client Default* for the *Client Certificate* from the value help.

    3.  Choose *Create*.


15. Choose *Save* to save the communication system.

16. Choose *Save* to save the communication arrangement.

    Note that the connection to the SAP Advanced Event Mesh only becomes active after creation of SAP\_COM\_0493.


