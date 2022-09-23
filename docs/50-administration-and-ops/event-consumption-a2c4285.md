<!-- loioa2c4285fba414b74b56573be88971f55 -->

# Event Consumption

Event consumption can be configured manually for some event types \(for example subscription billing\). These configuration options are described in this s. For all other event types, follow the steps described in [Creating an Event Consumption Model](https://help.sap.com/docs/SAP_S4HANA_CLOUD/25cf71e63940453397a32dc2b7676947/ea3dbc187ccd4c16aa9d0a11af1efd47.html) .



<a name="loioa2c4285fba414b74b56573be88971f55__section_vmm_btg_ytb"/>

## Initial Steps

You can configure consumption of events. To do so, proceed as follows:

1.  Log on to the SAP Fiori launchpad in the ABAP environment system.
2.  Click the *Enterprise Event Enablement - Configure Channel Bindings* tile from the Enterprise Event Enablement apps group.
3.  Choose the channel name \(created in the Create, Maintain and Delete Communication Arrangements area\)



<a name="loioa2c4285fba414b74b56573be88971f55__section_zwm_k2m_rnb"/>

## Subscriptions

Subscriptions, that are based on a queue, provide all incoming events. These incoming events are forwarded to the corresponding consumer.

> ### Note:  
> Events are only forwarded to an event consumer when an `Inbound Event Topic Binding` exists for the related event topic.

On the *Subscriptions* tab, you can do the following:

-   Create a new subscription.

    Press *Create* and enter a valid subscription address that corresponds to the name of the queue created in the SAP Event Mesh. Press *Create* again to save your entries. The new subscription is listed in the *Subscriptions* table.

    > ### Note:  
    > You can create a maximum of 10 subscriptions.

-   Delete an existing subscription.

    Select a subscription from the list and press *Delete*.


> ### Note:  
> Subscriptions must have a valid subscription address provided by the SAP Event Mesh. Once a new subscription has been created, the subscription has the status *New* until the subscription is acknowledged by the SAP Event Mesh service instance. Afterwards, the status is set to *Acknowledged*. Otherwise, the subscription gets the status *Rejected*. Both subscriptions and inbound bindings are required to consume events. For more information, refer to the next section.
> 
> The subscriptions table contains all subscriptions that exist for the selected channel. The different fields can have the following values:
> 
> -   **Status**:
> 
>     -   *Acknowledged*: Subscription is active and acknowledged by SAP Event Mesh service instance.
> 
>     -   *New*: Subscription was newly created and has not been acknowledged yet.
> 
>     -   *Inactive*: Subscription wasn't acknowledged by SAP Event Mesh service instance.
> 
> 
> -   **Subscription Address**: Depicts the current address.
> -   **Type Kind**: Queue-Based Subscription



<a name="loioa2c4285fba414b74b56573be88971f55__section_jzg_hfm_rnb"/>

## Inbound Event Topic Bindings for Event Consumption

Inbound event topic bindings are automatically created during generation and configuration of a custom `Event Consumption Model`. You can configure event consumers delivered by SAP manually.

On the *Inbound Topic Bindings* tab, you can do the following:

-   Create a new topic

    Press *Create*, enter a topic name and press *Create* again. The new topic is listed in the *Topic* table.

-   Delete an existing topic created by an user

    Select a topic from the list and press*Delete*.

-   Define table parameters

    Press *Settings* to define the table parameters.


The Inbound Topics table contains all inbound event topic bindings that exist for the selected channel and communication arrangement. The fields can have the following values:

-   **Status**:

    -   *Ok*

    -   *Incomplete*: No topic consumer exists for current topic binding.

    -   *Invalid*: The current topic binding is invalid for at least one topic consumer. This means either the topic filter doesn't exist or the corresponding destination is incorrect.


-   **Topic**: Is the topic presentation.
-   **Maintained by**
    -   *End User*: The event inbound topic binding was created manually by an user.

    -   *Communication Management*: The event inbound topic binding was created automatically during the configuration of a generated `Event Consumption Model`.



In case invalid bindings maintained by an user exist, you can select *Delete invalid bindings* to delete these bindings.

> ### Note:  
> To enable the consumption of events, the `AMQP` protocol replaces the `MQTT` protocol. New communication arrangements use the `AMQP` protocol by default. Existing communication arrangements can be updated via service key. To do so, press the *Update via Service Key* button. The communication arrangement is updated.



<a name="loioa2c4285fba414b74b56573be88971f55__section_jwt_q1s_xtb"/>

## Simulate Consumption

To allow you to test your consumer implementation, you can use the *Simulate Consumption* action . Then a dummy event of a given Topic Consumer will be sent to its consumer implementation. You can select the *Simulate Consumption* action in the *Detail View* of an Inbound Topic. In the table *Topic Consumer* at least one topic consumer must be selected, then you can execute *Simulate Consumption*.

In case of a wildcard in the topic, the wildcard is resolved and events for all resolved topics are created. The dummy events are sent to the corresponding consumer implementation. Then the simulated event is retrieved from the internal event queue and the status is checked. A short message is raised, informing the user on the success or failure of the simulation.

