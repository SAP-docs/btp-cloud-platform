<!-- loio2c267133264049f9b366ff6be5740037 -->

# Subscribe to Multiple Event Types

Configure a single Subscription to receive events of multiple types.



## Prerequisites

-   You have the Eventing module in your Kyma cluster.
-   You have access to Kyma dashboard. Alternatively, if you prefer CLI, you need kubectl and curl.
-   Optionally, you have the [CloudEvents Conformance Tool](https://github.com/cloudevents/conformance) for publishing events.
-   You have an inline Function as event sink \(see [Create and Modify an Inline Function](https://kyma-project.io/external-content/serverless/docs/user/tutorials/01-10-create-inline-function.html)\).

> ### Tip:  
> Use Istio sidecar proxies for reliability, observability, and security \(see [Istio Service Mesh](istio-service-mesh-ca84edb.md)\).



## Context

To subscribe to multiple events, you need a Subscription custom resource \(CR\). The following example shows how to subscribe to events of two types: `order.received.v1` and `order.changed.v1`.

If you want to subscribe to more event types, add more types to your subscription.



## Procedure

1.  Create a subscription with multiple event types.

    -   In Kyma dashboard, find the default namespace, go to *Configuration* and create a `Subscription` with the following parameters:
        -   *Subscription name*: `lastorder-sub`
        -   *Types*: `order.received.v1` and `order.changed.v1`
        -   *Service*: `lastorder` \(the sink is populated automatically\)
        -   *Type matching*: `standard`
        -   *Source*: `myapp`

    -   With kubectl, run:

    ```
    cat <<EOF | kubectl apply -f -
     apiVersion: eventing.kyma-project.io/v1alpha2
     kind: Subscription
     metadata:
      name: lastorder-sub
      namespace: default
     spec:
      sink: 'http://lastorder.default.svc.cluster.local'
      source: myapp
      types:
        - order.received.v1
        - order.changed.v1
    EOF
    
    ```

2.  Verify that the subscription is ready.

    -   In Kyma dashboard, the status must be ***READY***.
    -   Alternatively, run `kubectl get subscriptions lastorder-sub -o=jsonpath="{.status.ready}"` and see if the response is ***true***.

3.  Port-forward the Eventing Publisher Proxy to `localhost`, using port `3000`:

    ```
    kubectl -n kyma-system port-forward service/eventing-publisher-proxy 3000:80
    
    ```

4.  To publish the first event \(type `order.received.v1`\) to trigger your Function, open another terminal window:

    -   With the CloudEvents Conformance Tool, run:

        ```
        cloudevents send http://localhost:3000/publish \
           --type order.received.v1 \
           --id cc99dcdd-6f6d-43d6-afef-d024eb276584 \
           --source myapp \
           --datacontenttype application/json \
           --data "{\"orderCode\":\"3211213\", \"orderStatus\":\"received\"}" \
           --yaml
        
        ```

    -   With *curl*, run:

        ```
        curl -v -X POST \
           -H "ce-specversion: 1.0" \
           -H "ce-type: order.received.v1" \
           -H "ce-source: myapp" \
           -H "ce-eventtypeversion: v1" \
           -H "ce-id: cc99dcdd-6f6d-43d6-afef-d024eb276584" \
           -H "content-type: application/json" \
           -d "{\"orderCode\":\"3211213\", \"orderStatus\":\"received\"}" \
           http://localhost:3000/publish
        
        ```


5.  Publish the second event \(type `order.changed.v1`\) to trigger your Function.

    -   With the CloudEvents Conformance Tool, run:

        ```
        cloudevents send http://localhost:3000/publish \
           --type order.changed.v1 \
           --id 94064655-7e9e-4795-97a3-81bfd497aac6 \
           --source myapp \
           --datacontenttype application/json \
           --data "{\"orderCode\":\"3211213\", \"orderStatus\":\"changed\"}" \
           --yaml
        
        ```

    -   With curl, run:

        ```
        curl -v -X POST \
           -H "ce-specversion: 1.0" \
           -H "ce-type: order.changed.v1" \
           -H "ce-source: myapp" \
           -H "ce-eventtypeversion: v1" \
           -H "ce-id: 94064655-7e9e-4795-97a3-81bfd497aac6" \
           -H "content-type: application/json" \
           -d "{\"orderCode\":\"3211213\", \"orderStatus\":\"changed\"}" \ 
           http://localhost:3000/publish
        
        ```


6.  To verify that the event was delivered, check the logs of the Function.

    -   In Kyma dashboard, return to the view of your `lastorder` Function and go to *Code* \> *Replicas of the Function*. Select your replica and under *Containers*, view the logs.
    -   With kubectl, run:

        ```
        kubectl logs \
        -n default \
        -l serverless.kyma-project.io/function-name=lastorder,serverless.kyma-project.io/resource=deployment \
        -c function
        
        ```





## Results

You see the received event in the logs:

```
Received event: { orderCode: '3211213', orderStatus: 'received' }
Received event: { orderCode: '3211213', orderStatus: 'changed' }

```

