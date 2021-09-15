<!-- loio3e3ea05baa204284a3774856831a6465 -->

# Before Getting Started



<a name="loio3e3ea05baa204284a3774856831a6465__section_pnl_5f5_llb"/>

## Background Information for Print Queues

In a cloud environment, the back-end system does not have a connection to local printers in the customer's network \(no virtual private network access is available, for example\). To establish this connection, you need to create a print queue in the cloud system representing an output channel to a local printer. To do so, you have to install *SAP Cloud Print Manager for Pull Integration* in the customer's network from the *Install Additional Software* app so that the print manager can regularly check via a connection to the back-end system whether new print items are in the print queue. If this is the case, *SAP Cloud Print Manager for Pull Integration* retrieves these items and sends them to the locally configured printer. In addition to that, you need to define communication scenario `SAP_COM_0466`. For more information on the *SAP Cloud Print Manager for Pull Integration*, see [3048273](https://launchpad.support.sap.com/#/notes/3048273).

Watch the following video to learn how to get started with printing: 

**Related Information**  




