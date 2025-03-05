
# Install the Java CLI Plugin in the Cloud Foundry Environment

The Java plugin provides convenience utilities to work with Java applications deployed on Cloud Foundry.




## Prerequisites

You have installed the Cloud Foundry command line interface. See [Download and Install the Cloud Foundry Command Line Interface](download-and-install-the-cloud-foundry-command-line-interface-4ef907a.md).




## Procedure

1.  Open the command line interface or terminal.

2.  Check if a previous version is installed by using the command `cf plugins`. If the `java` is already installed, you have to uninstall it using the command `cf uninstall-plugin java`.
    
3.  To install the latest available version of the plugin, proceed as follows:

    a.  Make sure that you have the Cloud Foundry community repository in your Cloud Foundry command line interface. If it is not available there, add it by executing the following command:

        cf add-plugin-repo CF-Community https://plugins.cloudfoundry.org

    b.  To install the plugin, enter the following command:

        cf install-plugin -r CF_Community java


    > ### Note:  
    > Manual Installation if latest version is not available in the Cloud Foundry community repository
    > 
    > a.  Download the binary file for your target OS from the [latest release](https://github.com/SAP/cf-cli-java-plugin/releases/latest).
    > 
    > b.  If you've already installed the plugin and are updating it, you must first execute the cf uninstall-plugin java command.
    > 
    > c.  Install the plugin with cf install-plugin [cf-cli-java-plugin] (replace [cf-cli-java-plugin] with the actual binary name you will use, which depends on the OS you are running).

4.  Verify that the plugin has been installed successfully by entering `cf plugins`.

    You see a list of plugins that now includes the java CLI Plugin for the Cloud Foundry command line interface. The output also displays commands that are specific to this plugin.


**Related Information**  


[Download and Install the Cloud Foundry Command Line Interface](download-and-install-the-cloud-foundry-command-line-interface-4ef907a.md "Download and set up the Cloud Foundry Command Line Interface (cf CLI) to start working with the Cloud Foundry environment.")


