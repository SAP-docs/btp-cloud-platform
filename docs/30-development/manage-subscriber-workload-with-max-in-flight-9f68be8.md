<!-- loio9f68be8057f14a9b8211b7470c7b7a1a -->

# Manage Subscriber Workload with Max-In-Flight

Manage your subscriber's workload by configuring the max-in-flight limit to control concurrent event delivery.



## Prerequisites

-   You have the Eventing module in your Kyma cluster.
-   You have access to Kyma dashboard. Alternatively, if you prefer CLI, you need kubectl and curl.
-   Optionally, you have the [CloudEvents Conformance Tool](https://github.com/cloudevents/conformance) for publishing events.
-   You have an inline Function as event sink \(see [Create and Modify an Inline Function](https://kyma-project.io/external-content/serverless/docs/user/tutorials/01-10-create-inline-function.html)\). Replace the default code sample with the following code. To simulate prolonged event processing, the Function waits for 5 seconds before returning the response.

    ```
    module.exports = {
      main: async function (event, context) {
        console.log("Processing event:", event.data);
        // sleep/wait for 5 seconds
        await new Promise(r => setTimeout(r, 5 * 1000));
        console.log("Completely processed event:", event.data);
        return;
      } 
    }
    
    ```


> ### Tip:  
> Use Istio sidecar proxies for reliability, observability, and security \(see [Istio Service Mesh](istio-service-mesh-ca84edb.md)\).



## Context

Your subscriber applications, such as Functions or microservices, have finite resources. To prevent overload, configure the `maxInFlightMessages` limit on your `Subscription` CRD. This limit controls the maximum number of events delivered to your subscriber without waiting for a response. The Eventing module resumes delivery after the subscriber acknowledges processing some of the existing in-flight events.



## Procedure

1.  Create a subscription that forwards a maximum of 5 events in parallel to the sink without waiting for a response.

    -   In Kyma dashboard, find the default namespace, go to *Configuration* and create a subscription with the following parameters:
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
        config:
          maxInFlightMessages: "5"
        sink: 'http://lastorder.default.svc.cluster.local'
        source: myapp
        types:
          - order.received.v1
    EOF
    
    ```

2.  Verify that the subscription is ready.

    -   In Kyma dashboard, the status must be ***READY***.
    -   Alternatively, run `kubectl get subscriptions lastorder-sub -o=jsonpath="{.status.ready}"` and see if the response is ***true***.

3.  Port-forward the Eventing Publisher Proxy to `localhost`, using port *3000*:

    ```
    kubectl -n kyma-system port-forward service/eventing-publisher-proxy 3000:80
    
    ```

4.  Publish 15 events at once and see how the Eventing module triggers the workload. In another terminal window, run:

    -   With the CloudEvents Conformance Tool:

        ```
        for i in {1..15}
        do
          cloudevents send http://localhost:3000/publish \
            --type order.received.v1 \
            --id e4bcc616-c3a9-4840-9321-763aa23851f${i} \
            --source myapp \
            --datacontenttype application/json \
            --data "{\"orderCode\":\"$i\"}" \
            --yaml
        done
        
        ```

    -   With curl:

        ```
        for i in {1..15}
        do
          curl -v -X POST \
            -H "ce-specversion: 1.0" \
            -H "ce-type: order.received.v1" \
            -H "ce-source: myapp" \
            -H "ce-eventtypeversion: v1" \
            -H "ce-id: e4bcc616-c3a9-4840-9321-763aa23851f${i}" \
            -H "content-type: application/json" \
            -d "{\"orderCode\":\"$i\"}" \
            http://localhost:3000/publish
        done
        
        ```


5.  To verify that the event was delivered, check the logs of the Function.

    -   In Kyma dashboard, return to the view of your `lastorder` Function and go to *Code* \> *Replicas of the Function*. Select your replica and under *Containers*, view the logs.
    -   With kubectl, run:

        ```
        kubectl logs \
          -n default \
          -l serverless.kyma-project.io/function-name=lastorder,serverless.kyma-project.io/resource=deployment \
          -c function
        
        ```





## Results

In the logs, you see that only 5 events were delivered to the Function in parallel. As soon as the Function completed the processing of the event and returns a response, the Eventing module delivers the next in-line event to the Function.

See the following example:

```
Processing event: { orderCode: '1' }
Processing event: { orderCode: '2' }
Processing event: { orderCode: '3' }
Processing event: { orderCode: '4' }
Processing event: { orderCode: '5' }
Completely processed event: { orderCode: '1' }
Processing event: { orderCode: '6' }
Completely processed event: { orderCode: '2' }
Processing event: { orderCode: '7' }
Completely processed event: { orderCode: '3' }
Processing event: { orderCode: '8' }
Completely processed event: { orderCode: '4' }
Processing event: { orderCode: '9' }
Completely processed event: { orderCode: '5' }
Processing event: { orderCode: '10' }
Completely processed event: { orderCode: '6' }
Processing event: { orderCode: '11' }
Completely processed event: { orderCode: '7' }
Processing event: { orderCode: '12' }
Completely processed event: { orderCode: '8' }
Processing event: { orderCode: '13' }
Completely processed event: { orderCode: '9' }
Processing event: { orderCode: '14' }
Completely processed event: { orderCode: '10' }
Processing event: { orderCode: '15' }
Completely processed event: { orderCode: '11' }
Completely processed event: { orderCode: '12' }
Completely processed event: { orderCode: '13' }
Completely processed event: { orderCode: '14' }
Completely processed event: { orderCode: '15' }

```

