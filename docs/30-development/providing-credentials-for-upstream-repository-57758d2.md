<!-- loio57758d2e63da4e49a7339d2ff7bfbd52 -->

# Providing Credentials for Upstream Repository

Create a Kubernetes Secret and reference it in a `RegistryCacheConfig` resource to enable Registry Cache to authenticate against a private upstream registry.



<a name="loio57758d2e63da4e49a7339d2ff7bfbd52__context_provide_credentials"/>

## Context

If the upstream registry requires authentication, create a Kubernetes Secret in the same namespace as the `RegistryCacheConfig` resource and reference it in the `spec.secretReferenceName` field. The Secret must be immutable and of type `generic`.



## Procedure

1.  Set environment variables with the upstream registry credentials.

    ```
    export USERNAME=<your username>
    export PASSWORD=<your password>
    ```

2.  Create the `test` namespace if it doesn't exist.

    ```
    kubectl create namespace test
    ```

3.  To create the credential Secret, use the procedure that matches your registry type.

    -   For registries other than Google Artifact Registry, create an immutable Secret named `rc-secret` in the `test` namespace. The credential Secret must exist in the cluster before applying the `RegistryCacheConfig` resource.

        ```
        kubectl create -f - <<EOF
        apiVersion: v1
        kind: Secret
        metadata:
          name: rc-secret
          namespace: test
        type: Opaque
        immutable: true
        data:
          username: $(echo -n $USERNAME | base64 | tr -d '\n')
          password: $(echo -n $PASSWORD | base64 | tr -d '\n')
        EOF
        ```

    -   For [Google Artifact Registry](https://cloud.google.com/artifact-registry/docs/docker/authentication), the username is `_json_key` and the password is the service account key in JSON format.

        1.  Base64-encode the service account key.

            ```
            export PASSWORD=$(echo -nE $SERVICE_ACCOUNT_KEY_JSON | base64 | tr -d '\n')
            ```

        2.  Create an immutable Secret with the encoded key as the password.

            ```
            kubectl create -f - <<EOF
            apiVersion: v1
            kind: Secret
            metadata:
              name: rc-secret
              namespace: test
            type: Opaque
            immutable: true
            data:
              username: $(echo -n "_json_key" | base64 | tr -d '\n')
              password: $PASSWORD
            EOF
            ```



4.  Apply the Registry Cache configuration referencing the created Secret.

    ```
    kubectl create -f - <<EOF
    apiVersion: core.kyma-project.io/v1beta1
    kind: RegistryCacheConfig
    metadata:
      name: config2
      namespace: test
    spec:
      upstream: <protected registry URL>
      secretReferenceName: rc-secret
      volume:
        size: 100Gi
    EOF
    ```

    > ### Note:  
    > When using a private registry, store the same credentials in the following Kubernetes Secrets:
    > 
    > -   The Secret referenced in `spec.secretReferenceName`, which Registry Cache uses to authenticate against the upstream registry when pulling images to cache.
    > -   An `imagePullSecret` on each workload, which containerd uses to authenticate directly against the upstream registry as a fallback when Registry Cache is unavailable.
    > 
    > Do not remove the `imagePullSecret` from your workloads when configuring credentials for Registry Cache. If the cache is unavailable, containerd falls back to the upstream registry and requires the credentials directly.


