<!-- loio90380a61db3f4fd4872e428a577ec758 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Find Inactive Users

As an administrator, you want to have an overview of the users in your subaccount, no matter which identity provider stores them. You want to clean them up if necessary.



## Context

-   You want to find users that haven't been used for some time. The reason could be that employees left the company, but the users still exist in the system.

-   You want to find users who never logged on. For example, they could be manually created shadow users with a typo in their e-mail address, so they didn't match the user ID provided by the identity provider. They were never used, and it might make sense to delete them.




## Procedure

1.  Open the SAP BTP cockpit.

2.  Go to your global account and/or subaccount \(see [Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md)\).

3.  Choose *Security* \> *Users*.

    You see all the users in your subaccount.

4.  If you want to see users that were updated at a certain point in time, use the *Last Updated* field. You can filter the list according to the following filter criteria:

    -   All

    -   Today

    -   This week

    -   This month

    -   This year


    If you want to see the users who haven't logged on at a certain point in time, use the *Hasn't Logged On* field. You can filter the list according to the following filter criteria:

    -   All

    -   Last 7 Days

    -   Last 30 Days

    -   Last 180 Days

    -   Last 365 Days

    -   Choose a Date


    The SAP BTP cockpit displays the filtered list of users. The *Last Updated* column shows you the point in time when the user was updated last. The *Last Logon* column shows you the point of time of the user's last logon.

5.  \(Optional\) To see whether a user has never logged on, choose the user to display the user's overview section.

    The SAP BTP cockpit displays the user's overview section. If the user has never logged on, the *Last Logon* field shows the message *User has never logged on*.

6.  \(Optional\) To delete the user, close the overview section and choose :wastebasket: \(Delete\).

    > ### Remember:  
    > You can't undo the deletion of a user.


