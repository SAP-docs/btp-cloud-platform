<!-- loio5f9d612be915458ea22e611e91e5d57e -->

# Reuse Enterprise Event Enablement

You have a subaccount in SAP BTP, Cloud Foundry environment. Refer to [Getting Started with a Trial Account in the Cloud Foundry Environment](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/e50ab7b423f04a8db301d7678946626e.html).

You have created a service instance for SAP Event Mesh. If you haven't created a service instance before, refer to [Creating an Enterprise Messaging Service Instance](https://help.sap.com/viewer/bf82e6b26456494cbdd197057c09979f/Cloud/en-US/d0483a9e38434f23a4579d6fcc72654b.html).

The key user must have the business role `SAP_BR_ADMINISTRATOR` \(Administrator\) that contains the business catalog `SAP_CORE_BC_COM` \(Communication Management\).

The Event Mesh kernel service is provided in the SAP Business Technology Platform.

The destination URL of the Event Mesh kernel service instance is available. The destination URL is given in the corresponding service key of the SAP Event Mesh service instance.

 enterprise event enablement cloud landscape directory SAP Fiori launchpad SAP S/4HANA Cloud SAP Enterprise Messaging 1.0 for Cloud Foundry SAP Event Mesh 2.0 Event Mesh kernel service 16. Log on to the SAP Fiori launchpad in the SAP S/4HANA Cloud system.

 18. In the *Communication Management* app, select the *Communication Arrangements* artifact.

 20. Select the checkbox of the communication arrangement you want to delete.

 22. Choose *Delete*.

 



<a name="loio5f9d612be915458ea22e611e91e5d57e__result_rpj_zrn_fwb"/>

## Results

You have deleted a communication arrangement.

> ### Note:  
> When a communication arrangement is deleted, all events belonging to the channel ‒ including those that have not yet been successfully published to the SAP Event Mesh service ‒ are deleted from the event queue. Additionally, the configuration for the underlying channel, such as inbound and outbound bindings, is deleted.

