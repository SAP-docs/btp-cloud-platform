<!-- loio9f98dd0fcf9447019f233403f4ca60c1 -->

# Install the Custom Domain Plugin

Use the Custom Domain CLI plugin to configure and manage your custom domains.



## Prerequisites

Install the Cloud Foundry command-line interface \(CLI\) for the plugin to work. You can find the installation instructions here: [Download and Install the Cloud Foundry Command Line Interface](Download_and_Install_the_Cloud_Foundry_Command_Line_Interface_4ef907a.md).



## Procedure

1.  Download the latest version of the plugin that is compatible with your operating system. On the [Web page](https://tools.hana.ondemand.com/#cloud), you'll find the plugin under the **SAP BTP Cloud Foundry CLI plugins** section with the name Custom Domain.

2.  Untar or unzip the downloaded archive.

3.  Open the command-line interface or terminal.

4.  To install the plugin, enter the following command:

    -   Mac and Linux:

        ```
        cf install-plugin <path to the downloaded folder>/custom-domain-cli
        ```

    -   Windows:

        ```
        cf install-plugin <path to the downloaded folder>\custom-domain-cli.exe
        ```

    > ### Note:  
    > If you are reinstalling the plugin, first uninstall the previous version using: `cf uninstall-plugin "Custom Domain"` 

5.  Verify that the plugin has been installed successfully by entering:

    ```
    cf plugins
    ```

    You see a list of plugins that now includes Custom Domain. The output also displays commands that are specific to the Custom Domain plugin.




<a name="loio9f98dd0fcf9447019f233403f4ca60c1__result_cl2_wck_pgb"/>

## Results

You have installed the Custom Domain plugin for the Cloud Foundry CLI and can now use the extended commands that are available from the Custom Domain service.

**Related Information**  


[Download and Install the Cloud Foundry Command Line Interface](Download_and_Install_the_Cloud_Foundry_Command_Line_Interface_4ef907a.md "Download and set up the Cloud Foundry Command Line Interface (cf CLI) to start working with the Cloud Foundry environment.")

[Configuring Custom Domains](https://help.sap.com/viewer/74af813c7ee2457cb5eddca0cc70a0c1/Cloud/en-US/1c6c729595f144d9a0bec1b4e2ef1299.html "To make sure that your domain is trusted and all application data is protected, you must first set up secure TLS/SSL communication. Then, make your application reachable via the custom domain and route traffic to it.") :arrow_upper_right:

