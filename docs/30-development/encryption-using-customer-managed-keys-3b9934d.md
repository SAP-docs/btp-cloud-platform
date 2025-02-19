<!-- loio3b9934dae7e84984ae78fc914d730088 -->

# Encryption Using Customer-Managed Keys

You can secure your SAP data with your own customer-managed key \(CMK\) using SAP Data Custodian.

Integrating SAP Data Custodian with the HTML5 Application Repository service allows you to encrypt HTML5 application files and credentials stored in the HTML5 application repository using your own customer-managed key \(CMK\). For more information about customer-managed keys, see .[What is Key Management Service?](https://help.sap.com/docs/sap-data-custodian/key-management-service/what-is-key-management-service-page?version=LATEST).



<a name="loio3b9934dae7e84984ae78fc914d730088__section_zcr_f31_h2c"/>

## Enabling CMK Encryption for a New Instance of the HTML5 Application Repository Service

To enable the CMK for the HTML5 Application Repository, include a configuration file \(for example, `config.json`\) with the configuration `"enableCmk": true` when you create or update an HTML5 Application Repository service instance of the app-host service plan. For example:

> ### Sample Code:  
> ```
> cf create-service html5-apps-repo app-host -c config.json
> ```

The `config.json` file must contain:

> ### Sample Code:  
> ```
> {
>     "enableCmk": true 
> }
> 
> ```



<a name="loio3b9934dae7e84984ae78fc914d730088__section_bsz_f31_h2c"/>

## Enabling CMK Encryption for an Existing HTML5 Application Repository Service Instance

To enable CMK for an existing HTML5 Application Repository service instance, update the configuration file for the service instance to include the parameter `"enableCmk": true`.

Then redeploy the application content to the app-host service instance.



<a name="loio3b9934dae7e84984ae78fc914d730088__section_x4h_g31_h2c"/>

## Disabling CMK Encryption for an HTML5 Application Repository Service Instance

To disable the CMK for your HMTL5 Application Repository service instance, set the enableCmk parameter in the instance configuration file to false \(`"enableCmk": false`\).

Then redeploy the application content to the app-host service instance.

