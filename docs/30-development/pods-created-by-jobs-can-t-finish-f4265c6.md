<!-- loiof4265c65ee77444fb79b7b2b98f070e9 -->

# Pods Created by Jobs Can’t Finish



<a name="loiof4265c65ee77444fb79b7b2b98f070e9__section_rdv_2jb_4gc"/>

## Symptom

Pods created by Jobs remain in the `NotReady` status after the main containers have finished.



<a name="loiof4265c65ee77444fb79b7b2b98f070e9__section_qw1_fjb_4gc"/>

## Cause

The `istio-proxy` sidecar runs as a regular sidecar container, independently of the application container. There is no mechanism that shuts down the `istio-proxy` sidecar when the main container completes its tasks. Consequently, the Pod is also running.



<a name="loiof4265c65ee77444fb79b7b2b98f070e9__section_z1c_fjb_4gc"/>

## Solution

Inject `istio-proxy` as a native sidecar container.

To do this, set the `sidecar.istio.io/nativeSidecar` annotation in the Pod template to `"true"`.

See the following example:

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

This annotation instructs Istio to run `istio-proxy` as a native sidecar container. Then, the lifecycle of the native sidecar depends on the main application container, so `istio-proxy` finishes automatically at the same time as the main application container. After this, the Pod’s state changes to `Completed`.

**Related Information**  


[Istio Proxy as Native Sidecar Container](https://kyma-project.io/#/istio/user/00--istio-proxy-as-native-sidecar)

