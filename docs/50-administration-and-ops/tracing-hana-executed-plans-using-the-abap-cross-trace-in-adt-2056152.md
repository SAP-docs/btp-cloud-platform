<!-- loio205615230cd146b09bf1d9c85aea5c54 -->

# Tracing HANA Executed Plans Using the ABAP Cross Trace in ADT

As an ABAP developer working with SAP Fiori apps, you can use the ABAP Cross Trace to capture HANA executed plans of SQL statements run by the app you're tracing.

In the ABAP Cross Trace in ABAP development tools for Eclipse \(ADT\), capture executed plans for SQL statement executions as PlanViz \(PLV\) files using the integrated HANA Plan Trace feature. You can then download and view the PLV files in the SQL Analyzer Tool for SAP HANA.



<a name="loio205615230cd146b09bf1d9c85aea5c54__section_v3z_dnh_cfc"/>

## Procedure

1.  To open the ABAP Cross Trace view, choose *Window* \> *Show View* \> *Other* \> *ABAP Cross Trace* in ABAP development tools for Eclipse \(ADT\).

2.  Choose *Create Cross Trace Configuration*.

3.  In the *Request Filters* section, enter your transaction criteria in the fields for *User*, *Request Entry Type* and *Request Entry Name*.

4.  In the *Components* window on the right, make sure that *HANA Plan Trace* is selected and the *Trace Level* for this component is set to *Verbose*.

    ![](images/Cross_Trace_Configuration_c1e9b0f.png)

5.  To start the trace for your user, choose *OK*. The generation of trace records will stop after the maximum number, which is set in the properties section, is reached.

6.  On the *Trace Results* tab page, right-click on your user, choose *Refresh*, and you’ll get an overview of the captured trace records for the duration the trace was running. The trace records that include a captured PLV file have a comment in the properties starting with *TMO\_HPT: SADL\_PLV*.

7.  For details of a trace record, doubleclick an entry on the *Trace Results* tab page. In the tree, you find HANA Plan Trace results within the *SADL Query* nodes in *SQL SELECT* subnodes.

8.  Choose a trace result entry named *HANA Plan Trace*. The properties for this entry are displayed in the *Properties* section.

    ![](images/Cross_Trace_Results_8fee0d3.png)

9.  Chose *Content* to display the `PLV_TRACE_INFO`.

10. Copy the URL displayed under *PLV\_URI* into your web browser and open it. This will start the PLV download.

11. To view and analyze the PLV files, open them in the SQL Analyzer Tool for SAP HANA \(Visual Studio Code extension\).

    ![](images/CrossTrace_PLV_HANA_SQL_Analyzer_b89eb85.png)




<a name="loio205615230cd146b09bf1d9c85aea5c54__section_fgy_lg4_cfc"/>

## Related Information

[SQL Analyzer Tool for SAP HANA](https://help.sap.com/docs/sql-analyzer)

