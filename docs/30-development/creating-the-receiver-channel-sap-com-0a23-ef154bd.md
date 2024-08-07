<!-- loioef154bd74bb849b8aa7528bcdcfa1d1a -->

# Creating the Receiver Channel SAP\_COM\_0A23



<a name="loioef154bd74bb849b8aa7528bcdcfa1d1a__context_u3w_hx3_mbc"/>

## Context

Outline:

-   Create a new communication arrangement.
    -   Create a new communication system.
        -   Create a new inbound user as daemon user. Copy user and password.

    -   Save the communication system.

-   Save the communication arrangement. Copy API-url.



## Procedure

1.  Open the SAP Fiori launchpad of the receiver system.

2.  In the *Communication Management* section, open *Communication Arrangements*.

3.  Choose the *New* button.

4.  Select the scenario `SAP_COM_0A23`, labeled *Enterprise Event Enablement - Direct Event Inbound Integration*.

5.  Enter an arrangement name and choose *Create*.

    The communication arrangement editor is opened.

6.  In the *Common Data* section, next to the *Communication System* field, choose *New* to create a new communication system.

    The communication system editor is opened.

7.  Provide a *System ID* and a *System Name*.

    You can choose any system ID and name. For example, you can use the same as for the communication arrangement for both ID and name.

8.  Choose *Create*.

    The new *Communication System* is opened.

9.  In the *Technical Data* section, under *General*, mark the *Inbound Only* checkbox.

10. In the section *Users for Inbound Communication*, choose the *\+* symbol on the right to create a new user.

    1.  For the *Authentication Method*, select *User Name and Password*.

    2.  Leave the *User Name/Client ID* field blank and choose *New User*.

        The *Create Communication User* editor is opened.

    3.  Enter a *User Name* and a *Description*.

    4.  Enter a *Password* or choose *Propose Password* and save it for later.

    5.  Choose *Create*.

    6.  Choose *OK* in the *New Inbound Communication User* popup window.


    A new inbound user is created and added to the communication system.

11. Choose *Save* in the *Communication System* creation window.

12. In the *Communication Arrangements* window, in the *Additional Properties* tab, provide a *Channel* and a *Description*.

    You can choose any channel name. For example, you can use the same as for the communication arrangement for both channel and description. This channel name is used later during the channel configuration and monitoring.

13. From the *Common Data* section, copy the provided *API-URL* without `https://`. You will need this info later for the host name of the sender channel.

14. Choose *Save*.


