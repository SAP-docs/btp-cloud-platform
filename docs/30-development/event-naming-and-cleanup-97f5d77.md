<!-- loio97f5d77d27af4f5a91c98a5502975de6 -->

# Event Naming and Cleanup

The Eventing module uses event names to identify and route events to subscribers. Learn about the supported event types, the naming conventions, and how the Eventing module handles event names with prohibited characters.



<a name="loio97f5d77d27af4f5a91c98a5502975de6__section_event_types"/>

## Event Types

Event names depend on the type of event. Eventing supports the following event types:

-   CloudEvents: Events that conform to the [CloudEvents specification](https://cloudevents.io/). This is the recommended standard for describing event data in a common way. The specification is currently under the [CNCF](https://www.cncf.io/).
-   Legacy events: Events or messages published to Kyma that do not conform to the CloudEvents specification. The Eventing Publisher Proxy converts all legacy events into CloudEvents before processing them.



<a name="loio97f5d77d27af4f5a91c98a5502975de6__section_event_name_format"/>

## Event Name Format

The event name format ensures compatibility with CloudEvents specifications and underlying messaging backends.

For a Subscription custom resource \(CR\), the fully qualified event name follows a structure like `order.created.v1` or `Account.Root.Created.v1`.

An event type consists of the following components:

-   Event: Typically, has two or three segments separated by a dot \(`.`\); for example, `order.created` or `Account.Root.Created`
-   Version: A version identifier, typically `v1`

For publishers, the event type takes these sample forms:

-   `order.created` or `Account.Root.Created` for legacy events coming from the `commerce` application
-   `order.created.v1` or `Account.Root.Created.v1` for CloudEvents



<a name="loio97f5d77d27af4f5a91c98a5502975de6__section_event_name_cleanup"/>

## Event Name Cleanup

The Eventing Publisher Proxy modifies event names to filter out prohibited characters. This ensures compliance with CloudEvents specifications and the underlying messaging backend \(such as [NATS JetStream specifications](https://docs.nats.io/running-a-nats-service/nats_admin/jetstream_admin/naming)\).

If an event name contains prohibited characters, the Eventing Publisher Proxy removes these characters and uses the cleaned name for internal processing and routing. For example, if an event type is `order.payment*success.v1`, the Eventing module cleans it to `order.paymentsuccess.v1`.

To check the Subscription's cleaned event type, run: `kubectl get subscriptions {SUBSCRIPTION_NAME} -o=jsonpath="{.status.types}"`

This cleanup happens internally; you can still publish and subscribe using the original event names \(with prohibited characters\). However, the Eventing module processes the cleaned version.

> ### Caution:  
> This can lead to a naming collision if two different original event names clean up to the same internal name. For example, both `system>prod` and `systemprod` become `systemprod`. While this does not result in an error, a naming collision can cause subscribers to receive irrelevant events or miss expected events. For details, see [Subscriber Receives Irrelevant Events](subscriber-receives-irrelevant-events-d4f3166.md).

When you verify event delivery in your Function logs, the received event type reflects the cleaned name, not the original name you defined in the `Subscription` or published with.

