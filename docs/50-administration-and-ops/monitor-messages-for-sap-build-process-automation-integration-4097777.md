<!-- loio40977772a5814a04b1b079d30b5200f8 -->

# Monitor Messages for SAP Build Process Automation Integration

You can monitor the background processes for the integration of the SAP Build Process Automation.



<a name="loio40977772a5814a04b1b079d30b5200f8__prereq_ggw_qpy_rkb"/>

## Prerequisites

You have assigned business roles and business users.



<a name="loio40977772a5814a04b1b079d30b5200f8__context_pmz_cwv_5tb"/>

## Context

With the *Message Dashboard* or *Message Monitoring Overview*, you can monitor and administrate the SAP Build Process Automation background processing. You can manually trigger or cancel monitored background tasks that have issues.

AIF messages are deleted after a retention time, which can be configured in AIF customizing. The default value for all workflow-relevant namespaces and interfaces is set to 7 days.



## Procedure

1.  Log on to the SAP Fiori launchpad as an administrator user.

2.  With the *Assign Recipients to Users* app, assign the corresponding recipients to a business user.

    1.  Select the user for which you want to perform the assignment.

    2.  Repeatedly choose *Assign* and successively enter the following recipients:


        <table>
        <tr>
        <th valign="top">

        Namespace
        
        </th>
        <th valign="top">

        Recipient
        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
        `/SWFCP`\(for workflow capability\)
        
        </td>
        <td valign="top">
        
        *REC\_PROC\_BGRFC \(process bgRFC\)*

        REC\_RAISE\_EVT \(Recipient for raise of event\)
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `/SWFPV` \(for process visibility capability\)
        
        </td>
        <td valign="top">
        
        *EVENT\_PUBL \(Process bgRFC\)* 
        
        </td>
        </tr>
        </table>
        
        Also choose the message types that the user is allowed to view.

        For more information, see [Assigning Users to Recipients](https://help.sap.com/viewer/1cefaed5b7a3471cb08564e54d5ba866/4.0/en-US/2e8e31dff6e747249240601291384bc3.html).


3.  To view the results, open the *Message Dashboard* app.

4.  To view the triggered messages, use the *Calendar Monitor* to select the date range and choose *Search*.

5.  Alternatively, view the results with the *Message Monitoring Overview* app.

    The overview displays the interfaces and message types to which you’re subscribed. To see more details, click a message type.


**Related Information**  


[Blog on Working with the Message Dashboard](https://blogs.sap.com/2018/11/07/how-to-enable-users-to-work-with-the-message-dashboard/)

