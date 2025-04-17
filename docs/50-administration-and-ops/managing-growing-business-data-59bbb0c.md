<!-- loio59bbb0cc363c4cc1bf6b0e3828643cd0 -->

# Managing Growing Business Data

If you experience or expect a significant data growth in your application’s persistency \(SAP HANA database\), it’s essential that you define a data retention strategy to manage the amount of relevant data.

A good data retention and archiving strategy keeps your system lean, which increases the performance and lowers the total cost of ownership since storing and maintaining the data consumes resources. In other words, if your application persists a significant amount of data, it’s important that you do some lifecycle management for this data. If you don’t, your database will grow indefinitely by default, which will negatively impact the performance and TCO. This is why you need to analyze the relevancy of especially aged data and how long you need to keep it.

As a first step, it’s important that you need to understand the relevance of the data created by your business application. A simple categorization could look like this:

-   Short retention time \(30-90 days, depending on operational needs\)

    -   Log and monitoring data
    -   Temporary data \(caches, session data, processing queues\)

-   Medium retention time \(2–7 years, depending on policy\)

    -   Operational data \(transaction and master data\)
    -   Business communications

-   Long retention time \(7–30 years, sometimes indefinitely, depending on regulations\)

    -   Regulated data \(financial records, tax documents, legal contracts, HR records\)
    -   Intellectual property and R&D data
    -   Compliance & legal hold data


Once you have classified the importance of your data and the required retention time, you need to evaluate the different options that you have to manage your business data according to your needs.



<a name="loio59bbb0cc363c4cc1bf6b0e3828643cd0__section_grc_l5z_52c"/>

## Options to Delete Data or Move Data out of the System

-   **Managing Data Retention Using Application Jobs**

    You can implement and schedule an application job to delete the data after a certain period of time. This application job defines the retention period and is executed on a regular basis.

    For more information about creating application jobs, see [Application Jobs](../30-development/application-jobs-0837d1e.md).

-   **Archiving Your Data**

    If you need to keep important data for a long time, for example, for legal reasons, you should consider archiving your data.

    For more information, see [Data Archiving](../30-development/data-archiving-210104b.md)




<a name="loio59bbb0cc363c4cc1bf6b0e3828643cd0__section_dtm_dvz_52c"/>

## Options to Keep Aged Data Available to the Application

-   **Unloading Data from the SAP HANA Memory Using Nearline Storage Extension \(NSE\)**

    If you want to keep the data available within the system, consider using the nearline storage extension \(NSE\) of the SAP HANA database. Using NSE, you can move major parts of your data out of the HANA memory. The data will remain mostly on disk, which is a much cheaper way to retain your data. You can switch on the NSE feature in ABAP development tools for Eclipse \(ADT\).

    For more information about NSE, see [Native Storage Extension for the ABAP Environment](native-storage-extension-for-the-abap-environment-68eb2a0.md).

-   **Optimizing the Delta Merge by Partitioning HANA Tables**

    SAP HANA requires memory to perform delta merge operations on tables. If you expect a table in your SAP HANA database to grow considerably to **over 100 million records**, you should consider optimizing the delta merge by partitioning the table. If you choose a very selective partition key that is also used frequently as a filter criterion by the application, this may also increase query performance.

    For more information about partitioning your table, see [Partition HANA Tables](partition-hana-tables-c2af316.md).

-   **Using Inverted Individual Indexes**

    You can reduce the size of the primary index by changing the index to an inverted individual index, which is a special type of SAP HANA index with more than one column for column store tables. Using an inverted individual index significantly reduces the memory footprint of specifically tables with many primary key columns. You can switch on the feature to change an index to an inverted individual index in ABAP development tools for Eclipse \(ADT\).

    For more information, see SAP Note [2600076](https://me.sap.com/notes/2600076).

-   **Compressing LOBs**

    If your application data contains a high volume of LOB data \(XSTRING or STRING fields with a length of more than 1000 bytes\), you should consider compressing such LOBs. This provides significant space savings and improves query performance because less I/O is required to access the same amount of data. In addition, the compression of LOBs reduces time and space requirements for backup, restore, and log archiving. The SAP HANA database doesn’t compress LOB data that exceeds 1000 bytes. In your application, you can compress and decompress LOB data using the ABAP class CL\_ABAP\_ZIP.

    For more information about compressing and decompressing your data, see [Compression/Decompression](../30-development/compression-decompression-f552f50.md).


