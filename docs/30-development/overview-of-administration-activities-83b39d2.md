<!-- loio83b39d21b4694bd88d07ad9564d41f6e -->

# Overview of Administration Activities

Get an overview of the example used in this documentation and what kind of administration activities you need to expect and why.



<a name="loio83b39d21b4694bd88d07ad9564d41f6e__section_arf_pn3_v2b"/>

## Example Scenario Used in This Documentation

In the example scenario used in this documentation, developers want to make an outbound service call from the ABAP environment to SAP S/4HANA Cloud, using an SAP S/4HANA service to create a business partner.

When an outbound service call in the ABAP environment is implemented, the following authentication methods can be used to authenticate at the SAP S4/HANA cloud system:

-   User ID and password \(basic authentication\)

-   OAuth 2.0


In this example scenario, OAuth 2.0 authentication is used.



<a name="loio83b39d21b4694bd88d07ad9564d41f6e__section_pjp_4rn_v2b"/>

## Overview of Administration Activities

As an administrator, your main task is to establish a trust relationship between the communication partners, the ABAP environment and SAP S/4HANA Cloud. You establish this trust relationship by creating several communication management artifacts in SAP S/4HANA Cloud. At the same time, you have to configure a destination on SAP BTP.

Most of the administrative steps can be performed automatically by using the SAP S/4HANA Cloud Extensibility service on SAP BTP. This is the recommended option, as it simplifies the process and reduces the possibility of human error. However, you can also perform all the steps manually. In the following sections, both options are described.



<a name="loio83b39d21b4694bd88d07ad9564d41f6e__section_w52_fwp_ssb"/>

## Next Step for Developers

After you have completed the integration of the ABAP environment with SAP S/4HANA Cloud, developers can start implementing their services. For more information about the next steps of the developers and additional resources, see [Implementing an Outbound Service Call to SAP S/4HANA Cloud](implementing-an-outbound-service-call-to-sap-s-4hana-cloud-a4e21bd.md).



<a name="loio83b39d21b4694bd88d07ad9564d41f6e__section_fxw_bl4_v2b"/>

## More Information

To learn more about how to use communication management apps in SAP S4/HANA systems to integrate with other systems, see [Communication Management](https://help.sap.com/viewer/0f69f8fb28ac4bf48d2b57b9637e81fa/latest/en-US/56cf82e75f2a42de827b5dc30e48db64.html).

For more information about available services in SAP S/4HANA Cloud that can be consumed by external systems, search for services on the SAP API Business Hub at [http://api.sap.com](http://api.sap.com) or follow this [direct link](https://api.sap.com/package/SAPS4HANACloud?section=Artifacts).

To find out how to consume services offered as part of SAP S/4HANA Cloud or other SAP products, see [API Management](https://help.sap.com/viewer/66d066d903c2473f81ec33acfe2ccdb4/Cloud/en-US/adcbc07b031b4ac285b22867a1216306.html).

