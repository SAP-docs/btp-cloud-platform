<!-- loio50b6899b7f254794b75d9e036a6e0b63 -->

# How to Prepare for the Migration from Business Roles to IAM Roles



## Context

The migration from business roles to IAM roles is introduced in two phases:

-   *Key User Extensibility Migration*

-   *Developer Extensibility Migration*


> ### Note:  
> Key user extensibility migration is not yet available and will be delivered with a later release.

The following steps describe how the migration process will work once it becomes available.



## Procedure

1.  Open the *Maintain Business Roles* app.

2.  Select the business roles you want to migrate.

3.  Choose *Migrate* and select one of the following options:

    -   *Migrate Selected* to migrate only the roles you have selected
    -   *Migrate All* to migrate all roles

4.  The *IAM Role Migration Wizard* opens.

    > ### Note:  
    > This wizard is currently for information purposes only and does not execute the migration process. The guidelines below describe the steps that can be performed in the future.

5.  In *Step 1: General Information*, review the migration concept.

6.  Choose *Next*.

7.  In *Step 2: Related Objects*, review the selected roles and their related objects.

8.  Choose *Next*.

9.  In *Step 3: Pre-Requisites Check*, review the *Business Role Readiness* status.

    -   *Ready*: No action required.
    -   *Action Required*: Additional steps are necessary. Select the status to display the migration readiness details.

10. Proceed as follows:

    -   Choose *Next* if no action is required.
    -   If the status indicates that a business catalog needs to be migrated, continue with the [Developer Extensibility Migration](developer-extensibility-migration-e32d087.md).

11. In *Step 4: Summary*, review the migration summary.

12. Choose *Migrate* to complete the migration.

    > ### Caution:  
    > This option will be available in a future release.




## Results

Business roles are prepared for migration to IAM roles once the feature becomes available.

**Related Information**  


[Key User Extensibility Migration](key-user-extensibility-migration-64ae629.md "This task describes upcoming support for key user extensibility migration.")

[Developer Extensibility Migration](developer-extensibility-migration-e32d087.md "This task describes the developer extensibility migration process.")

