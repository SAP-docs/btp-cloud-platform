<!-- loioa4c7b148a9ab4341b876574fd54c0a18 -->

# Configuring a Solution Manually

You can configure the multitenant application manually, which allows you to finetune your solution beyond the options offered in the *Maintain Solution*app. In this case, you must configure the individual project files and deploy the project using the corresponding command line tools.

In the following sections, the general steps are described. For a description of multitenant applications in general and more detailed configuration options, see [Multitenant Applications](multitenant-applications-195031f.md).



<a name="loioa4c7b148a9ab4341b876574fd54c0a18__section_xhz_n15_4zb"/>

## Configure the solution

It is recommended that you initially configure your solution using the Maintain Solution app and then use the Download functionality to obtain the application descriptor file. Since the download is available on deployment configuration level, it is necessary to create both a solution and a deployment configuration.

Follow the steps detailed in Using the Maintain Solution app \(see [Order and Provide](order-and-provide-975bd3e.md)\), creating both the solution and the deployment configuration for the test phase. Once configured, use the Download function to obtain the application descriptor. Finally, clone the reference solution linked below and replace the standard descriptor with the generated one. This results in a project that is already configured, making it the perfect starting point to implement your modifications.

The reference solution provided by SAP can be found here: [GitHub - sap-software/abap-saas-reference-solution: Template of an ABAP SaaS Reference Solution allowing the SAP Partner to deploy a solution containing approuter and XSUAA dependencies](https://github.com/sap-software/abap-saas-reference-solution).

> ### Note:  
> gCTS Delivery: If you use gCTS instead of add-ons for the delivery of software components to production systems, the value for the add-on product name in the application descriptor has to be empty. See [Delivery via Add-On or gCTS](delivery-via-add-on-or-gcts-438d7eb.md).



<a name="loioa4c7b148a9ab4341b876574fd54c0a18__section_es1_w15_4zb"/>

## Deploy the solution for test purposes

After configuring the multitenant application, it is recommended to perform a test deployment to validate the subscription process.

Your project should already have the correct deployment configuration, as you maintained this in the Maintain Solution app before generating the application descriptor. As a result, you can directly build and deploy your project.

Use the [Cloud MTA Build Tool](https://sap.github.io/cloud-mta-build-tool/)and the[Cloud Foundry CLI](https://docs.cloudfoundry.org/cf-cli/install-go-cli.html).

Once deployed, your solution should appear in the service marketplace on SAP BTP Cockpit for subaccounts within your global account for development.



<a name="loioa4c7b148a9ab4341b876574fd54c0a18__section_ufj_z15_4zb"/>

## Test the solution

You can test the multitenant application by subscribing from a consumer subaccount created in the global account for development. See [Subscribe to Multitenant Applications Using the Cockpit](https://help.sap.com/docs/btp/sap-business-technology-platform/subscribe-to-multitenant-applications-using-cockpit?version=Cloud).

Once the subscription is successful, you may also want to test the initial user onboarding process. First, assign the onboarding role collection, which includes the SolutionAdmin role, to your user. Afterwards, access the application via the consumer subaccount and trigger the user onboarding. For more details, please see the section on the [Initial User Onboarding](initial-user-onboarding-4a9c501.md).



<a name="loioa4c7b148a9ab4341b876574fd54c0a18__section_zpr_cb5_4zb"/>

## Deploy the solution for production purposes

After successfully testing the subscription process, you can proceed to a production deployment of your solution.

You can use MTA extension descriptors to configure the required values for deployment to different targets. This allows you to deploy the same project to different subaccounts. See [Multitenant Applications](multitenant-applications-195031f.md).

Build and then deploy your project. Once deployed, your solution should appear in the service marketplace on SAP BTP Cockpit for subaccounts within your global account for production.

