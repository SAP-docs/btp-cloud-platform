<!-- loiobf3186f34ae747ed9c0f601ac5ac1394 -->

# Assigning users to the SAP Application Interface Framework



## Prerequisites

The user must have the business role `BR_CONF_EXPERT_BUS_NET_INT` \(Configuration Expert ‒ Business Network Integration\). If the user doesn't have the business role `BR_CONF_EXPERT_BUS_NET_INT`, add the business role in the *Maintain Business Roles* app.



## Context

In order to receive alerts for the consumption with the given *Event Consumption Model*, you can assign your user to the SAP Application Interface Framework interface by a corresponding recipient.



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
        -   *Recipient Name*: Choose the generated recipient name.

            The generated recipient name is a <generic\_hash\> with the description <event\_consumption\_model\_id\> <event\_consumption\_model\_version\> \#\#GENERATED.

        -   *Message Type*: Choose a *Message Type*.

        > ### Tip:  
        > There is also a general monitoring case with the *Recipient Name* *RECIPIENT\_CHANNEL*. Refer to [Assigning recipients to users](assigning-recipients-to-users-a9cd185.md).

    2.  Choose *Assign* to save the user assignment.

        The assigned recipient is now displayed in the *Recipients for User* list.





## Next Steps

If you want to assign additional recipients to the user, click the *Assign* button on the right hand side of the *Recipients for User* list and repeat the steps.

