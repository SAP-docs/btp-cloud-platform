<!-- loio9af13e42d94b4597bfc298b5d09e941b -->

# Configuring the Receiver



## Context

Create a new communication arrangement representing a consumer on the receiver side.

Outline:

-   Create a new communication arrangement.
    -   Create a new communication system.
        -   Mark checkbox *Inbound Only*
        -   Set *Event Exchange Infrastructure* slider to *On*.
            -   Add the SAP\_COM\_0A23 receiver event channel.

        -   Create a new inbound user.

    -   Save the communication system.

-   Save the communication arrangement.
-   Open the receiver channel to see all inbound topics listed.



## Procedure

1.  Open the SAP Fiori launchpad of the receiver system.

2.  In the *Communication Management* section, open *Communication Arrangements*.

3.  Choose the *New* button.

4.  Select a suitable consumption scenario.

5.  Enter an arrangement name and choose *Create*.

    The communication arrangement editor is opened.

6.  In the *Common Data* section, next to the *Communication System* field, choose *New* to create a new communication system.

    The communication system editor is opened.

7.  Provide a *System ID* and a *System Name*.

    You can choose any system ID and name. For example, you can use the same as for the communication arrangement for both ID and name.

8.  Choose *Create*.

    The new *Communication System* is opened.

9.  In the *Technical Data* section, under *General*, mark the *Inbound Only* checkbox.

10. In the *OAuth 2.0 Settings* section, set the *Event Exchange Infrastructure* slider to *On*.

11. In the *Event Exchange Infrastructure* section, choose the *\+* symbol on the top right to add an event channel.

12. Select the SAP\_COM\_0A23 receiver event channel you created earlier. \(See: [Creating the Receiver Channel SAP\_COM\_0A23](creating-the-receiver-channel-sap-com-0a23-ef154bd.md)\)

13. In the section *Users for Inbound Communication*, choose the *\+* symbol on the right to create a new user. You can select an existing user from the value help or create a new one. To create a new user, proceed as follows:

    1.  For the *Authentication Method*, select *User Name and Password*.

    2.  Leave the *User Name/Client ID* field blank and choose *New User*.

        The *Create Communication User* editor is opened.

    3.  Enter a *User Name* and a *Description*.

    4.  Enter a *Password* or choose *Propose Password* and save it for later.

    5.  Choose *Create*.

    6.  Choose *OK* in the *New Inbound Communication User* popup window.


    A new inbound user is created and added to the communication system.

14. Choose *Save* in the *Communication System* creation window.

15. Choose *Save* in the *Communication Arrangement* window.




<a name="loio9af13e42d94b4597bfc298b5d09e941b__result_vns_fcx_mbc"/>

## Results

In the receiver channel, all defined inbound topics bindings are now displayed. You can now proceed to the following topic to syncronize the sender with the receiver channel.

