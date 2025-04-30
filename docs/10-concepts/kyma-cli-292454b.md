<!-- loio292454b34bf543afa111dec20d9da434 -->

# Kyma CLI

Kyma CLI is an essential tool for application developers who want to get started quickly and efficiently with SAP BTP, Kyma runtime. Designed to streamline workflows, it simplifies complex tasks, enabling developers to deploy and manage applications easily

> ### Caution:  
> The `alpha` group commands are still in development, which means their functions and API may be modified over time. We encourage you to explore them, but keep in mind that changes may occur.



<a name="loio292454b34bf543afa111dec20d9da434__section_mgt_m11_v2c"/>

## What is Kyma CLI

With a single command, you can push a simple application to a Kyma cluster. Kyma CLI builds the container image from source code or Dockerfile, pushes it to the in-cluster registry, and applies the necessary Kubernetes resources, eliminating the manual setup process and accelerating your development.

Kyma CLI provides a hands-on experience when interacting with Kyma’s extensions to Kubernetes API, making it easier to explore, test, and fine-tune Kyma's custom resources directly from the command line.

Kyma CLI also provides a set of commands to manage Kyma modules efficiently. You can manage, deploy, and configure modules seamlessly. With the Kyma CLI module commands, you can list available and installed modules, and add or delete them. Modules can be deployed with the default or custom configuration.



<a name="loio292454b34bf543afa111dec20d9da434__section_vyy_nx2_52c"/>

## Features

Kyma CLI provides the following features:

-   Simplified module management.

-   Automated deployments.

-   Simplified SAP BTP service instance bindings.

-   Commands providing useful automation.




<a name="loio292454b34bf543afa111dec20d9da434__section_xy1_41f_52c"/>

## Install Kyma CLI

-   Using Homebrew:

    ```
    brew install kyma-cli
    ```

-   Using GitHub releases:

    ```
    curl -sL "https://raw.githubusercontent.com/kyma-project/cli/refs/heads/main/hack/install_cli_stable.sh" | sh -
    kyma
    
    ```


**Related Information**  


[Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c "To use a Kyma module, you must add it first. Use Kyma dashboard or Kyma CLI to do that. If you don't need the module anymore, delete it to save resources.")

[Setting Your Module to the Unmanaged and Managed State](../50-administration-and-ops/setting-your-module-to-the-unmanaged-and-managed-state-c071680.md#loioc07168072c8340ecbb392260cf52c165 "In some cases, for example, for testing, you may need to modify your module beyond what is supported by its configuration. By default, when a module is in the managed state, Kyma Control Plane governs its Kubernetes resources, reverting any manual changes during the next reconciliation loop. To modify Kubernetes objects directly without them being reverted, you must set the module to the unmanaged state. In this state, reconciliation is disabled, ensuring your manual changes are preserved.")

