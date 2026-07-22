<!-- loio9aeafcf40e724233b15108a827df637e -->

# Registry Cache Does Not Cache Images from Private Registry

Diagnose and resolve a misconfigured credential Secret that prevents Registry Cache from caching images from a private upstream registry.



<a name="loio9aeafcf40e724233b15108a827df637e__section_symptom"/>

## Symptom

You configured Registry Cache with credentials for a private upstream registry. Image pulls in your workloads succeed, but you suspect or observe that images are not being served from the cache.

> ### Note:  
> Registry Cache is designed to not impair operations if its configuration is incorrect. If you have configured an `imagePullSecret` on your workloads \(recommended\), image pulls still succeed using direct fallback to the upstream registry even when the Registry Cache credentials are incorrect. This means misconfigured credentials are not immediately visible — the only way to verify that the cache is working correctly is to check the registry cache Pod logs as described in this document.



<a name="loio9aeafcf40e724233b15108a827df637e__section_cause"/>

## Cause

When Registry Cache credentials are incorrect, the registry cache Pod in the `kube-system` namespace receives an error response from the upstream registry. Depending on the upstream registry, the error may be indistinguishable from a missing image at the log level — for example, JFrog Artifactory returns ***404*** instead of an authentication error. Meanwhile, image pulls in workloads continue to succeed using the `imagePullSecret` fallback, so the misconfiguration is not immediately visible.



<a name="loio9aeafcf40e724233b15108a827df637e__section_solution"/>

## Solution

The Gardener extension creates the registry cache Pods in `kube-system`. They are named after the upstream registry host they cache.

1.  List the registry cache Pods for the affected upstream.

    ```
    kubectl get pods -n kube-system | grep registry-<upstream-host>
    ```

2.  Check the logs of the relevant Pod.

    ```
    kubectl logs -n kube-system <pod-name> --tail=50
    ```

    A pull failure due to incorrect credentials looks similar to this one:

    ```
    level=error msg="response completed with error" err.code="manifest unknown" err.detail="unknown tag=<tag>" err.message="manifest unknown" ... http.response.status=404
    ```

3.  If you see this pattern repeating, verify that the credentials in the referenced Secret are correct and that the Secret is up to date.


