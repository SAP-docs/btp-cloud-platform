<!-- loio1bc4f81bdddf4d03bde6c4e59367c636 -->

# Deleting Communication Arrangements



## Prerequisites

You've created a communication arrangement. Refer to [Creating Communication Arrangements](creating-communication-arrangements-980bd73.md).



## Context



## Procedure

1.  Log on to the SAP Fiori launchpad in the SAP S/4HANA Cloud system.

2.  In the *Communication Management* app, select the *Communication Arrangements* artifact.

3.  Select the checkbox of the communication arrangement you want to delete.

4.  > ### Note:  
    > Deleting a communication arrangement can cause loss of business data \(refer to the SAP Note [3287352](https://launchpad.support.sap.com/#/notes/3287352)\).

    Choose *Delete*.




## Results

You have deleted a communication arrangement.

> ### Note:  
> When a communication arrangement is deleted, all events belonging to the channel ‒ including those that have not yet been successfully published to the SAP Event Mesh service ‒ are deleted from the event queue. Additionally, the configuration for the underlying channel, such as inbound and outbound bindings, is deleted.

