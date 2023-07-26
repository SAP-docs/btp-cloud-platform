<!-- loio210104b5fb854062b9038b4121b247bf -->

# Data Archiving

Data archiving is used to extract data from the database, write it to archive files and delete the data from the database tables.

Data archiving is needed for data volume management. Usually, you want to remove data from the database which is not needed for your daily business anymore, but needs to be retained.

*Steps to implement a data archiving solution*

1.  [Create a storage manager implementation to store the archive data to an external storage system](storage-manager-implementation-07e4335.md)
2.  [Select data and write it to archive files](select-data-and-write-it-to-archive-files-f24d613.md)
3.  [Delete data from the database](delete-data-from-the-database-c5758c7.md)
4.  [Read archived data](read-archived-data-df7f035.md)
5.  [Reload archived data into the database](reload-archived-data-into-the-database-7621fc2.md)
6.  [Create a definition for archiving an object in ADT](https://help.sap.com/docs/btp/sap-abap-development-user-guide/working-with-archiving-objects?version=Cloud)

7.  [Perform data archiving](perform-data-archiving-894f952.md)

For data archiving in ABAP Cloud the *Archive Development Kit* \( ADK\) provides released APIs or interfaces for all of these steps, which can be used in your implementation to archive content of your own tables.

