<!-- loio3936cbd523fb4e58828bc9735da06654 -->

# Troubleshooting for the Eventing Module

Troubleshoot problems related to the Eventing module.

-   [General Diagnostics: Event Not Delivered](general-diagnostics-event-not-delivered-98ee233.md): Start here if your events are not reaching their destination or your `Subscription` is not ***Ready***.
-   [Subscriber Receives Irrelevant Events](subscriber-receives-irrelevant-events-d4f3166.md): Use this guide if a subscriber receives events it did not subscribe to.
-   [NATS Backend Storage Is Full](nats-backend-storage-is-full-bb47681.md): Follow these steps if the Eventing Publisher Proxy returns a ***507 Insufficient Storage*** error.

For issues with the NATS cluster, see the NATS troubleshooting guides:

-   [General Diagnostics: NATS Module Readiness and Connectivity](general-diagnostics-nats-module-readiness-and-connectivity-8cdf63e.md): Refer to this guide for issues related to the NATS module itself, such as Pod health or stream configuration.
-   [Published Events Are Pending in the Stream](published-events-are-pending-in-the-stream-a490b23.md): Use this guide if events are stuck in the NATS stream and are not being delivered.

If you can't find a solution, don't hesitate to create a [GitHub issue](https://github.com/kyma-project/eventing-manager/issues/new/choose).

