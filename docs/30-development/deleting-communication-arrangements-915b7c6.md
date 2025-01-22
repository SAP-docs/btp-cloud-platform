<!-- loio915b7c6cc90646208fa6a87c97d2cbb3 -->

# Deleting Communication Arrangements

In this topic, a communication arrangement is deleted.



## Prerequisites

The key user must have the business role `SAP_BR_ADMINISTRATOR` \(Administrator\) that contains the business catalog `SAP_CORE_BC_COM` \(Communication Management\).



## Context

After creating a communication arrangement, you can still delete the communication arrangement.



## Procedure

1.  Log on to the SAP Fiori launchpad in the SAP BTP ABAP environment system.

2.  In the *Communication Management* app, select the *Communication Arrangements* artifact.

3.  Select the checkbox of the communication arrangement you want to delete.

4.  Choose *Delete*.




## Results

You have deleted a communication arrangement.

> ### Note:  
> When a communication arrangement is deleted, all events belonging to the channel ‒ including those that have not yet been successfully published to the respective service ‒ are deleted from the event queue. Additionally, the configuration for the underlying channel, such as inbound and outbound bindings, is deleted.



## Next Steps

After deleting the communication arrangement, you need to delete the communication system belonging to the communication arrangement manually.

