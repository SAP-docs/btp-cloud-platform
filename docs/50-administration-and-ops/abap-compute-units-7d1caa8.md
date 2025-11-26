<!-- loio7d1caa87c4b34366a7cf1b00a93199e2 -->

# ABAP Compute Units

ABAP Compute Units \(ACUs\) represent the runtime size in an SAP BTP ABAP environment. Each ABAP Compute Unit comprises 16 GB of memory and approximately four virtual CPUs \(vCPUs\).

For availability reasons, we recommend using more instances instead of larger ones. However, large servers are more efficient when usage is constantly high, such as in multi-tenancy systems. Multi-tenancy systems consume more resources for runtime \(ACU\) and persistence \(HANA Compute Units, HCUs\).

The minimum number of ACUs and HCUs depends on the number of tenants. For every 100 tenants, at least one ACU and two HCUs are required.

The maximum number of ACUs is limited by:

-   Twice the number of HCUs

-   32 times the size of application servers \(0.5 or 2 ACUs\)


The memory limit for a single session is 4 GB, regardless of the application server size.

