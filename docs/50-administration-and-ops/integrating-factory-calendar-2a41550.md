<!-- loio2a41550e1999405b8b64a41ac7f8cf4d -->

# Integrating Factory Calendar

Learn how to integrate an ABAP Platform system with the factory calendar.



<a name="loio2a41550e1999405b8b64a41ac7f8cf4d__section_dnj_mjz_zxb"/>

## Context

This communication scenario allows you to set up a connection to the import factory calendar customizing from another ABAP client. There can be at most one source client for an ABAP tenant.



<a name="loio2a41550e1999405b8b64a41ac7f8cf4d__section_a1n_bkz_zxb"/>

## Prerequisites

You have to connect your ABAP system via RFC. To do this, follow the steps described in [3148310](https://me.sap.com/notes/3148310) or install the required support package. The following RFC-enabled function modules are called during import:

-   `SCAL_TO_FHC_MIG_COMPLETED`
-   `SCAL_READ_CUSTOMIZING`
-   `SFHC_READ_CUSTOMIZING`



<a name="loio2a41550e1999405b8b64a41ac7f8cf4d__section_gd1_zjz_zxb"/>

## Procedure

1.  Create a communication user in the*Maintain Communication Users* app. For more information, see [How to Create Communication Users](how-to-create-communication-users-0377ade.md).
2.  Create a communication system in the *Communication Systems* app. For more information, see [How to Create Communication Systems](how-to-create-communication-systems-c2234ac.md).
3.  Create a communication arrangement for the **Factory Calendar Integration** scenario \(`SAP_COM_0834`\) in the *Communication Arrangements* app. For more information, see [How to Create a Communication Arrangement](how-to-create-a-communication-arrangement-a0771f6.md).

After creating the communication arrangement, assign the business catalog `SAP_CA_BC_IC_LND_CAL_CA0_PC` **or** `SAP_CA_BC_IC_LND_CAL_CA1_PC` to schedule an application job. The application job is required to pull the data of the three related IMG activities via the connection. The check logic of the application job and the transaction prevent the scheduling and execution in clients where the selected customizing objects are not editable.

> ### Note:  
> Existing factory calendar customizing will be overwritten by the import. In case the automatic pull destination is configured, a warning is issued in the customizing maintenance UIs to prevent concurrent changes.

All changes are recorded on a task.

The source of the factory calendar depends on the migration state of the source client:

-   If the source client has not yet been migrated, the cross-client calendar will be pulled
-   If the source client has been migrated, the client-dependent calendar will be pulled

