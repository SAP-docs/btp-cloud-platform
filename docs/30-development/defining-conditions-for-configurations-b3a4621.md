<!-- loiob3a4621060d84ba79b80e0556f7060b6 -->

# Defining Conditions for Configurations



## Prerequisites

You've created a configuration in the *Read Access Logging Configuration* app. Refer to [Creating Configurations](creating-configurations-c8ec529.md).



## Procedure

1.  Log on to the SAP Fiori launchpad in the ABAP environment system.

2.  In the *Read Access Logging Configuration* app, select the *Administration* tab.

3.  Choose *Configuration*.

4.  Choose *Enterprise Event Enablement* as *Channel*.

5.  Search for your configuration in the *Search Criteria* section. Refer to [Searching for Existing Configurations](searching-for-existing-configurations-2c7cbf4.md).

6.  Click the *Edit Configuration* icon of the configuration you want to define a condition for.

7.  In the *Conditions* section, click the button with the tooltip *Create Condition*.

    1.  Define the *Condition*.

    2.  Define the *Description*.

    3.  Click *Create*.





## Next Steps

Adding conditions is recommended to specify configurations \(refer to [Adding Expressions to Conditions](adding-expressions-to-conditions-8fba77e.md)\). This can influence the system performance depending on the logging scenario you have chosen. If you have chosen read access of events during support \(monitoring\), the system performance is improved. If you have chosen read access of events during sending \(runtime\), the system performance can become worse.

