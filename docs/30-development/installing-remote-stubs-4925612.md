<!-- loio4925612fe6bd47c6a78b81d4d9ee8f6a -->

# Installing Remote Stubs

During ATC execution, the central check system accesses the systems in your landscape remotely through so-called remote stubs using RFC connection. Thus, remote stubs serve as an interface between the central check system and on-premise systems; they return a model of custom code that needs to be checked.



<a name="loio4925612fe6bd47c6a78b81d4d9ee8f6a__prereq_cwz_z1q_1kb"/>

## Prerequisites

In the on-premise system, implement SAP Note [2599695](https://me.sap.com/notes/2599695) \(Custom Code Migration Fiori App: Remote Stubs for the Checked System\) in advance.



## Context

You want to analyze your custom code in your on-premise system using the `Custom Code Migration` app.



## Procedure

1.  In the on-premise system, perform transaction `SNOTE`.

2.  Download SAP Note [2599695](https://me.sap.com/notes/2599695).

    The *Note Assistant: Note Download* dialog is opened.

3.  To implement the remote stubs, select and confirm the displayed SAP Note.

4.  It is also recommended to apply SAP Notes in checked systems. Update your check system by following these steps:

    1.  Perform transaction `SNOTE`.

    2.  In the menu bar, select *Goto* \> *Other tools* \> *Launch Note Analyzer*.

    3.  Upload the file *SAPNote\_2436688\_Checked\_System.xml* available as attachment in SAP Note [2436688](https://me.sap.com/notes/2436688). You can now process the notes using SAP Note Analyzer.

        > ### Note:  
        > In case you don't want to use the Note Analyzer, please also apply the following SAP Notes:
        > 
        > -   [2485231](https://me.sap.com/notes/2485231) - Remote ATC Checks of Modifications and Enhancements
        > 
        > -   [2270689](https://me.sap.com/notes/2270689) - RFC Extractor for performing static checks
        > 
        > -   [2190065](https://me.sap.com/notes/2190065) - ATC/CI: Remote Code Analysis - Object Provider Stub





<a name="loio4925612fe6bd47c6a78b81d4d9ee8f6a__result_a4y_43c_3yb"/>

## Results

The `Custom Code Migration` app now has access to the on-premise system. You can now start the custom code analysis.

