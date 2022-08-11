<!-- loioe7b0a46a4bbf400e8a052dac277ab803 -->

# Read Access Logging \(RAL\)

With *Read Access Logging* \(RAL\) for events, you can monitor and log read access to sensitive data because of diverse data privacy regulations. The categorization of sensitive data can vary: it can depend on your country’s code of law or on your external or internal company policies. RAL thus helps you to find out who had access to sensitive data, in which way and at what time.

RAL is offered for different channels. A channel is a way for data to leave the system, for example dynpros of Web services. *Enterprise Event Enablement* is another channel that is supported in the central RAL monitor.

For more information on RAL in the context of SAP NetWeaver, see [Read Access Logging](https://help.sap.com/doc/saphelp_scm70/7.0/en-US/54/69bbeab2e94c93b9031584711d989d/frameset.htm).

> ### Note:  
> Using RAL requires system resources. This can have a strong impact on your system performance, depending on the number and type of logs.

**Prerequisites**

If you want to use RAL, you need the *Data Privacy Specialist* \(SAP\_BR\_DATA\_PRIVACY\_SPECIALIST\) business role template with which you can block, unblock, and display blocked personal data. See [Access Control and Data Protection](https://help.sap.com/viewer/55a7cb346519450cb9e6d21c1ecd6ec1/2102.500/en-US/2fc65edfd6604391b89753ca9feb6218.html).

Events can be logged for three scenarios:

-   Read access of events during support \(monitoring\)

    This is the case when the event monitor was opened by SAP support to check the payload of sent or consumed events.

-   Read access of events during sending \(runtime\)

    This is the case when an outbound binding exists and an event is to be sent to SAP Event Mesh by the Enterprise Event Enablement. For more information, see [Configure Event Publishing and Event Consumption Scenarios](configure-event-publishing-and-event-consumption-scenarios-978b039.md).


You can define which properties of an event are to be logged to avoid that all events are logged. Please consider this carefully as it may affect the system performance.

The following types can be logged once a corresponding configuration exists:

-   Channel Fields
    -   Cloud Event Context Fields

        -   Source

        -   Type

        -   Id

        -   Time


    -   Payload types of a selected producer or consumer. A producer or consumer is a set of event types belonging to a business entity.



-   System Fields

    -   User Name

    -   Screen Title

    -   Transaction Code



For more information, see [Events on SAP API Business Hub](https://help.sap.com/viewer/0f69f8fb28ac4bf48d2b57b9637e81fa/latest/en-US/8cbf952e55364254be2da77aa1342aa5.html).

In the *Read Access Logging Configuration* app, you have two options:

-   You can search for existing configurations

-   You can create your own configurations




<a name="loioe7b0a46a4bbf400e8a052dac277ab803__section_nh4_wbr_1pb"/>

## Searching for Existing Configurations

1.  In the *Read Access Logging Configuration* app on the *Administration* tab, choose *Configuration*.

2.  Choose *Enterprise Event Enablement* as channel.

3.  Specify your search criteria:

    -   Registration ID

    -   Registration Version

    -   Repository ID

    -   Event Scenario

    -   Description

    -   State


4.  Click *Search*.


A list of existing configurations is displayed.



<a name="loioe7b0a46a4bbf400e8a052dac277ab803__section_jgm_cyv_4cb"/>

## Creating Configurations

1.  In the *Read Access Logging Configuration* app on the *Administration* tab, choose *Configuration*.

2.  Choose *Enterprise Event Enablement* as channel.

3.  Press *Create*.

4.  On the *Create Configuration* screen, you can search for existing event consumers or event producers to which you can assign a configuration. To do so, specify your search criteria:

    -   Registration ID

    -   Registration Version

    -   Repository ID

    -   Event Scenario


5.  Click *Search*

    A list of existing producers \(P\) and consumers \(C\), matching your search criteria, is displayed.

    > ### Note:  
    > If you do not specify your search criteria and click *Search*, all existing producers and consumers are displayed.

6.  Choose one producer/consumer and press *Create*. For the chosen consumer or producer, the following sections are displayed:

    -   Attributes

        -   Application/Software Component that is assigned to a consumer or producer

        -   Description for the the Application/Software Component


    -   Administrative Information

        -   Technical Data

        -   Created

        -   Changed


    -   Log Groups

        Log groups are groups of fields that are displayed in one log entry in the read access log. You can add a log group by clicking the *Create Log Group* button. In the opening dialog box, define the purpose and the description for the log group and press *Create*.

        > ### Note:  
        > Keep in mind to drag and drop channel fields and/or system fields from the *Field List* to the *Fields* section of the log group.

        > ### Note:  
        > You can create log groups without adding conditions. If you want to add conditions, uncheck the *Without Condition* flag.

    -   Conditions. For more information, see chapter *Defining and Adding Conditions to Configurations*.

    -   Field list


7.  Press *Save as Active* to activate your configuration.




<a name="loioe7b0a46a4bbf400e8a052dac277ab803__section_vl2_bhr_1pb"/>

## Defining and Adding Conditions to Configurations \(optional\)

You can define conditions by clicking the *Create Conditions* button. In the opening dialog box, enter a condition name and a description for the condition and press *Create*. The newly created condition is displayed in the *Conditions* section.

> ### Note:  
> Adding conditions is recommended to specify configurations. This can influence the system performance depending on the logging scenario you have chosen. If you have chosen read access of events during support \(monitoring\), the system performance is improved. If you have chosen read access of events during sending \(runtime\), the system performance can become worse.

**Adding Expressions to Conditions**



Once you have created a condition and you want to log events only in a certain context, i.e. at runtime, add an expression to your condition. To do so, proceed as follows:

1.  Press *Create* in the *Expressions* section of the condition.

2.  In the opening dialog box, enter a name for the expression an press *Create*. The *Attributes* and *Select Options* are displayed in the *Details of Expression* area.

3.  Drag and drop the *Access Context* condition field from the *Field List* to the *Select Options* area under *Details of Expression*.

4.  Press *Save as Active* to activate your configuration including assigned conditions again.


For more information, see [Defining Configurations in Read Access Logging](https://help.sap.com/doc/saphelp_scm700_ehp02/7.0.2/en-US/68/c9d60a3ed34ccca056afc7efce6f36/frameset.htm).



<a name="loioe7b0a46a4bbf400e8a052dac277ab803__section_fdx_qfb_x4b"/>

## Monitor Logged Events

1.  In the *Read Access Logging Configuration* app, choose *Read Access Log*.

2.  As *Data Source*, choose *Raw Database*.

3.  Specify your search criteria:

    -   Channel

    -   Date/Time

    -   User Name

    -   Application Comp.

    -   Software Component


4.  Specify the maximum number of hits.

5.  Choose *Search*.

    A list of logs according to the search criteria is displayed.




[Read Access Logging](../50-administration-and-ops/read-access-logging-5688c3a.md)

[How to Monitor the Read Access Log](../50-administration-and-ops/how-to-monitor-the-read-access-log-5a1011a.md)

[Access Control and Data Protection](https://help.sap.com/viewer/55a7cb346519450cb9e6d21c1ecd6ec1/2102.500/en-US/2fc65edfd6604391b89753ca9feb6218.html)

