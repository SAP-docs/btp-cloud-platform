<!-- loio7c6df2db6332419ea7a862191525377c -->

# Account Administration Using the SAP BTP Command Line Interface \(btp CLI\) \[Feature Set B\]

Use the SAP BTP command line interface \(btp CLI\) for all account administration tasks, such as creating or updating subaccounts, authorization management, and working with service brokers and platforms. It is an alternative to the SAP BTP cockpit for all users who like to work in a terminal or want to automate operations using scripts.

The btp CLI offers convenient features for interactive use as well as for scripting: For the interactice user, there's login via SSO, command autocompletion, as well as several interactive commands with prompts. But all commands can also be run with parameters, so the btp CLI can just as well be used for scripting. In addition, there is the `--format JSON` option to receive the results as JSON instead of text, and it exposes exit codes for the result status. You can then use the capabilities of the shell, e.g. jq, to work with the results.

For a basic tutorial about automation with btp CLI, see [Automate Account Operations with the Command Line Interface](https://developers.sap.com/tutorials/cp-cli-automate-operations.html).

> ### Note:  
> With the release of version 2.0.0 on March 25, 2021, the executable file of the CLI client was renamed from **sapcp** to **btp**. All commands remain compatible, and we will support the sapcp CLI until September 2021. However, this documentation and all examples inside refer to the **btp CLI**, and we recommend to download the latest btp CLI client from the [SAP Development Tools](https://tools.hana.ondemand.com/#cloud-btpcli) page. See [Migrating from sapcp to btp](migrating-from-sapcp-to-btp-4f1fe8d.md).

> ### Note:  
> The content in this section is only relevant for cloud management tools feature set B. For more information, see [Working with Cloud Management Tools Feature Set B in the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/8c963e83a42545e29d1b4277a287a01b.html "Enterprise accounts in SAP BTP that have access to cloud management tools feature set B, can also use the enhanced capabilities offered by feature set B with their subaccounts in the Neo environment.") :arrow_upper_right: and [Cloud Management Tools - Feature Set Overview](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/caf4e4e23aef4666ad8f125af393dfb2.html).



<a name="loio7c6df2db6332419ea7a862191525377c__section_ihd_xcc_mkb"/>

## Learn How to Work With the btp CLI

Learn how to use the client:

-   [Download and Start Using the btp CLI Client](download-and-start-using-the-btp-cli-client-8a8f17f.md)

-   [Set the Default Command Context](set-the-default-command-context-720645a.md)


Apart from reading the documentation, you can also check out the [Get Started with btp CLI](https://developers.sap.com/tutorials/cp-sapcp-getstarted.html) tutorial.

Learn about frequent administrative tasks you can perform using the btp CLI:

-   [Working with Global Accounts, Directories, and Subaccounts Using the btp CLI](working-with-global-accounts-directories-and-subaccounts-using-the-btp-cli-85a683e.md)
-   [Setting Entitlements Using the btp CLI](setting-entitlements-using-the-btp-cli-5af849c.md)
-   [Working with Environments Using the btp CLI](working-with-environments-using-the-btp-cli-48db155.md)
-   [Working with Multitenant Applications Using the btp CLI](working-with-multitenant-applications-using-the-btp-cli-c1b0fcc.md)
-   [Managing Users and Their Authorizations Using the btp CLI](managing-users-and-their-authorizations-using-the-btp-cli-94bb593.md)
-   [Working With Resources of the SAP Service Manager Using the btp CLI](working-with-resources-of-the-sap-service-manager-using-the-btp-cli-fe6a53b.md)



<a name="loio7c6df2db6332419ea7a862191525377c__section_lk5_xjg_qjb"/>

## How the btp CLI Works

 ![](images/Overview_of_CLI_for_SAP_BTP_3a71aa7.png) 

You download the btp CLI client to your local desktop and access it through the shell of your operating system. The client then accesses all required platform services through its backend, the CLI server, where the command definitions are stored. The CLI server delegates authentication and authorization to the authorization server, and forwards trust to the platform services, which then take care of authorization at the execution of each command.



<a name="loio7c6df2db6332419ea7a862191525377c__section_tfh_g23_xlb"/>

## Setting up a Global Account via the Command Line

The btp CLI is an alternative to the SAP BTP cockpit that lets you carry out all account administration tasks on global account, directory, and subaccount level via the command line. If you go down the hierarchy starting with the global account, the last task in the btp CLI is to create environment instances \(for example, a Cloud Foundry org\). From here on, you need the cf CLI if you want to stay in the command line.

See the following workflows to learn how to set up a global account with the CLIs, see:

-   Step-by-step instructions for manual setup:

    -   [Setting Up a Trial Account via the Command Line \[Feature Set B\]](../20-getting-started/setting-up-a-trial-account-via-the-command-line-feature-set-b-a21360f.md)

    -   For enterprise accounts: [Setting Up a Global Account via the Command Line \[Feature Set B\]](../20-getting-started/setting-up-a-global-account-via-the-command-line-feature-set-b-accd5b2.md)


-   Learn how to automate the global account setup: [Automate Account Operations with the Command Line Interface](https://developers.sap.com/tutorials/cp-cli-automate-operations.html)




**Related Information**  


[Download and Start Using the btp CLI Client](download-and-start-using-the-btp-cli-client-8a8f17f.md "To use the SAP BTP command line interface (btp CLI), you need to download the client first.")

[Command Syntax of the btp CLI](command-syntax-of-the-btp-cli-69606f4.md "Each command consists of the base call btp followed by a verb (the action), a combination of group and object, and parameters.")

[Log in](log-in-e241b30.md "Log in with the btp CLI is on global account level.")

[Set the Default Command Context](set-the-default-command-context-720645a.md "Change the default context for all command calls to the global account, a directory, or a subaccount by using the btp target command.")

[Commands in the btp CLI](commands-in-the-btp-cli-a03a555.md "A list of all tasks and respective commands that are available in the SAP BTP command line interface (btp CLI).")

[Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

