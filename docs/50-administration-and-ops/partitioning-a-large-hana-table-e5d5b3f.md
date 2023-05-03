<!-- loioe5d5b3fe71614a1d8f4fc80e9c14a6cb -->

# Partitioning a Large HANA Table

Break down large columnar tables into partitions before the SAP HANA database threshold of two billion records per table is reached.



<a name="loioe5d5b3fe71614a1d8f4fc80e9c14a6cb__PartitioningLargeTables_steps"/>

## Procedure

1.  On the SAP Fiori launchpad of your ABAP environment, search for the *Partition HANA Tables* app.

2.  To search for tables that contain a large number of records, enter your search criteria.

    By default, the search criteria include the table name, the number of records, the total memory in MB and the number of partitions. If you want to include other search criteria, choose the *Adapt Filters* button.

3.  Choose the *Go* button.

    A list of tables that match the search criteria and that are eligible for partitioning is displayed, such as your own tables or tables released for partitioning by SAP. You can identify large tables in this list by checking the number of records and the total memory of the individual tables.

    > ### Note:  
    > You can add or remove columns in the list by choosing the *Settings* button.

4.  Choose the table that you want to partition and choose the *Partition Table* button.

5.  In the *Change Partitioning Schema* dialog box, select the partitioning key and enter the number of partitions that you want to create. Then choose *Partition Table*.

6.  In the *Confirm Table Partitioning* dialog box, choose *OK*.

    A background job is scheduled on the backend system that carries out the table partitioning.

7.  To check whether the job has finished and your table was partitioned successfully, refresh the list of tables by choosing the *Go* button.

    > ### Note:  
    > You can always undo the partitioning of a table by choosing a partitioned table in the list and then choosing the *Merge Partitions* button. All partitions of this table will then be merged back into one partition.


