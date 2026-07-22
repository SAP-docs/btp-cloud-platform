<!-- loio0771999d5751423188b55344a8b284e2 -->

# Managing Registry Cache Configuration

List and delete `RegistryCacheConfig` resources in your cluster.



## Procedure

-   To list all `RegistryCacheConfig` resources across all namespaces, run:

    ```
    kubectl get registrycacheconfig -A
    ```

-   To list resources in a specific namespace, run:

    ```
    kubectl get registrycacheconfig -n <namespace>
    ```

-   To delete a `RegistryCacheConfig` resource, run:

    ```
    kubectl delete registrycacheconfig <name> -n <namespace>
    ```

    For example:

    ```
    kubectl delete registrycacheconfig config -n test
    ```


