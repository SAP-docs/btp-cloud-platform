<!-- loio8cdf63e7525444ceb951973aea78494b -->

# General Diagnostics: NATS Module Readiness and Connectivity



<a name="loio8cdf63e7525444ceb951973aea78494b__section_dmb_tzs_dhc"/>

## Symptom

-   The NATS module is not in a `Ready` state.
-   The Eventing module reports that it cannot connect to the NATS backend.
-   NATS Pods are in a `CrashLoopBackOff` or `Pending` state.



<a name="loio8cdf63e7525444ceb951973aea78494b__section_pjj_vzs_dhc"/>

## Cause

Issues with the NATS module can stem from misconfigurations in the NATS custom resource \(CR\), problems with the underlying Kubernetes Nodes, or storage issues with Persistent Volume Claims \(PVCs\).



<a name="loio8cdf63e7525444ceb951973aea78494b__section_kww_wzs_dhc"/>

## Solution



### 1. Check the NATS CR Status

1.  To verify the health of the NATS cluster, check the NATS CR.

    ```
    kubectl get nats -n kyma-system
    ```

2.  Look for `STATE: Ready`. If the state is `Error` or `Processing`, inspect the CR for detailed error messages.

    ```
    kubectl get nats {NATS_CR_NAME} -n kyma-system -o yaml
    ```

3.  Review the `status.conditions` to understand the root cause.



### 2. Check the NATS Pods

1.  Ensure all NATS Pods are running correctly.

    ```
    kubectl get pods -n kyma-system -l nats_cluster=eventing-nats
    ```

2.  If any Pods are not in the `Running` state, use `kubectl describe pod` and `kubectl logs` to investigate further.



### 3. Check the Persistent Volume Claims \(PVCs\)

1.  If you use file storage, a common issue is a problem with the PVCs.

    ```
    kubectl get pvc -n kyma-system -l nats_cluster=eventing-nats
    ```

2.  Check the `STATUS` column. If a PVC is `Pending`, there may be no available Persistent Volume that satisfies its request. If it is `Bound`, check if it is full by referring to the [NATS Backend Storage Is Full](https://github.com/kyma-project/eventing-manager/blob/main/docs/user/troubleshooting/evnt-03-free-jetstream-storage.md) guide.



### 4. Inspect the NATS JetStream

If the cluster appears healthy, you can inspect the JetStream components directly using the [NATS CLI](https://github.com/nats-io/natscli).

1.  Ensure that you have access to the NATS server \(see [Accessing the NATS Server Using CLI](https://github.com/kyma-project/nats-manager/blob/main/docs/user/01-10-access-nats-server.md)\).
2.  Port-forward to a NATS Pod.

    ```
    kubectl -n kyma-system port-forward svc/eventing-nats 4222
    ```

3.  Verify that the `kyma` stream exists.

    ```
          $ nats stream ls
      ╭────────────────────────────────────────────────────────────────────────────╮
      │                                  Streams                                   │
      ├──────┬─────────────┬─────────────────────┬──────────┬───────┬──────────────┤
      │ Name │ Description │ Created             │ Messages │ Size  │ Last Message │
      ├──────┼─────────────┼─────────────────────┼──────────┼───────┼──────────────┤
      │ sap  │             │ 2022-05-03 00:00:00 │ 0        │ 318 B │ 5.80s        │
      ╰──────┴─────────────┴─────────────────────┴──────────┴───────┴──────────────╯
    
    ```

4.  If the stream exists, check the timestamp of the `Last Message` that the stream received. A recent timestamp would mean that the event was published correctly.
5.  Check if the consumers were created and have the expected configurations.

    ```
    nats consumer info
    ```

    To correlate the consumer to the Subscription and the specific event type, check the `description` field of the consumer.

6.  If the PVC storage is fully consumed and matches the stream size as shown above, the stream can no longer receive messages. Either increase the PVC storage size \(see [NATS Backend Storage Is Full](nats-backend-storage-is-full-bb47681.md)\) or set the `MaxBytes` property which removes the old messages.

