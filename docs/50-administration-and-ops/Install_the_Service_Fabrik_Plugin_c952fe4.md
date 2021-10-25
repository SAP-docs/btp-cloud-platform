<!-- loioc952fe4806554093aa4b12abfc77fc56 -->

# Install the Service Fabrik Plugin

The Service Fabrik plugin lets you manage backups of a service instance by extending Cloud Foundry commands.



<a name="loioc952fe4806554093aa4b12abfc77fc56__prereq_nxj_nxp_d1b"/>

## Prerequisites

You need to have Cloud Foundry Command Line Interface \(CF CLI\) installed for the plugin to work since it is built on CF CLI. The installation instructions for CF CLI can be found [here](https://docs.cloudfoundry.org/cf-cli/install-go-cli.html). The minimum version of CF CLI, on which the plugin has been tested successfully is v6.20.



## Procedure

1.  Download the latest version of the plugin that is compatible with your operating system. On the Web page, you will find the plugin under the **SAP Cloud Platform Cloud Foundry CLI Plugins** section with the name **Service Fabrik based B&R**.

2.  Untar or unzip the downloaded archive.

3.  Open the command line interface or terminal.

4.  To install the plugin, enter the following command:

    -   Mac and Linux: `cf install-plugin` *<path to the downloaded folder\>**</service-fabrik-cli-plugin \[Linux/Mac\]\>*
    -   Windows : `cf install-plugin`*<path to the downloaded folder\>**<\\service-fabrik-cli-plugin.exe \[Windows\]\>*

    > ### Note:  
    > If you are reinstalling the plugin, first uninstall the previous version using: `cf uninstall-plugin ServiceFabrikPlugin` 

5.  Verify that the plugin has been installed successfully by entering `cf plugins`.

    You see a list of plugins that now includes Service Fabrik. The output also displays commands that are specific to the Service Fabrik plugin.


**Related Information**  


[https://tools.hana.ondemand.com/\#cloud](https://tools.hana.ondemand.com/#cloud)

[Download and Install the Cloud Foundry Command Line Interface](Download_and_Install_the_Cloud_Foundry_Command_Line_Interface_4ef907a.md "Download and set up the Cloud Foundry Command Line Interface (cf CLI) to start working with the Cloud Foundry environment.")

