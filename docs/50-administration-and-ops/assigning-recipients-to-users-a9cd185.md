<!-- loioa9cd185c9adb46f6b5d99df799fe0179 -->

# Assigning recipients to users



## Prerequisites

The user must have the business role `BR_CONF_EXPERT_BUS_NET_INT` \(Configuration Expert ‒ Business Network Integration\). If the user doesn't have the business role `BR_CONF_EXPERT_BUS_NET_INT`, add the business role in the *Maintain Business Roles* app.



## Context

Before you can display messages in the *Message Monitoring for Integration Experts* app, you must assign a user to a specific recipient.



## Procedure

1.  Log on to the SAP Fiori launchpad in the SAP S/4HANA Cloud system.

2.  Open the *Assign Recipients to Users* app.

    A list containing all users that are already assigned to recipients is displayed.

3.  Click the *\+* in the bottom row of the left-hand side of the screen.

    > ### Note:  
    > If you want to add additional recipients to a user who is already assigned to a recipient, use the *Search Users with Assigned Recipients* search field.

4.  On the *Add User* dialog box, enter a user name or a user ID.

5.  Choose *Add*.

    1.  In the *Assign Recipients* dialog box, enter the following:

        -   *Namespace*: `/IWXBE`
        -   *Recipient Name*: `RECIPIENT_CHANNEL`
        -   *Message Type*: *Technical Error*

    2.  Choose *Assign* to save the user assignment.

        The assigned recipient is now displayed in the *Recipients for User* list.





## Next Steps

If you want to assign additional recipients to the user, click the *Assign* button on the right hand side of the *Recipients for User* list and repeat the steps.

**Related Information**  


[Assign Recipients to Users](assign-recipients-to-users-576fa8d.md)

