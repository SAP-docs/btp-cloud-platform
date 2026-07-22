<!-- loiod5848fd093f64fccaf2e568f95af8cf6 -->

# Rotating Credentials

Update the credentials used by Registry Cache to authenticate against a private upstream registry.



<a name="loiod5848fd093f64fccaf2e568f95af8cf6__context_rotate_credentials"/>

## Context

Credential Secrets are immutable and cannot be updated in place.



## Procedure

1.  Create a new Secret with the updated credentials. Use a different name \(for example, `rc-secret-v2`\).

    ```
    kubectl create -f - <<EOF
    apiVersion: v1
    kind: Secret
    metadata:
      name: rc-secret-v2
      namespace: <namespace>
    type: Opaque
    immutable: true
    data:
      username: $(echo -n $USERNAME | base64 | tr -d '\n')
      password: $(echo -n $PASSWORD | base64 | tr -d '\n')
    EOF
    ```

2.  Update `spec.secretReferenceName` in the existing `RegistryCacheConfig` resource to reference the new Secret.

    ```
    kubectl patch registrycacheconfig <name> -n <namespace> \
      --type=merge -p '{"spec":{"secretReferenceName":"rc-secret-v2"}}'
    ```

3.  When the `RegistryCacheConfig` is in *Ready* state, delete the old Secret.

    ```
    kubectl delete secret rc-secret -n <namespace>
    ```


