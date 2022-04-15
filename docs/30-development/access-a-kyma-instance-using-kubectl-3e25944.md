<!-- loio3e25944e491049b2aeec68c562a5ee48 -->

# Access a Kyma Instance Using kubectl



## Context

Once you have a Kyma instance created in your subaccount of the SAP BTP cockpit, you can manage Kyma via GUI, Kyma Dashboard. If you prefer command-line tools, you can use the Kubernetes command-line tool, kubectl. To start using kubectl, follow these steps:



## Procedure

1.  Install [kubectl oidc-login](https://github.com/int128/kubelogin). Follow the original instruction from the project repository. Use the relevant commands for macOS, Linux, or Windows users.

    > ### Recommendation:  
    > On Windows, we recommend using the release binaries to install the kubectl oidc-login plugin. The installation of the kubectl oidc-login plugin using Chocolatey and Krew could cause issues.

2.  In the SAP BTP cockpit, in your subaccount *Overview*, go to the *Kyma Environment* section, and click on the *KubeconfigURL* link to download `kubeconfig.yaml`.

3.  To export the kubeconfig file, run:

    ```
    export KUBECONFIG={KUBECONFIG_FILE_PATH}
    ```

    .




<a name="loio3e25944e491049b2aeec68c562a5ee48__result_jp1_p4w_fsb"/>

## Results

Now you can manage your Kyma instance using kubectl. If you authenticate in the Kyma environment with an Identity Provider using OpenID Connect, the downloaded `kubeconfig.yaml` can be used indefinitely to re-authenticate.

