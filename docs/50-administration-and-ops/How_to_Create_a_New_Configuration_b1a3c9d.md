<!-- loiob1a3c9df868e416097a3c146859724df -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# How to Create a New Configuration

You can define what to log by creating your own read access logging configuration or modifying a template delivered by SAP.



## Procedure

1.  In the *Read Access Logging Configuration* app, choose *Configuration*.

2.  Select a channel.

3.  Decide whether to create a configuration or modify one of the templates delivered by SAP.

    SAP delivers default configurations you can copy and modify to your needs or you can create your own.

    -   To create your own configuration, select a channel and choose *Create* under *Search Results*.

        For channels that use recordings, choose a recording.

    -   To copy a configuration from SAP, do the following.


    1.  Under *Search Criteria*, filter with **Owner** is **SAP Template**.


    1.  From the search results, select a template from SAP.

        Templates from SAP use the <span class="SAP-icons"></span> \(SAP\) icon under *Owner*.

    2.  Under *Actions*, choose <span class="SAP-icons"></span> \(Copy\).

        For channels that use recordings, copy the recording that comes with the template under the same name or enter a new name.

    3.  Find the channel you just copied and choose <span class="SAP-icons"></span> \(Edit Configuration\).


4.  Depending on the channel, select the object you want to create a configuration for.

    For example, an operation for a Web Service, a function module for an RFC, or an application for a Web Dynpro. If you are editing an existing channel, the object is already selected for you.

    For more information, see [Channel-Specific Information](Channel-Specific_Information_24c7399.md).

5.  Enter the required data.

    -   For Dynpro, choose *Application / Software Component*.

    -   For Dynpro and Web Dynpro, specify a *Log Context*.

6.  Create log groups.

    > ### Note:  
    > For a logging purpose, only create one logging group.

    1.  Under *Log Groups*, choose <span class="SAP-icons"></span> \(Create Log Group\).

    2.  Specify a logging purpose and a description for the log group.

    3.  Specify the fields that you want to log together in the log group.

        Move fields in the *Field list* to the log group.

    4.  In the *Fields* list, define how each field should be logged.

        -   The *Logging Type* determines if only the field name is logged when accessed or if the value of that field is also logged.

        -   To save space in the database, set *Exclude if Initial* to have Read Access Logging ignore a field if its value is initial.

            > ### Note:  
            > The initial value is not the default value, but the technical initial value. For example, the empty value for string or character-based fields or the number zero for integers. The default value is logged in any case.
            > 
            > If this option is set and all fields within a Web service, RFC, or Web Dynpro UI are initial, no log entry is created for any of the fields.

        -   For Dynpro and Web Dynpro, specify the *Field Type*, which is whether an input field, an output \(display\) field, or both.


        > ### Note:  
        > Values for password fields cannot be included in logs. The*Logging Type* is *Without Value* and cannot be changed.


7.  Create conditions.

    1.  Under *Conditions* choose <span class="SAP-icons"></span> \(Create Condition\).

        If you do not assign any conditions, select the *Without Condition* checkbox in the log group attributes and continue with the next step.

    2.  Specify a name and a description for the condition.

    3.  Create one or more expressions for the condition.

        Expressions are joined using logical `AND`.

    4.  Specify the fields that you want to define rules for.

        Move fields in the *Field list* to the expression.

    5.  For each field, specify the select option \(the selection criteria\).

        For example, *Username Inclusive Equals John Smith*.

        Select options are joined using logical `OR`.

    6.  Assign conditions to a log group or set the *Without Condition* option.

        To assign a condition, select the Log Group, choose *Assign Condition* and select a condition. Activate the assignment if you want to apply the condition to the log group. The log groups and conditions do not need to be activated, however.


8.  To check the configuration for consistency and function: choose <span class="SAP-icons"></span> \(Check Configuration\) *Check*.

9.  Save your entries.


