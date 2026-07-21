<!-- loiof4265c65ee77444fb79b7b2b98f070e9 -->

# Pods Created by Jobs Can’t Finish



<a name="loiof4265c65ee77444fb79b7b2b98f070e9__section_rdv_2jb_4gc"/>

## Symptom

Pods created by Jobs remain in the `NotReady` status after the main containers have finished.



<a name="loiof4265c65ee77444fb79b7b2b98f070e9__section_qw1_fjb_4gc"/>

## Cause

By default, the Istio module 1.22 and later versions inject `istio-proxy` containers as native sidecars. However, you can also set the annotation `sidecar.istio.io/nativeSidecar` to *"false"* for a specific Pod. This annotation overwrites the default setting and indicates that instead of native sidecars, the annotated Pod must be injected with a regular `istio-proxy` container.

When `istio-proxy` is a regular container, it runs independently of the application container. There is no mechanism that shuts down the `istio-proxy` regular container when the main container completes its tasks. Consequently, the Pod is also running.



<a name="loiof4265c65ee77444fb79b7b2b98f070e9__section_z1c_fjb_4gc"/>

## Solution

Check whether `istio-proxy` is declared as `initContainer` or `container`.

-   If it is an `initContainer`, it means that `istio-proxy` already runs as a native sidecar. Since native sidecars do not cause problems with incomplete Jobs, the root cause of the issue is not related to the type of containers used by Istio proxies.
-   If `istio-proxy` is declared as a regular container, switch to using a native sidecar instead. To do this, apply the annotation `sidecar.istio.io/nativeSidecar="true"` on the Pod or in the Pod template. See the following example:

    > ### Sample Code:  
    > ```
    > apiVersion: batch/v1
    > kind: Job
    > metadata:
    >   name: test-job
    >   namespace: test
    > spec:
    >   template:
    >     metadata:
    >       annotations:
    >         sidecar.istio.io/nativeSidecar: "true"
    >     spec:
    >       containers:
    >       - name: test-job
    >         image: alpine:latest
    >         command: [ "/bin/sleep", "10" ]
    >       restartPolicy: Never
    > ```


When `istio-proxy` runs as a native sidecar, its lifecycle depends on the main application container, so `istio-proxy` finishes automatically at the same time as the main application container. After this, the Pod's state changes to ***Completed***.

**Related Information**  


[Regular and Native Sidecar Containers](regular-and-native-sidecar-containers-b1e4cd0.md "Understand the differences between Istio proxies running as regular containers and as native sidecars, learn about the default settings applied by the Istio module, and find out how to override these settings for specific workloads as needed.")

