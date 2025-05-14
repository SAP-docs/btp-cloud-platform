<!-- loioabb810d1119d4312ba1f4b91a5a9b31b -->

# Autoscaler Plugin for Cloud Foundry CLI

The Autoscaler service offers a CLI plugin for the Cloud Foundry Command Line Interface \(CLI\).

The plugin enables users to:

-   attach or detach scaling policies to apps
-   view attached scaling policies and view the scaling histories
-   view the metrics sent by apps

This is useful:

-   to get some insights into how current scaling policies work and if changes are reasonable.
-   for debugging, especially when introducing custom-metrics to scale an app. It lets you check if the sent metrics are correctly handled by the Application Autoscaler, and it helps you understand why your app is scaling out or in or why this does not happen.

This documentation explains how to use the plugin on Cloud Foundry in BTP. For details not related to BTP, see [https://github.com/cloudfoundry/app-autoscaler-cli-plugin/blob/main/README.md](https://github.com/cloudfoundry/app-autoscaler-cli-plugin/blob/main/README.md).



<a name="loioabb810d1119d4312ba1f4b91a5a9b31b__section_ads_z3v_q2c"/>

## Command List

[Cloud Foundry Commands of Application Autoscaler](cloud-foundry-commands-of-application-autoscaler-0faf8a2.md)

**Related Information**  


[Initial Setup](https://help.sap.com/viewer/7472b7d13d5d4862b2b06a730a2df086/Cloud/en-US/f3e7fa907e9d4da89fc55602818bd6f4.html "Create an instance of the Application Autoscaler service and bind it to your application. Install the Autoscaler plugin for the Cloud Foundry Command Line Interface (cf CLI).") :arrow_upper_right:

[Cloud Foundry Commands of Application Autoscaler](cloud-foundry-commands-of-application-autoscaler-0faf8a2.md "The Application Autoscaler plugin for the Cloud Foundry Command Line Interface (cf CLI) includes commands that you can use to get some insights into your scaling policies and for debugging.")

