<!-- loiob70486ee198343af8cfc4fa8ba284ef5 -->

# Process Findings After Analysis

Find out how you can process your findings after custom code analysis.



<a name="loiob70486ee198343af8cfc4fa8ba284ef5__section_b2t_y15_lcc"/>

## Purpose

In case you've been wondering what the next steps would be after custom code analysis and what to do with your findings in the Analyze Custom Code app, this topic is for you. Here, you will learn about your options for after custom code analysis.

1.  **ABAP Test Cockpit \(ATC\) Baseline**

    With the baseline functionality, it's now possible to add/remove custom code project check results to/from the baseline​ and choose whether you would like to:

    1.  Exempt your findings: ATC findings from the baseline will be marked as exempted in the check results list.

    2.  Suppress your findings: After a new ATC check run, all ATC findings from the baseline are excluded from the ATC run results list.

    3.  Reduce findings' priority: The priority will be reduced to low \(priority 3\) for all ATC findings of the relevant ATC check result.

        **Result:** After adding findings to the baseline, they won't appear in the subsequent check results of the custom code project.


    > ### Note:  
    > Please be aware that:
    > 
    > -   Once you have added findings to the baseline, the custom code migration project cannot be deleted. Remove your findings from the baseline first and then proceed with deleting your project.
    > 
    > -   The analysis cannot be started again after the findings were added to the baseline.

2.  **SAP Readiness Check**

    You can download the check results to upload them later onto SAP Readiness Check 2.0. To do so, in the *Analyze Findings* section of your project, choose the arrow next to the spreadsheet icon and select *Export for SAP Readiness Check*. To learn more about SAP Readiness Check for SAP S/4HANA, see SAP Note [2913617](https://me.sap.com/notes/2913617).


