<!-- loio27f3af39c2584d4ea8c15ba8c282fd75 -->

# Install the MultiApps CLI Plugin in the Cloud Foundry Environment

The MultiApps command line interface plugin \(formerly known as the MTA plugin\) for the Cloud Foundry command line interface lets you deploy, remove, and view MTAs, among other possible operations, by extending Cloud Foundry commands.



<a name="loio27f3af39c2584d4ea8c15ba8c282fd75__prereq_nxj_nxp_d1b"/>

## Prerequisites

You have installed the Cloud Foundry command line interface version 6.40 or higher. See [Download and Install the Cloud Foundry Command Line Interface](Download_and_Install_the_Cloud_Foundry_Command_Line_Interface_4ef907a.md).



<a name="loio27f3af39c2584d4ea8c15ba8c282fd75__steps_ubf_jpq_p1b"/>

## Procedure

1.  Open the command line interface or terminal.

2.  Check if a previous version is installed by using the command ***cf plugins***. If the `MtaPlugin` is already installed, you have to uninstall it using the command ***cf uninstall-plugin MtaPlugin***.

    If you do not uninstall the previous version of the plugin and try to install a new one, you receive the following error:

    > ### Output Code:  
    > ```
    > Plugin multiapps v<version> could not be installed as it contains commands with names and aliases that are already used: 
    > bg-deploy, deploy, download-mta-op-logs, mta, mta-ops, mtas, purge-mta-config, undeploy, dmol
    > ```

3.  To install the latest available version of the plugin, proceed as follows:

    1.  Make sure that you have the Cloud Foundry community repository in your Cloud Foundry command line interface. If it is not available there, add it by executing the following command:

        ***cf add-plugin-repo CF-Community https://plugins.cloudfoundry.org***

    2.  To install the plugin, enter the following command:

        ***cf install-plugin multiapps -f***

    > ### Note:  
    > Alternatively, if you want to install a specific version of the plugin, proceed as follows:
    > 
    > 1.  Download the [preferred version](https://github.com/cloudfoundry-incubator/multiapps-cli-plugin/releases) of the plugin that is compatible with your operating system.
    > 2.  Extract the downloaded archive if required.
    > 3.  To install the plugin, enter the following command:
    >     -   Mac and Linux: ***`cf install-plugin`*<path to the downloaded plugin\>*`-f`***
    >     -   Windows: ***`cf install-plugin`*<path to the downloaded plugin\>*`-f`***

4.  Verify that the plugin has been installed successfully by entering `cf plugins`.

    You see a list of plugins that now includes the MultiApps CLI Plugin for the Cloud Foundry command line interface. The output also displays commands that are specific to this plugin.


**Related Information**  


[SAP BTP, Cloud Foundry CLI Plugins](https://tools.hana.ondemand.com/#cloud)

[Download and Install the Cloud Foundry Command Line Interface](Download_and_Install_the_Cloud_Foundry_Command_Line_Interface_4ef907a.md "Download and set up the Cloud Foundry Command Line Interface (cf CLI) to start working with the Cloud Foundry environment.")

[MultiApps CLI Plugin](https://github.com/cloudfoundry-incubator/multiapps-cli-plugin/releases)

