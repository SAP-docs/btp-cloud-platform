<!-- loiod280fcc3a54640f6b3601f3236e91e9c -->

# Monitor Messages for Workflow Capability Integration

You can monitor the background processes for workflow capability integration.



<a name="loiod280fcc3a54640f6b3601f3236e91e9c__prereq_ggw_qpy_rkb"/>

## Prerequisites

You have assigned business roles and business users.



<a name="loiod280fcc3a54640f6b3601f3236e91e9c__context_pmz_cwv_5tb"/>

## Context

With the *Message Dashboard* or *Message Monitoring Overview*, you can monitor and administrate the SAP Business Workflow background processing. You can manually trigger or cancel monitored background tasks that have issues.

AIF messages are deleted after a retention time, which can be configured in AIF customizing. The default value for all workflow-relevant namespaces and interfaces is set to 7 days.



<a name="loiod280fcc3a54640f6b3601f3236e91e9c__steps_oj4_q4h_lmb"/>

## Procedure

1.  Log on to the SAP Fiori launchpad as an administrator user.

2.  With the *Assign Recipients to Users* app, assign the corresponding interface to a business user.

    1.  In the *Namespace* field, enter the namespace ***/SWFCP*** for the workflow capability integration.

    2.  Select the interfaces using the recipient names:

        -   REC\_PROC\_BGRFC \(Process bgRFC\)

        -   REC\_RAISE\_EVT \(Recipient for raise of event\)


    3.  Choose the message types the user is allowed to view:

        -   Application Error or Technical Error

        -   Info

        -   Success

        -   Warning

        -   Application Error

        -   Technical Error

        -   None



    For more information, see [Assigning Users to Recipients](https://help.sap.com/viewer/1cefaed5b7a3471cb08564e54d5ba866/4.0/en-US/2e8e31dff6e747249240601291384bc3.html).

3.  To view the results, open the *Message Dashboard* app.

4.  To view the triggered messages, use the *Calendar Monitor* to select the date range and choose *Search*.

5.  Alternatively, view the results with the *Message Monitoring Overview* app.

    The overview displays the interfaces and message types to which you’re subscribed. To see more details, click a message type.


**Related Information**  


[How to enable users to work with the message dashboard](https://blogs.sap.com/2018/11/07/how-to-enable-users-to-work-with-the-message-dashboard/)

