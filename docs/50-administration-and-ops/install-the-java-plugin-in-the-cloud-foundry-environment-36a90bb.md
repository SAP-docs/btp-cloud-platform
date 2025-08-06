<!-- loio36a90bb2f1a04122ac1f1214c77765d4 -->

# Install the Java Plugin in the Cloud Foundry Environment

The Java plugin provides convenience utilities to work with Java applications deployed on Cloud Foundry.



<a name="loio36a90bb2f1a04122ac1f1214c77765d4__prereq_bdl_zvh_1fc"/>

## Prerequisites

You have installed the Cloud Foundry command line interface \(cf CLI\). See: [Download and Install the cf CLI](https://help.sap.com/docs/btp/sap-business-technology-platform/download-and-install-cloud-foundry-command-line-interface?version=Cloud)



## Procedure

1.  Open the command line interface or terminal.

2.  Check if you already have the Java plugin installed. Run:

    ```
    cf plugins
    ```

    If the **`java`** plugin is installed, you have to uninstall it first. Run:

    ```
    cf uninstall-plugin java
    ```

3.  Before installing the latest available version of the plugin, make sure you have the Cloud Foundry community repository in your cf CLI.

    If it is not available there, you need to add it. Run:

    ```
    cf add-plugin-repo CF-Community https://plugins.cloudfoundry.org
    ```

4.  Install the latest Java plugin version. Run:

    ```
    cf install-plugin -r CF-Community java
    ```

    > ### Tip:  
    > In case the latest version is not available in the Cloud Foundry community repository, you can perform a manual installation:
    > 
    > 1.  Download the binary file for your target operating system from the [latest release](https://github.com/SAP/cf-cli-java-plugin/releases/latest).
    > 2.  If you've already installed the plugin and you're now updating it, run: `cf uninstall-plugin java`
    > 3.  Now install the plugin. Run: `cf install-plugin [cf-cli-java-plugin]`
    > 
    >     **Note:** Replace `[cf-cli-java-plugin]` with the *actual* binary name you'll use, which depends on your operating system.

5.  Verify that the plugin has been installed successfully. Run:

    ```
    cf plugins
    ```




<a name="loio36a90bb2f1a04122ac1f1214c77765d4__result_hsz_hv3_1fc"/>

## Results

You see a list of cf CLI plugins that now includes the **`java`** one. The output also displays commands that are specific to this plugin.

