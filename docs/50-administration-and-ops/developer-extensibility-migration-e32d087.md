<!-- loioe32d0873a742455cbdc851a0eec0e315 -->

# Developer Extensibility Migration

This task describes the developer extensibility migration process.



## Procedure

1.  Navigate to the relevant business catalog in the ABAP Development Tools \(ADT\).

2.  Check the migration status of the associated IAM apps.

3.  Verify that the Restriction Type Migration Status for each IAM app is *Migrated*.

4.  For each IAM app that isn't migrated, choose the *Migrate Restriction Types* button.

5.  In the migration wizard, complete the following steps:

    -   Choose *Next*.
    -   Select the restriction types to migrate.
    -   Choose *Next* to confirm.

    The IAM app status changes to *Migrated*.

6.  After you migrate all IAM apps, choose *Migrate Business Catalog* in the *Overview* tab.

7.  Complete the wizard by choosing *Next*, and then choose *Finish*.

    The business catalog status changes to *Migrated*.

8.  Navigate to the *Maintain Business Roles* app in the Fiori UI and verify the readiness status in the *IAM Role Migration Wizard*. For more information, see [How to Prepare for the Migration from Business Roles to IAM Roles](how-to-prepare-for-the-migration-from-business-roles-to-iam-roles-50b6899.md).

    The business catalog is now marked as *Ready*.




## Results

The associated business catalog now has the Migration Status of *Migrated*.

The IAM app now also has the Restriction Type Migration Status of *Migrated*.

The restriction types are assigned at the IAM app level.

