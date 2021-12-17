<!-- loio591b668e8ce345b9af3311249c88a2c5 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# How to Define Purposes of Read Access Logging

Read Access Logging is always based on a logging purpose that is freely defined according to the requirements of an organization. It describes why specific data is logged.



## Context

In the configuration, you specify the logging purpose and each log entry in the log is assigned its purpose as an attribute. This configuration enables you to organize the log data by the logging purpose. For example, various archiving rules or reportings can be created based on logging purposes.

In each Read Access Logging configuration, assign a logging purpose. When you define archiving rules, use the logging purpose as the basis.



## Procedure

1.  In the *Read Access Logging Configuration* app, choose *Logging Purposes*.

2.  Decide whether to create a purpose or modify one of the templates delivered by SAP.

    SAP delivers default purposes you can copy and modify to your needs or you can create your own.

    -   To create your own purpose, choose *Create* under *Search Results*.

    -   To copy a purpose from SAP, do the following.


    1.  Under *Search Criteria*, choose *Search*.

    2.  From the search results, select a template from SAP.

        Templates from SAP use the <span class="SAP-icons"></span> \(SAP Template\) icon under *Owner* or list ***SAP*** under *Created By* or *Changed By*.

    3.  Under *Actions*, choose <span class="SAP-icons"></span> \(Copy\).


3.  Enter the required data.

    The ID is limited to ten characters. We recommend that you use an abbreviation of the purpose name as ID.

    The purpose name appears on all UIs.

4.  Save your entries.




<a name="loio591b668e8ce345b9af3311249c88a2c5__result_yf3_yvc_b2b"/>

## Results

Assign logging purposes during the creation of Read Access Logging configurations. Logging purposes help you with the definition of archiving rules.

