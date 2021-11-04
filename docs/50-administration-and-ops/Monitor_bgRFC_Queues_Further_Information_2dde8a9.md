<!-- loio2dde8a97130d4a9190a801e6cb63f759 -->

# Monitor bgRFC Queues: Further Information



Please note the following when using the *Monitor bgRFC Queues* app.

-   Deleting a queue or unit can be risky. If you delete a queue, the included units are automatically removed. This can cause issues in the processing because dependencies between units and queues might exist.

-   Queues and units can be stopped from the monitor. This function is only intended for analysis and not for regular operations, because it has consequences for runtime. If a queue is to be stopped, this also refers to the top unit that uses this queue. As soon as the unit is restarted, the queue is released again.


