<!-- loioeaac92b93d8e4ca0a7d239232693fb91 -->

# Using Message Monitoring



## Context

Before you can display messages in the *Message Monitoring for Integration Experts* app, you must assign a user to a specific recipient. Refer to [Assigning Recipients to Users](assigning-recipients-to-users-14a9615.md).



## Procedure

1.  Log on to the SAP Fiori launchpad in the ABAP environment system.

2.  Open the *Message Monitoring for Integration Experts* app.

    1.  Enter the following parameters:

        -   *Time*: Define the period of time to be considered.
        -   *From*: Specify the period of time.
        -   *To*: Specify the period of time.
        -   *Interface*: Enter `/IWXBE_TECHNICAL` or select `/IWXBE_TECHNICAL` from the combo box.
        -   *Additional Interface Options*: Specify the interface that should be displayed.

    2.  Choose *Go*.


    The *Message Status Overview* screen displays your interfaces and all error messages with the following states:

    -   All
    -   Error
    -   Warning
    -   Success
    -   In Process
    -   Canceled




## Next Steps

You can click the number of received messages of a specific status to display the corresponding list of messages. Select a message from the *Log Details* section to display the log message details on the right-hand side of the screen. If there is a correlation between the error message and the related communication arrangement, the *Display Communication Arrangement* link is displayed in the *Functions* section. Click the link to open the *Communication Arrangements* app and to display the related communication arrangement.

> ### Note:  
> You need authorization to open the *Communication Arrangements* app. For more information, refer to [Creating Technical Communication User](creating-technical-communication-user-576291c.md).

**Related Information**  


[Message Monitoring for Integration Experts](https://help.sap.com/docs/btp/sap-business-technology-platform/message-monitoring-for-integration-experts)

