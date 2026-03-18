<!-- loio25a6d53d8b0b4846a58a85fac39eb1f3 -->

# Resilience of an ABAP Environment System

Learn about the resilience features that are provided to all ABAP Cloud applications built on the SAP BTP ABAP environment.

Instances deployed to the SAP BTP ABAP environment without the multi-availability zone option receive the following resilience features:

-   The components of a single ABAP system and the corresponding SAP HANA Cloud database preferably run together inside the same availability zone of a region.

-   Automated monitoring and restart of services in case of failures is ensured for the ABAP system components and the SAP HANA Cloud database.

-   A restart usually happens within minutes if hardware is available. A restarted ABAP application server still needs some more minutes to warm up before it can serve traffic.

-   In case of failures, components are restarted on other hardware \(subject to availability\).

-   Enqueue locks are stored redundantly.


With the multi-availability zone option for an ABAP environment system inside a region, the following additional features apply:

-   The application servers for ABAP are distributed across the availability zones inside the region, in a round-robin fashion.

-   Two instances of the SAP HANA Cloud database will be set up in different availability zones and configured with synchronous and transaction-safe data replication. This is covered with the multizone synchronous replication feature of the SAP HANA Cloud service.

-   In case of failures, the ABAP system components are restarted on other hardware with higher priority than components of systems without the multi-availability zone option.

-   In most cases, the underlying infrastructure handles outages of components automatically and restarts them on functional hardware within minutes.

-   In severe cases, like complete availability zone outages, a fully automatic outage handling can't be guaranteed. For such cases, a manual declaration of a zone outage by SAP's operations team will lead to the evacuation of the defective zone and will bring up the system with the multi-availability zone option in the remaining zones, within the limits of hardware availability.

-   In case of database-related failures, a takeover to the secondary database instance takes place automatically, and the application servers for ABAP reconnect to the secondary database instance.

-   The multi-zone option doesn't affect the costs for the ABAP runtime: the consumed ABAP Compute Units \(ACUs\) don't change compared to a system without the multi-availability zone option.

-   The second database instance affects the costs for the ABAP persistence: the consumed HANA Compute Units \(HCUs\) increase by factor 2.


> ### Note:  
> The multi-availability zone option is based on the principles of the multi-availability zone architecture for SAP BTP *In-Metro Disaster Recovery* as described in [Resilience, High Availability, and Disaster Recovery](https://help.sap.com/docs/btp/sap-business-technology-platform/resilience-high-availability-and-disaster-recovery?version=Cloud).

> ### Tip:  
> The distribution of ABAP application servers across multiple availability zones requires at least two application servers. For example: with application servers of the size 0.5 ACU, the minimum *Total ABAP runtime size* is 1 ACU. A more resilient setup requires a minimum of three ABAP application servers. This configuration ensures that at least two servers remain running if one availability zone fails. For example: with 0.5 ACU servers, in this case, the minimum *Total ABAP runtime size* would be 1.5 ACU, and with 2 ACU servers, the minimum *Total ABAP runtime size* would be 6 ACU.
> 
> An exception is the SAP Cloud Infrastructure region `eu01`, which currently has only two availability zones. If you want at least two servers to remain running in the event of an availability zone failure, you need at least four application servers. For example, with 0.5 ACU servers, this corresponds to a minimum *Total ABAP runtime size* of 2 ACUs.

> ### Note:  
> The multi-availability zone option does not reduce the technical downtime for upgrades or updates and hotfix collection imports.

> ### Note:  
> SAP BTP ABAP environment provides protection against denial-of-service attacks via various defense mechanisms. These are continuously improved to keep a decent protection level. However, a full protection against DoS attacks can't be guaranteed.

**Related Information**  


[SAP HANA Database Availability Zone and Replicas](https://help.sap.com/docs/hana-cloud/sap-hana-cloud-administration-guide/sap-hana-database-availability-zone-and-replicas)

[Resilience, High Availability, and Disaster Recovery](https://help.sap.com/docs/btp/sap-business-technology-platform/resilience-high-availability-and-disaster-recovery?version=Cloud)

