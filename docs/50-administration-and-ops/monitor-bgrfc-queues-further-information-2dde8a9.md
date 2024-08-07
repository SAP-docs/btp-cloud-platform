<!-- loio2dde8a97130d4a9190a801e6cb63f759 -->

# Monitor bgRFC Queues: Further Information



Please note the following when using the *Monitor bgRFC Queues* app.

-   Deleting a queue or unit can be risky. If you delete a queue, the included units are automatically removed. This can cause issues in the processing because dependencies between units and queues might exist.

-   Queues and units can be stopped from the monitor. This function is only intended for analysis and not for regular operations, because it has consequences for runtime. If a queue is to be stopped, this also refers to the top unit that uses this queue. As soon as the unit is restarted, the queue is released again.

-   Transactional \(*T-Type*\) units can be displayed to check whether any errors occurred. They are listed below the *BGPF*\(Background Processing Framework\) *Inbound Destination*. To call them up, you need to click the*Standard* list entry of the relevant queue.

-   In the *Queue* table, the *Start All* and *Delete All* pushbuttons enable batch operations. When clicked, they apply their respective actions to all current entries in the table based on the filters that have been set. Therefore, if no filters are in place, all queues in the table will be affected. Conversely, if filters have been set, only those queues matching the filter criteria will be impacted. If you click one of these pushbuttons, a confirmation dialog box appears indicating the number of queues that will be impacted by the action.


