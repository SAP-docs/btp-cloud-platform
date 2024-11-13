<!-- loio3e3ea05baa204284a3774856831a6465 -->

# Before Getting Started



<a name="loio3e3ea05baa204284a3774856831a6465__section_pnl_5f5_llb"/>

## Background Information for Print Queues

In a Cloud environment, the back-end system does not have a connection to local printers in your network \(no virtual private network access is available, for example\). To establish this connection, you need to create a print queue in the Cloud system representing an output channel to a local printer. To do so, open the *Install Additional Software* app and install the `SAP Cloud Print Manager for Pull Integration` \(hereafter abbreviated as CPM\) in your network. The CPM can then regularly check whether new print items are in the print queue. If this is the case, the CPM retrieves these items and sends them to the locally configured printer. In addition to that, you need to define communication scenario `SAP_COM_0466`. For more information on the CPM, see [3048273](https://me.sap.com/notes/3048273) or [Working with the SAP Cloud Print Manager for Pull Integration](working-with-the-sap-cloud-print-manager-for-pull-integration-964486f.md).

Watch the following video to learn how to get started with printing: 

**Related Information**  


[SAP\_COM\_0466 \(SAP S/4HANA Cloud\)](https://help.sap.com/docs/SAP_S4HANA_CLOUD/0f69f8fb28ac4bf48d2b57b9637e81fa/d07a4297e776446e898f2b27532f63c6.html)

[SAP\_COM\_0466 \(SAP BTP ABAP Environment\)](https://help.sap.com/docs/btp/sap-business-technology-platform/sap-com-0466?version=Cloud)

