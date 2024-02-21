<!-- loioed3e22de359d4955a51c9164da1315ff -->

# Creating Print Queues

You want to set up print queues to manage the printing of documents.



## Procedure

1.  Open the *Maintain Print Queues* app.

2.  Click *New* to create a new print queue.

3.  Select a print manager.

4.  Enter the required information:

    -   **Queue**: Print queue name

    -   **Description**: Print queue desciption
    -   **Format**: The format is the printer language type of the queue. The following language types are available: `PDF, CAB 203 dpi, CAB 300 dpi, Datamax 203dpi, Datamax 300 dpi, Datamax 406 dpi, Datamax 600 dpi, HP Laserjet 4350 PCL 5e, HP LaserJet 4350 PS, PCL 5c (Color), PCL 5e (Monochrome), Intermec 203 dpi, Intermec 300 dpi, Intermec 400 dpi, Lexmark T644 PCL 5e, Lexmark T644 PS, PostScript 2, Postscript 3, Toshiba 203 dpi, Toshiba 305 dpi, XMLDATA, Zebra 203 dpi, Zebra 300 dpi, Zebra 600 dpi.`
    -   **Communication User**: Technical user with which the *SAP Cloud Print Manager for Pull Integration* logs on to the system. You have to define a communication user in the communication scenario `SAP_COM_0466` first. You can connect several queues to the same *SAP Cloud Print Manager for Pull Integration* - in this case all queues must use the same communication user.
    -   **Retention**: Spool Retention Period. The retention period is the number of days after which the print queue items that are in final state \(*successful* or *failed*\) will be deleted automatically.

5.  Click *Create* to create a new print queue.




<a name="loioed3e22de359d4955a51c9164da1315ff__result_k4w_py1_cjb"/>

## Results

You have created a print queue you can use in the *SAP Cloud Print Manager for Pull Integration*.

> ### Note:  
> The *Maintain Print Queues* app always includes a print queue called *DEFAULT*. It’s the only print queue provided by SAP and serves as a sample queue that can't be used for productive output as it can’t be connected to the *SAP Cloud Print Manager for Pull Integration*.
> 
> To connect to your physical printers, you therefore need to create one or more custom print queues.
> 
> Keep in mind that you can't define custom retention time for items in the *DEFAULT* queue and that SAP might adapt the standard retention time at any time to avoid misuse. The *DEFAULT* print queue should also not be used as storage for all documents that are printed from the system, as SAP might restrict the given quota at any time to avoid misuse. A cleanup job will delete all items in the *DEFAULT* print queue after eight days, regardless of their status. This will not affect the behavior of other print queues.

**Related Information**  


 <?sap-ot O2O class="- topic/link " href="d07a4297e776446e898f2b27532f63c6.xml" text="" desc="" xtrc="link:1" xtrf="file:/home/builder/src/dita-all/jjq1673438782153/loio2080d0faf9d84ce6aa14caa4caa32935_en-US/src/content/localization/en-us/ed3e22de359d4955a51c9164da1315ff.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 

