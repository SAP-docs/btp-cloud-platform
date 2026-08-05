<!-- loioe32d0873a742455cbdc851a0eec0e315 -->

# Developer Extensibility Migration

This task describes developer extensibility migration.



## Procedure

1.  Navigate to *Identity and Access Management* in your system in ABAP Development Tools \(ADT\)

2.  Locate the relevant business catalog and check the migration status of its associated IAM apps.

3.  For each IAM app that is not yet migrated, choose *Migrate IAM App*.

4.  In the migration wizard:

    -   Choose *Next*
    -   Select the restriction types to migrate
    -   Choose *Next* to confirm

    The IAM app status changes to *Migrated*.

5.  After all IAM apps are migrated, choose *Migrate Business Catalog*.

6.  Complete the wizard by choosing *Next* and then *Finish*.

    The business catalog status changes to *Migrated*.

7.  Navigate to the *Maintain Business Roles* app and recheck the readiness status in the *IAM Role Migration Wizard*. See, [Key User Extensibility Migration](key-user-extensibility-migration-64ae629.md).

    The business catalog should now be marked as *Ready*.




## Results

The selected business roles are migrated to IAM roles. Associated IAM apps and business catalogs are also migrated, and restriction types are assigned at the IAM app level.

