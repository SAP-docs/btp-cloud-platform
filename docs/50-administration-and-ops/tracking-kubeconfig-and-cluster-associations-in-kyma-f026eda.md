<!-- loiof026eda1bd4749219be37d83012f07c5 -->

# Tracking Kubeconfig and Cluster Associations in Kyma

You can identify which kubeconfig is associated with a particular Kyma cluster by the value of the *Cluster Name* parameter.

The [Cluster Name\*](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Cluster_Name) \(technical name: `name`\) parameter specifies the name of your cluster. Its value is also used in the kubeconfig of a Kyma instance as a context name and a user name \(if OIDC authentication is configured\). With the *\{CLUSTER\_NAME\}* value used in this way, you can track the kubeconfig - cluster associations.

If multiple OIDC configurations are provided, user entries are generated following this incremental naming convention:

-   *\{CLUSTER\_NAME\}*
-   *\{CLUSTER\_NAME-2\}*
-   *\{CLUSTER\_NAME-3\}*

The pattern continues for additional users. Without any OIDC configuration, the `users` section is omitted.

To view the kubeconfig file, you can download it from the SAP BTP cockpit. In your subaccount *Overview*, go to the *Kyma Environment* section and choose the *KubeconfigURL* link.

See how the *\{CLUSTER\_NAME\}* value is used in a typical kubeconfig file:

```
---
apiVersion: v1
kind: Config
current-context: {CLUSTER_NAME}
clusters:
  - name: {CLUSTER_NAME}
    cluster:
      certificate-authority-data: {CERTIFICATE_DATA}
      server: {SERVER_URL}
contexts:
  - name: {CLUSTER_NAME}
    context:
      cluster: {CLUSTER_NAME}
      user: {CLUSTER_NAME}
users:
  - name: {CLUSTER_NAME}
    user:
      exec:
        apiVersion: client.authentication.k8s.io/v1beta1
        args:
          - get-token
          - "--oidc-issuer-url={ISSUER_URL}"
          - "--oidc-client-id={CLIENT_ID}"
          - "--oidc-extra-scope=email"
          - "--oidc-extra-scope=openid"
        command: kubectl-oidc_login
        installHint: |
          kubelogin plugin is required to proceed with authentication
          # Homebrew (macOS and Linux)
          brew install int128/kubelogin/kubelogin

          # Krew (macOS, Linux, Windows and ARM)
          kubectl krew install oidc-login

          # Chocolatey (Windows)
          choco install kubelogin
```

