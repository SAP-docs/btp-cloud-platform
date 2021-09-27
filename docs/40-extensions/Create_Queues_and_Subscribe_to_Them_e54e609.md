<!-- loioe54e6094bb0c4c8d9aef58c54c842c98 -->

# Create Queues and Subscribe to Them



<a name="loioe54e6094bb0c4c8d9aef58c54c842c98__prereq_ewm_p25_b4b"/>

## Prerequisites

Уou have created the `SAP S/4HANA Cloud Extensibility` service instance in the Cloud Foundry or Kyma environment. See:

-   [Create an SAP S/4HANA Extensibility Service Instance in the Cloud Foundry Environment](Create_an_SAP_S4HANA_Extensibility_Service_Instance_in_the_Cloud_Foundry_Environment_531a909.md)

-   [Create an SAP S/4HANA Extensibility Service Instance in the Kyma Environment](Create_an_SAP_S4HANA_Extensibility_Service_Instance_in_the_Kyma_Environment_55d876e.md)


Уou have created the SAP Event Mesh service instance in the Cloud Foundry or Kyma environment. See:

-   [Create an SAP Event Mesh Service Instance in the Cloud Foundry Environment](Create_an_SAP_Event_Mesh_Service_Instance_in_the_Cloud_Foundry_Environment_c2d4d87.md)

-   [Create an SAP Event Mesh Service Instance in the Kyma Environment](Create_an_SAP_Event_Mesh_Service_Instance_in_the_Kyma_Environment_3de02d2.md)




## Context

After both instances are created and configured, you can create the topic-to-queue subscription. To do so, you first create a subscription to SAP Event Mesh with plan `standard`. Then, create a queue in the client that refers to the SAP Event Mesh service instance and then subscribe the topic of the namespace of the SAP S/4HANA Cloud Extensibility service to that queue.

> ### Note:  
> You can subscribe to the SAP Event Mesh service once per subaccount.



## Procedure

1.  Create a subscription to SAP Event Mesh.

    1.  In the SAP BTP cockpit, navigate to the space in which you want to create a service instance.

    2.  In the navigation area, choose *Services* \> *Service Marketplace*, and then choose *Event Mesh* in the *Service Marketplace* panel.

    3.  From the *Event Mesh* service tile, choose *Create* and follow the steps in the wizard to subscribe to the service.

    4.  In the *New Instance or Subscription* wizard:

        1.  In the *Service* dropdown list, select *Event Mesh*.

        2.  In the *Plan* dropdown list, select the *standard* service plan. Choose *Create*.

2.  Assign the necessary roles to your user.

    1.  In the SAP BTP cockpit, navigate to your subaccount.

    2.  In the navigation area, choose *Security* \> *Trust Configuration*, and then choose *SAP ID Service* in the *Trust Configuration* panel.

    3.  On the *Role Collection Assignment* page, enter the e-mail of your user in the empty field and choose *Show Assignments*. Then, choose *Assign Role Collection*.

    4.  In the *Assign Role Collection* wizard, select the following role collections:

        -   *Enterprise Messaging Administrator*

        -   *Enterprise Messaging Developer*

        -   *Enterprise Messaging Display*

        -   *Enterprise Messaging Subscription Administrator*

    5.  Choose *Assign Role Collection*.

3.  Open the SAP Event Mesh application.

    1.  In the SAP BTP cockpit, navigate to the space in which you want to create a service instance.

    2.  In the navigation area, choose *Services* \> *Instances and Subscriptions*.

    3.  In the *Subscriptions* tab, choose the *Event Mesh* application.

    4.  From the *Event Mesh* page, choose *Go to Application* and open the SAP Event Mesh application.

        > ### Note:  
        > If you are using the sample JSON files when creating the SAP S/4HANA Extensibility and the Event Mesh service instances, you should see 2 message clients in the SAP Event Mesh application, *s4hc* and *ems-s4hc*.

4.  Create a queue that is specific to your application.

    1.  Open the message client created when creating the Event Mesh service instance. For example, choose the *ems-s4hc* tile.

    2.  Choose the *Queues* tab in the message client page and then choose *Create Queue*.

    3.  Enter a queue name. Note that in the blue field of the *Create a New Queue* wizard, the final queue name is displayed. For example, if you write ***my-queue*** in the *Queue Name* field, the final queue name would be *sap/S4HANAOD/ems-s4hc/my-queue*. Choose *Create*.

5.  Subscribe this queue to the channel topic that SAP S/4HANA Cloud tenant uses to produce events.

    1.  From the *Actions* of your newly created queue, select *Queue Subscriptions*.

    2.  In the *Topic* field, enter the topic you configured in the SAP S/4HANA Cloud tenant. For example, `sap/S4HANAOD/s4hc/ce/sap/s4/beh/businesspartner/v1/BusinessPartner/Changed/v1`.

    3.  Choose *Add*.


**Related Information**  


[Manage Queues](https://help.sap.com/viewer/bf82e6b26456494cbdd197057c09979f/Cloud/en-US/57af1bd4e8f54b0a9b36414a5ec6b800.html)

