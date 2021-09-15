<!-- loio02a09ca79c63481c8d8823dcaa89cee7 -->

# Using ABAP Statistics Records to Analyze System Activities

Use ABAP statistics records to find out which activities are running in your system.



<a name="loio02a09ca79c63481c8d8823dcaa89cee7__section_wqg_q2z_jqb"/>

## ABAP Request Statistics

By default, in the ABAP environment, requests are recorded with technical information, such as response time, program name, or CPU time. The resulting individual ABAP statistics records are written to the file system of the relevant tenant. ABAP statistics records are well suited to investigating the performance or resource consumption of a system or of a tenant in more detail, or, if performance problems occur, to identifying the area causing the problems.



<a name="loio02a09ca79c63481c8d8823dcaa89cee7__section_ob2_bfz_jqb"/>

## Use Cases

You typically use ABAP statistics records in the following scenarios:

-   You want to investigate your system workload to find out about top consumers and investigate in detail the overall response time contributions or the database connections.

    For more information, see [Analyzing the ABAP Resource Utilization of the ABAP Environment](Analyzing_the_ABAP_Resource_Utilization_of_the_ABAP_Environment_c54ec5e.md).

-   You want to analyze a specific workload, for example, the request statistics of an individual user or program name at a particular time.

    For more information, see [Capturing Request Statistics](Capturing_Request_Statistics_e86943a.md) and [Analyzing Captured Request Statistics](Analyzing_Captured_Request_Statistics_af3e856.md).


-   **[Capturing Request Statistics](Capturing_Request_Statistics_e86943a.md "With the Capture Workloads (Capture Request Statistics) app, you can capture request
		statistics to find out which activities are running in your ABAP system.")**  
With the *Capture Workloads* \(*Capture Request Statistics*\) app, you can capture request statistics to find out which activities are running in your ABAP system.
-   **[Analyzing Captured Request Statistics](Analyzing_Captured_Request_Statistics_af3e856.md "Get an overview of the request statistics that you have captured using the Capture Request Statistics app. View the
		server response time contribution or the database connections of a single request.")**  
Get an overview of the request statistics that you have captured using the *Capture Request Statistics* app. View the server response time contribution or the database connections of a single request.

