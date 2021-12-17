<!-- loio4c1bf988d60e49bf95a488f5ec18f2b4 -->

# Restore Configuration Settings After an Instance Refresh

After an instance refresh, you must restore some of your extension integration artifacts and configuration settings for the SAP SuccessFactors target company.



## Prerequisites

-   You have a dedicated SAP SuccessFactors company instance.
-   You have a registered SAP SuccessFactors system in your global account in SAP BTP.
-   You have performed the instance refresh with the *Instance Refresh* tool or your cloud operators have performed an instance refresh manually.



## Context

In SAP SuccessFactors, instance refresh is a procedure in which the data and the settings of a source company instance are copied into another company instance. During the instance refresh the data of the target company instance is deleted and replaced by the data of the source company instance. Therefore, after an instance refresh, if the target company has been integrated with a global account in SAP BTP, the extension integration configuration settings and artifacts in the target company are overwritten by the configuration settings and data coming from the source company.

You can trigger the instance refresh automatically with the *Instance Refresh* tool or your cloud operators can trigger it manually.

If you have performed an instance refresh with the *Instance Refresh* tool, the OAuth clients, and the Assertion Consumer Services \(ACS\) created by the cloud platform are recreated. In *Provisioning*, the *Extension Management Configuration* page displays the integration details for the target system.

> ### Note:  
> The OAuth clients are assigned new IDs. This does not affect the configuration settings.

However, if you have the following artifacts, you must reconfigure them in the SAP SuccessFactors target company instance:

-   Custom home page tiles

-   Permission roles

-   Permission groups


> ### Note:  
> After a manual instance refreshed, no artifacts are reconfigured. If you want to restore the integration settings for the target company instance, you need to recreate the *SAP SuccessFactors Extensibility* service instance.



## Procedure

1.  To restore the configuration settings after an instance refresh, proceed as follows:

    -   After an automated instance refresh:
        1.  If you have configured custom home page tiles in the target company instance, reconfigure them. See [Custom Home Page Tiles](https://help.sap.com/viewer/59f821da545a4bdb94f1eb8fa22e4b36/latest/en-US/82a5f1bc52854218a4d0078b6acfbbcb.html).
        2.  If you have configured permission roles and permission groups, you need to reconfigure them. See [What Are Role-Based Permissions?](https://help.sap.com/viewer/b569eee64d3f4159b2b5272ba7d6b127/latest/en-US/b95c4a4e43aa48d4a962f6b6e878d3a9.html).


    -   After a manual instance refresh:
        1.  For SAP SuccessFactors, Second Half 2021 Release or later, proceed as follows:

            1.  Recreate the *SAP SuccessFactors Extensibility* service instance. See [Create a Service Instance to Consume the SAP SuccessFactors HXM Suite OData API](create-a-service-instance-to-consume-the-sap-successfactors-hxm-suite-odata-api-46c5ea1.md).

            2.  If you have configured permission roles and permission groups, you need to reconfigure them. See [Custom Home Page Tiles](https://help.sap.com/viewer/59f821da545a4bdb94f1eb8fa22e4b36/latest/en-US/82a5f1bc52854218a4d0078b6acfbbcb.html).

            3.  Reconfigure the permission roles and permission groups. See [What Are Role-Based Permissions?](https://help.sap.com/viewer/b569eee64d3f4159b2b5272ba7d6b127/latest/en-US/b95c4a4e43aa48d4a962f6b6e878d3a9.html).







## Results

You have restored the extension integration artifacts and configuration setting of the target company instance.

