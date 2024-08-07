<!-- loioec0e986509eb4219a8705c9823ccba6b -->

# Creating the Sender Channel SAP\_COM\_0A22



## Context

Outline:

-   Create a new communication arrangement
    -   Create a new communication system.
        -   Create a new outbound user: choose the daemon user created before.
        -   Additionally, create a new inbound user as destination.

    -   Save the communication system.

-   Save the communication arrangement.



## Procedure

1.  Open the SAP Fiori launchpad of the sender system.

2.  In the *Communication Management* section, open *Communication Arrangements*.

3.  Choose the *New* button.

4.  Select the scenario `SAP_COM_0A22`, labeled *Enterprise Event Enablement - Direct Event Outbound Integration*.

5.  Enter an arrangement name and choose *Create*.

    The communication arrangement editor is opened.

6.  In the *Common Data* section, next to the *Communication System* field, choose *New* to create a new communication system.

    The communication system editor is opened.

7.  In the *General* section, paste the API-url you created in the communication arrangement of receiver channel into the *Host Name* field.

    Paste the url without `https://`.

    For more information about where to find the API-url for the host name, see [Creating the Receiver Channel SAP\_COM\_0A23](creating-the-receiver-channel-sap-com-0a23-ef154bd.md).

8.  In the section *Users for Outound Communication*, choose the *\+* symbol on the right to create a new user.

    1.  For the *Authentication Method*, select *User Name and Password*.

    2.  In the *User Name/Client ID* field, enter the inbound user you created in the receiver channel.

    3.  Enter the *Password* you defined for the inbound user of the receiver channel.

    4.  Choose *Create*.


    A new outbound user is added to the communication system.

9.  In the section *Users for Inbound Communication*, choose the *\+* symbol on the right to create a new user.

    1.  For the *Authentication Method*, select *User Name and Password*.

    2.  Leave the *User Name/Client ID* field blank and choose *New User*.

        The *Create Communication User* editor is opened.

    3.  Enter a *User Name* and a *Description*.

    4.  Enter a *Password* or choose *Propose Password*.

    5.  Choose *Create*.

    6.  Choose *OK* in the *New Inbound Communication User* popup window.


    A new inbound user is created and added to the communication system.

10. In the *Communication Arrangements* window, in the *Additional Properties* tab, provide a *Channel* and a *Description*.

    You can choose any channel name. For example, you can use the same as for the communication arrangement for both channel and description.

11. In the *Communication Partner ID* field, enter the name of the SAP\_COM\_0A23 receiver channel you created before.

12. Choose *Save*.

    The communication arrangement is activated.


