<!-- loio0253f4ec37e24098a5d01ad5fd882e8c -->

# Semantic Business Configuration Lock Token

When critical business configuration changes are made in a customizing tenant of the development system, a check is triggered in the test and production systems to ensure that the configurations can be changed consistently. To count as a consistent change, the new configuration must meet the following critera:

-   It doesn't violate existing configurations or business processes in the production system.
-   It can be imported into the test and production systems, offering the new or changed business processes.

If the new business configuration matches the existing configuration or application data, it generally returns either a **SUCCESS** or a **ERROR** messages. The **SUCCESS** status allows to save the business configuration in the customizing tenant of the development system. This business configuration can then be sent to the targeted test and production systems with a transport request to make the changes active. A **Semantic Business Configuration Lock Token** safeguards this verified configuration until the transport reaches the test and production systems.

This generic mechanism is defines into three phases:

1.  **Setting the Semantic Business and Configuration Locks**

    After the checks are successful in the test and production systems, a lock is saved with the status **Preliminary | On hold**. Once the configuration changes are recorded to a transport and saved in the customizing tenant of the development system, the locks will be finalized and changed from **Preliminary | On hold** to **Active** in the test and production systems.

2.  **Checking the Business Processes for existing Locks**

    When a lock is set in the test and production system, all related business processes are checked for active locks. If a business process is blocked due to an existing lock, the user receives detailed information explaining why the process could not be completed as usual.

3.  **Release of Semantic Business & Configuration Locks**

    When an active lock exists, the business processes are blocked. To release this lock, import the transport containing the critical configuration changes into the test and production systems. This import will successfully release the locks.


> ### Note:  
> Critical business configuration changes create a lock in the test and production systems, so these changes should no longer be imported into these environments. To resolve this, revert the configuration changes in the customizing tenant of the development system, and then import the transport into the test and production systems to release the locks.

