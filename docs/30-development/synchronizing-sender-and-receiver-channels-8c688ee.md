<!-- loio8c688ee64ca34d6ea2c0a3e8236f324d -->

# Synchronizing Sender and Receiver Channels



## Context

Outline:

-   Open sender channel, outbound topic bindings.
    -   Choose button *Overwrite with remote topic bindings*. The available outbound topics are called from the receiver and set up automatically. Sender and receiver are now synchronized.

-   Test your connection: Go to *Event Monitor*. Mark your sender channel. Choose *Produce Test Event*. Refresh the page.



## Procedure

1.  Open the SAP Fiori launchpad of the sender system.

2.  Open the app *Enterprise Event Enablement - Configure Channel Binding*.

3.  Open your sender channel.

    The *Outbound Topic Bindings* list is empty if it hasn't been synchronized before.

4.  Choose the *Overwrite with remote topic bindings* button on the top right.

    The available outbound topics are called from the receiver channel and set up automatically in the sender channel.

    > ### Note:  
    > If the corresponding event topic cannot be assigned, for example because the event topic doesn't exist in the system, a corresponding message is displayed.
    > 
    > If the receiver receives events that are not listed in the inbound binding allowlist, these events are stored in the receiver channel in status "failed".

5.  **\[Optional\]** To test your connection, go to the *Event Monitor*.

    1.  Mark your sender channel and choose *Produce Test Event*.

    2.  Refresh the page.

        The test event is counted in the column *In Process Events* column.



