<!-- loiob4854a0ac35f43ed8116d17c9a284f08 -->

# IAM Roles

IAM roles are a new role concept that replaces business roles with improved performance and scalability through simplified design and modern frameworks. Use IAM roles to manage larger numbers of roles and more complex role definitions while migrating existing business roles during the transition period.



## General Information

The IAM role is a new role concept that gradually replaces the business role. Its simplified design and use of modern frameworks improve performance and scalability, supporting a larger number of roles and more complex role definitions.

Business roles and IAM roles coexist for several releases during the transition period. Over time, the system deprecates and eventually removes business roles. Therefore, migrate all existing business roles to the new IAM role concept during the transition phase.



## IAM Role Features and Migration Details

-   After you migrate a business role, the original business role remains available to ensure reliability and backward compatibility. However, use IAM roles for all future role maintenance activities.
-   To increase transparency and control, the system doesn't update IAM roles automatically during upgrades or transport imports. You must apply any required changes manually.
-   Transporting IAM roles is faster and more stable because you can't modify IAM roles directly in target systems. You maintain all changes exclusively in the development system.
-   You can migrate a business role to an IAM role. However, the system doesn't synchronize changes you make later in the IAM role back to the original business role.
-   IAM role authorizations are based on authorization objects and authorization fields rather than restriction types and restriction fields. During migration, the system converts business role restrictions one-to-one into the corresponding IAM role authorizations.
-   Thoroughly test all migrated IAM roles after you complete the migration process.

