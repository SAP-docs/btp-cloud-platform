<!-- loiobac9a426b5154b69ae59dcc02b89a193 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# How to Define Semantic Grouping of Fields to Be Logged

Within an application, the data to be logged must be defined on a semantic level, before the actual fields and rules are defined. Log domains are semantic descriptions of semantically identical or related fields that have different technical representations.



## Context

In Read Access Logging, you define a log domain. When changing Read Access Logging configurations, assign a log domain to each field to be logged.

For a log domain, specify a name and a business area that the data element is related to. This definition is necessary because different applications might use the same log domain. For example, a log domain *account* can be something different in the Human Resources application than it is in the Banking application.



## Procedure

1.  In the *Read Access Logging Configuration* app, choose *Log Domains*.

2.  Decide whether to create a log domain or modify one of the templates delivered by SAP.

    SAP delivers default log domains you can copy and modify to your needs or you can create your own.

    -   To create your own log domain, choose *Create* under *Search Results*.

    -   To copy a log domain from SAP, do the following.


    1.  Under *Search Criteria*, choose *Search*.

    2.  From the search results, select a template from SAP.

        Templates from SAP use the <span class="SAP-icons-V5"></span> \(SAP\) icon under *Owner* or list ***SAP*** under *Created By* or *Changed By*.

    3.  Under *Actions*, choose <span class="SAP-icons-V5"></span> \(Copy\).


3.  Enter the required data.

    You can freely define the business area. The business area functions as a namespace for the data element.

    The description appears in the detailed view of the read access log and can be helpful for the person evaluating the log to identify the log domain.

4.  Save your entries.




<a name="loiobac9a426b5154b69ae59dcc02b89a193__result_wlz_yw3_fdb"/>

## Results

When you change a configuration, you can assign a log domain to each field to be logged. The log domain is displayed in the read access log and helps the log evaluator to understand the semantics of the field. It enables the evaluator to search for a given semantic field regardless of the technical representation or ID of this field.

