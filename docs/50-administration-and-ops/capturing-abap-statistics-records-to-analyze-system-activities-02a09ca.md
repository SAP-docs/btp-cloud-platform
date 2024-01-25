<!-- loio02a09ca79c63481c8d8823dcaa89cee7 -->

# Capturing ABAP Statistics Records to Analyze System Activities

Capture ABAP statistics records to find out which activities are running in your ABAP and database system.



<a name="loio02a09ca79c63481c8d8823dcaa89cee7__section_wqg_q2z_jqb"/>

## ABAP Request Statistics

By default, in the ABAP environment, requests are recorded with technical information, such as response time, program name, or CPU time. The resulting individual ABAP statistics records are written to the file system of the relevant tenant. ABAP statistics records are well suited to investigating the performance or resource consumption of a system or of a tenant in more detail, or, if performance problems occur, to identifying the area causing the problems.



<a name="loio02a09ca79c63481c8d8823dcaa89cee7__section_ob2_bfz_jqb"/>

## Use Cases

You typically use ABAP statistics records in the following scenarios:

-   You want to investigate your system workload to find out about top consumers and investigate in detail the overall response time contributions or the database connections. In this case, you can use the ABAP statistics records that are captured by default and visualized in the *System Workload* app.

    For more information, see [Navigating from System Workload to Single ABAP Statistics Records](https://help.sap.com/viewer/b273a660af4e4948a49a316ea2438f24/Cloud/en-US/2cb595f288194aebb15ba8a93692a678.html "Learn how you can find out about the system workload and how to drill down to single ABAP statistics records.") :arrow_upper_right:.

-   You want to analyze a specific workload, for example, the request statistics of an individual user or program name at a particular time.

    For more information, see [Capturing Request Statistics](capturing-request-statistics-e86943a.md) and [Analyzing Captured Request Statistics](analyzing-captured-request-statistics-af3e856.md).


**Related Information**  


[ABAP Statistics Records](https://help.sap.com/viewer/b273a660af4e4948a49a316ea2438f24/Cloud/en-US/583c0987c19b49d190e14aa909adb5b1.html "With an ABAP statistics record, you can get information about a request such as the response time, the request entry name, and so on.") :arrow_upper_right:

