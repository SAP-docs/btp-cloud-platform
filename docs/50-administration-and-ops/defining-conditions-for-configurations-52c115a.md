<!-- loio52c115a948ef4ea5a3bfa776fff2ada1 -->

# Defining Conditions for Configurations



## Prerequisites

You've created a configuration in the *Read Access Logging Configuration* app. Refer to [Creating Configurations](creating-configurations-7f3d5dd.md).



## Context

You can define conditions by In the opening dialog box, enter a condition name and a description for the condition and press *Create*. The newly created condition is displayed in the *Conditions* section.



## Procedure

1.  Log on to the SAP Fiori launchpad in the SAP S/4HANA Cloud system.

2.  In the *Read Access Logging Configuration* app, select the *Administration* tab.

3.  Choose *Configuration*.

4.  Choose *Enterprise Event Enablement* as *Channel*.

5.  Search for your configuration in the *Search Criteria* section. Refer to [Searching for Existing Configurations](searching-for-existing-configurations-84c908b.md).

6.  Press the *Edit Configuration* icon of the configuration you want to define a condition for.

7.  In the *Conditions* section, press the button with the tooltip *Create Condition*.

    1.  Define the *Condition*.

    2.  Define the *Description*.

    3.  Press *Create*.





## Next Steps

Adding conditions is recommended to specify configurations \(refer to [Adding Expressions to Conditions](adding-expressions-to-conditions-a979aab.md)\). This can influence the system performance depending on the logging scenario you have chosen. If you have chosen read access of events during support \(monitoring\), the system performance is improved. If you have chosen read access of events during sending \(runtime\), the system performance can become worse.

