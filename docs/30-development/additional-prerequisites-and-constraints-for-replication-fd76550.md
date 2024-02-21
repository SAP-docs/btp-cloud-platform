<!-- loiofd765505261e432d8db72a084bc6789d -->

# Additional Prerequisites and Constraints for Replication

If you want to use an SQL service for replication, additional prerequisites and contraints apply.



The following generally applies for replication using an SQL service:

-   CDS view entities with parameters can never be replicated.

-   An initial load \(complete replication of all records\) is possible without further restrictions.

-   Every CDS view entity that is used for **delta** replication must declare this intention in its header via the annotation `@DataIntegration.deltaReplication.intended: true`.


You must perform an initial load again if **all** of the following applies:

-   A table structure has been changed, which has also affected the primary key.

-   The changed primary key is used in a CDS view entity that is part of a replication scenario.


In this case, a delta replication is not sufficient, but you must re-initialize the process with a full replication of the records.

For delta replication on CDS view entities, additional constraints apply. For more information and a full list of constraints, see the Knowledge Transfer Documentation for the annotation `@DataIntegration.deltaReplication.intended: true`, which can be called up in ABAP Development Tools.

