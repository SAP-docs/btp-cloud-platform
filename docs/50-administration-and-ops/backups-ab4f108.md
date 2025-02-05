<!-- loioab4f1086295847eda5be678ba68907e2 -->

# Backups

The ABAP environment relies on backups from SAP HANA Cloud:

-   Backups are retained up to 30 days.

-   The recovery point objective \(RPO\), which is the maximum data loss, is no more than 15 minutes.

-   Backups are stored encrypted and redundantly in different availability zones.

    > ### Note:  
    > A point-in-time recovery requires a coordinated plan between you as a customer and SAP that clarifies the target point-in-time and the target time of execution.


You can initiate a restore via a service request by using component `BC-CP-ABA`. To perform a restore, please provide the following information:

-   The ID \(GUID\) of the ABAP environment service instance

-   The target point-in-time to which the instance should be restored specified in coordinated universal time \(UTC\)

    > ### Caution:  
    > All data stored between the specified time and the time at which the service request is processed by SAP can't be retrieved.

    > ### Caution:  
    > A point-in-time recovery changes data stored in the ABAP environment service database only. Other data will not be changed, which may lead to inconsistencies with communication integration configurations or integrated services.

    > ### Restriction:  
    > In case of SAP-managed software updates that are part of scheduled maintenance, the target point-in-time can only be set after the last software update.


