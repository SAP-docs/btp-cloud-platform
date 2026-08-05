<!-- loioe7d35d304517471c9f6d951ea526cd7e -->

# Monitor bgRFC Queues



With this app you can monitor the bgRFC \(background RFC\) queues together with the associated units and inbound destinations. As well as displaying queues and units that belong to a destination, the app provides you with functions that let you intervene in their processing, such as *Stop*, *Start*, or *Delete*.



Please note the following when using the *Monitor bgRFC Queues* app.

-   Deleting a queue or unit can be risky. If you delete a queue, the included units are automatically removed. This can cause issues in the processing because dependencies between units and queues might exist.

-   Queues and units can be stopped from the monitor. This function is only intended for analysis and not for regular operations, because it has consequences for runtime. If a queue is to be stopped, this also refers to the top unit that uses this queue. As soon as the unit is restarted, the queue is released again.

-   Transactional \(*T-Type*\) units can be displayed to check whether any errors occurred. They are listed below the *BGPF*\(Background Processing Framework\) *Inbound Destination*. To call them up, you need to click the*Standard* list entry of the relevant queue.

-   In the *Queue* table, the *Start All* and *Delete All* pushbuttons enable batch operations. When clicked, they apply their respective actions to all current entries in the table based on the filters that have been set. Therefore, if no filters are in place, all queues in the table will be affected. Conversely, if filters have been set, only those queues matching the filter criteria will be impacted. If you click one of these pushbuttons, a confirmation dialog box appears indicating the number of queues that will be impacted by the action.




## Key Features

You can use this app to:



-   Save units with errors for later analysis to move them into a separate a queue and execute the blocked units in this queue that were waiting to be processed.

    > ### Caution:  
    > We recommend that you use this feature with caution and process only the units that are independent from the one with errors, for example, units for sales orders with multiple line items.

-   Stop and start destinations, queues, units

-   Delete queues and units if they are no longer needed

-   Check for errors

-   Display the first function module for each unit
-   Navigate to Message Monitoring to view more details if required



<a name="loioe7d35d304517471c9f6d951ea526cd7e__supported_devices"/>

## Supported Device Types

-   Desktop

-   Tablet




<a name="loioe7d35d304517471c9f6d951ea526cd7e__customer_component"/>

## Component for Customer Incidents

If you need support or experience issues, please report an incident under component `BC-SRV-APS-COM`.

**Related Information**  


 <?sap-ot O2O class="- topic/link " href="0b09dce4a2354c23b833e746cb2695d7.xml" text="" desc="" xtrc="link:1" xtrf="file:/home/builder/src/dita-all/jjq1673438782153/loio2080d0faf9d84ce6aa14caa4caa32935_en-US/src/content/localization/en-us/e7d35d304517471c9f6d951ea526cd7e.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 

