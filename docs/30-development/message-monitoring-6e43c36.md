<!-- loio6e43c36fc7b34e8e986b03d8a7023964 -->

# Message Monitoring

The `/IWXBE_TECHNICAL` interface allows you to receive messages in case a technical error occurs. You can monitor the messages using the *Message Monitoring for Integration Experts* app, provided by the *SAP Application Interface Framework* \(SAP AIF\).



<a name="loio6e43c36fc7b34e8e986b03d8a7023964__section_aqn_ryw_nqb"/>

## Prerequisites

Before you can display messages in the *Message Monitoring for Integration Experts* app, you must assign a user to a specific recipient. To do so, proceed as follows:

1.  Log on to the SAP Fiori launchpad.

2.  Open the *Assign Recipients to Users* app. A list containing all users that are already assigned to recipients is displayed.

3.  Click the + in the bottom row of the left-hand side of the screen.

    > ### Note:  
    > If want to add additional recipients to a user who is already assigned to a recipient, use the *Search Users with Assigned Recipients* search field.

4.  On the *Add User* dialog box, enter a user and press *Add*. The *Assign Recipients* dialog box opens.

5.  In the *Assign Recipients* dialog box, enter the following:

    -   Namespace: `/IWXBE`

    -   Recipient Name: `RECIPIENT_CHANNEL`

    -   Message Type: *Technical Error*


6.  Press *Assign* to save the user assignment. The assigned recipient is now displayed in the *Recipients for User* list.


> ### Note:  
> If you want to assign additional recipients to the user, click the *Assign* button on the right hand side of the *Recipients for User* list and repeat step 3.

For more information, see [Assign Recipients to Users](../50-administration-and-ops/assign-recipients-to-users-576fa8d.md)



<a name="loio6e43c36fc7b34e8e986b03d8a7023964__section_txy_xsj_4qb"/>

## Message Monitoring

To use *Message Monitoring* for *Enterprise Event Enablement*, proceed as follows:

1.  Log on to the SAP Fiori launchpad.

2.  Click the *Message Monitoring for Integration Experts* tile.

3.  Enter the following parameters:

    -   Time: define the period of time to be considered.

    -   From - To: specify the period of time.

    -   Interface: enter `/IWXBE_TECHNICAL` or choose it from the drop-down list.

    -   Additional Interface Options: specify the interface that should be displayed.


4.  Press *Go*.


For more information, see [Message Monitoring for Integration Experts](../50-administration-and-ops/message-monitoring-for-integration-experts-69bf7dc.md).

Once you have performed the above-mentioned steps, the *Message Status Overview* screen opens displaying your interfaces and all error messages with the following statuses:

-   All

-   Errors

-   Warnings

-   Success

-   In Process

-   Canceled


You can click the number of received messages of a specific status to display the corresponding list of messages. Select a message from the*Log Details* section to display the log message details on the right-hand side of the screen. If there is a correlation between the error message and the related communication arrangement, the *Display Communication Arrangement* link is displayed in the *Functions* section. Click the link to open the *Communication Arrangements* app and to display the related communication arrangement.

> ### Note:  
> You need authorization to open the *Communication Arrangements* app. For more information, see [Create Technical Communication User](create-technical-communication-user-a089d73.md).

