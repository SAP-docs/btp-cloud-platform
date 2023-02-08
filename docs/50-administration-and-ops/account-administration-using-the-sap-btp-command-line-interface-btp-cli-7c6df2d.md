<!-- loio7c6df2db6332419ea7a862191525377c -->

# Account Administration Using the SAP BTP Command Line Interface \(btp CLI\)

Use the SAP BTP command line interface \(btp CLI\) for all account administration tasks, such as creating or updating subaccounts, authorization management, and working with service brokers and platforms. It is an alternative to the SAP BTP cockpit for all users who like to work in a terminal or want to automate operations using scripts.

The btp CLI offers convenient features for interactive use as well as for scripting: For the interactice user, there's login via SSO, command autocompletion, as well as several interactive commands with prompts. But all commands can also be run with parameters, so the btp CLI can just as well be used for scripting. In addition, there is the `--format JSON` option to receive the results as JSON instead of text, and it exposes exit codes for the result status. You can then use the capabilities of the shell, e.g. jq, to work with the results.

> ### Note:  
> The content in this section is only relevant for cloud management tools feature set B. For more information, see [Working with Cloud Management Tools Feature Set B in the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/8c963e83a42545e29d1b4277a287a01b.html "Enterprise accounts in SAP BTP that have access to cloud management tools feature set B, can also use the enhanced capabilities offered by feature set B with their subaccounts in the Neo environment.") :arrow_upper_right: and [Cloud Management Tools - Feature Set Overview](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/caf4e4e23aef4666ad8f125af393dfb2.html).



<a name="loio7c6df2db6332419ea7a862191525377c__section_nc4_bpf_15b"/>

## Documentation

In this documentation, you learn how to download, install, update, and use the btp CLI. Additionally, see the following:

-   [btp CLI Command Reference](https://help.sap.com/docs/BTP/btp-cli/intro.html)

-   [Get Started with the SAP BTP Command Line Interface \(btp CLI\)](https://developers.sap.com/tutorials/cp-sapcp-getstarted.html)

-   [Automate Account Operations with the Command Line Interface](https://developers.sap.com/tutorials/cp-cli-automate-operations.html)

-   [Setting Up a Global Account via the Command Line \[Feature Set B\]](../20-getting-started/setting-up-a-global-account-via-the-command-line-feature-set-b-accd5b2.md)

-   Access command help from the terminal with `btp help`




<a name="loio7c6df2db6332419ea7a862191525377c__section_lk5_xjg_qjb"/>

## How the btp CLI Works

 ![](images/Overview_of_CLI_for_SAP_BTP_3a71aa7.png) 

You download the btp CLI client to your local desktop and access it through the shell of your operating system. The client then accesses all required platform services through its backend, the CLI server, where the command definitions are stored. The CLI server delegates authentication and authorization to the authorization server, and forwards trust to the platform services, which then take care of authorization at the execution of each command.

**Related Information**  


[btp CLI Command Reference](https://help.sap.com/docs/BTP/btp-cli/intro.html)

