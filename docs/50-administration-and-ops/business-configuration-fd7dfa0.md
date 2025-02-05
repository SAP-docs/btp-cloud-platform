<!-- loiofd7dfa034dec4016b46219300d61cb71 -->

# Business Configuration

Find out which lifecycle management tasks a business process configuration expert \(business role `SAP_BPC_EXPERT`\) needs to perform for the administration of business configurations.



<a name="loiofd7dfa034dec4016b46219300d61cb71__section_c1w_yn5_ysb"/>

## Context

Business configuration is the customization of business applications. In enterprise software, business configuration refers to a predefined set of configuration options that affect its functionality and behavior. You can maintain custom business configuration content in your`SAP BTP ABAP Environment` to enrich your extensibility scenarios. This includes both functionalities provided by SAP and custom business configuration objects developed using `ABAP Development Tools` \(ADT\).

If you're looking for more information on how to implement custom business configuration objects, please refer to [Custom Business Configurations App](custom-business-configurations-app-76384d8.md).



<a name="loiofd7dfa034dec4016b46219300d61cb71__section_eps_t45_ysb"/>

## Requirements

The administration of your business configuration has the following requirements:

-   The business configuration is client-dependent. After import, it's only available in the client where the import took place. In contrast, development objects are not client-dependent.

-   Business configuration content is usually not directly maintained in a productive system, but created in a development system, and then transported to the test system and productive system. For more information on how to set up your system landscape, please refer to the scenarios described in [Setting Up and Working with Your Landscape](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/latest/en-US/9a6fe7edf77a4f1299254c1c3c8bad48.html).

-   Changes to business configuration content are recorded onto transport requests of the type `Customizing`. They can be released in the source system and imported in any target system. For more information on how to set up a suitable software component for transport, please refer to [Software Components](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/58480f43e0b64de782196922bc5f1ca0.html?version=Cloud).




<a name="loiofd7dfa034dec4016b46219300d61cb71__section_vky_fr5_ysb"/>

## Procedure

You as a business process configuration expert are responsible for the lifecycle management of business configuration content. First, you need to create transport requests of the type `Customizing` that contain corresponding transport tasks. Once a suitable transport task has been assigned, you can proceed with the creation and adjustment of content. When the content is ready, the transport tasks and the transport requests can be released. The changes will be written to the remote repository corresponding to the software component that was used for transport. The content can then be imported into target systems simply by pulling the changes for the software component that was used. This procedure is valid regardless of the specific landscape setup or whether software components of the type `Development` or `Business Configuration` are used.

> ### Note:  
> It's possible to maintain local business configuration changes which can't be transported to other systems. If no software component of the type `Business Configuration` is cloned in the source system, you can still create a customizing transport request in the *Export Customizing Transports* app. This request will have no target. It can be used to record business configuration changes, but its release will have no effect.

The following sections will introduce the applications needed for both the maintenance and lifecycle management of business configuration content.

