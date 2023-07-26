<!-- loioa979aab7d43d469fb4b3e27d1d762df6 -->

# Adding Expressions to Conditions



## Prerequisites

You've created a condition for a configuration in the *Read Access Logging Configuration* app. Refer to [Defining Conditions for Configurations](defining-conditions-for-configurations-52c115a.md).



## Context

Once you've created a condition and you want to log events only in a certain context, like at runtime, add an expression to your condition.



## Procedure

1.  Log on to the SAP Fiori launchpad in the SAP S/4HANA Cloud system.

2.  In the *Read Access Logging Configuration* app, select the *Administration* tab.

3.  Choose *Configuration*.

4.  Choose *Enterprise Event Enablement* as *Channel*.

5.  Search for your configuration in the *Search Criteria* section. Refer to [Searching for Existing Configurations](searching-for-existing-configurations-84c908b.md).

6.  Click the *Edit Configuration* icon of the configuration you want to define a condition for.

7.  In the *Conditions* section, select the condition you want to add expressions for.

8.  Click *Create* in the *Expressions* section of the condition.

    1.  Define a name for the *Expression*.

    2.  Choose *Create*.


    The *Attributes* and *Select options* are displayed in the *Details of Expression* section.

9.  Drag and drop the *Access Context* condition field from the *Field List* \> *Channel Fields* \> *Condition Fields* to the *Select options* section under *Details of Expression*.

10. Click *Save as Active* to activate your configuration including assigned conditions.


**Related Information**  


[Defining Configurations in Read Access Logging](https://help.sap.com/doc/saphelp_scm700_ehp02/latest/en-US/68/c9d60a3ed34ccca056afc7efce6f36/frameset.htm "Defining Configurations in Read Access Logging")

