<!-- loio98ee2331a4be4338a591ed6c763ed558 -->

# General Diagnostics: Event Not Delivered



## Symptom

-   You publish an event, but the subscriber doesn't receive it.
-   A `Subscription` custom resource \(CR\) is not in the ***Ready*** state.
-   You can't publish events, and the publisher receives an error.



## Cause

This issue can have several causes, from misconfiguration of the Eventing module or `Subscription` to problems with the event payload or the subscriber workload.



## Solution

Follow these steps to detect the source of the problem:



### 1. Verify that the Eventing module is healthy

1.  Check the state of the `Eventing` CR:

    ```
    kubectl get eventing -n kyma-system
    ```

2.  In the output, look for ***STATE: Ready***. If the state is not ***Ready*** \(for example, ***Warning*** or ***Error***\), inspect the CR's status for detailed error messages:

    ```
    kubectl get eventing eventing -n kyma-system -o yaml
    ```

3.  To understand the issue, review the `status.conditions` and `status.state`. For common states and recommended actions, see [Eventing Module Status and Event Flow](https://github.com/kyma-project/eventing-manager/blob/main/docs/user/resources/eventing-cr.md#eventing-module-status-and-event-flow).




### 2. Check the Subscription Status

If the `Eventing` CR is ready, check the status of your `Subscription`.

1.  Check if the `Subscription` is ready. Replace the placeholders with your values.

    ```
    kubectl get subscription {SUBSCRIPTION_NAME} -n {NAMESPACE}
    ```

2.  In the output, look for ***READY: true***. If it's ***false***, inspect the `Subscription`'s status for details:

    ```
    kubectl get subscription {SUBSCRIPTION_NAME} -n {NAMESPACE} -o yaml
    ```

3.  Examine the `status.conditions` array for error messages. A common issue is an invalid sink, which must be a valid, reachable HTTP endpoint \(for example, `http://my-service.my-namespace.svc.cluster.local`\).




### 3. Check the Publisher and Event Payload

If the `Subscription` CR is ready, verify that you are publishing the event correctly.

After sending an event, check the HTTP response code.

-   ***4xx*** error: A client-side error indicates a problem with your request. Ensure that your event conforms to the CloudEvents specification or the legacy event format. For details, see [Event Name Format](event-naming-and-cleanup-97f5d77.md#loio97f5d77d27af4f5a91c98a5502975de6__section_event_name_format).
-   ***5xx*** error: A server-side error indicates a problem with the Eventing Publisher Proxy. Check its logs for errors:

    ```
    kubectl logs -n kyma-system -l app.kubernetes.io/name=eventing-publisher-proxy
    ```

-   ***2xx*** status: Verify that the event `type` attribute in your published event exactly matches one of the types defined in your `Subscription`'s `spec.types` field.



### 4. Check the Eventing Manager Logs

The Eventing Manager is responsible for dispatching events from the backend to the subscriber.

1.  Check the logs for dispatch errors or other warnings:

    ```
    kubectl logs -n kyma-system -l app.kubernetes.io/name=eventing-manager
    ```

2.  Look for logs related to your subscription. If you use the NATS backend, a successful dispatch log contains ***"message":"event dispatched"***. If this log is missing, it could mean that the subscriber is unreachable or the NATS server is unavailable.




### 5. Check the Subscriber's Health

Ensure the subscriber application \(the sink\) is running and can receive HTTP requests.

1.  Get the sink URL from your `Subscription`:

    ```
    kubectl get subscription {SUBSCRIPTION_NAME} -n {NAMESPACE} -o jsonpath='{.spec.sink}'
    ```

2.  Run a temporary curl pod inside the cluster to test connectivity to the sink. Replace *<\{SINK\_URL\}\>* with the output from the previous command:

    ```
    # Run the test
    kubectl run sink-test --image=curlimages/curl --restart=Never -n {NAMESPACE} -- curl -v -X POST {SINK_URL}
    
    # Check the logs for the HTTP response
    kubectl logs sink-test -n {NAMESPACE}
    
    # Clean up the pod
    kubectl delete pod sink-test -n {NAMESPACE}
    
    ```


If the response code is not ***2xx***, the problem is with your subscriber application. Check its logs to diagnose the issue.



### 6. Check the NATS Backend

If all previous steps show no errors, the issue may be within the NATS backend itself. Continue with [General Diagnostics: NATS Module Readiness and Connectivity](general-diagnostics-nats-module-readiness-and-connectivity-8cdf63e.md).

