<!-- loio7f3d5ddd964743d89dce15a9c89cb2eb -->

# Creating Configurations



## Prerequisites

The key user must have the business role `SAP_BR_ADMINISTRATOR` \(Administrator\) that contains the business catalog `SAP_CORE_BC_COM` \(Communication Management\).



## Procedure

1.  Log on to the SAP Fiori launchpad in the SAP S/4HANA Cloud system.

2.  In the *Read Access Logging Configuration* app, select the *Administration* tab.

3.  Choose *Configuration*.

4.  Choose *Enterprise Event Enablement* as *Channel*.

5.  Click *Create* at the bottom of the page.

6.  On the *Create Configuration* screen, you can search for existing event consumers or event producers to which you can assign a configuration. To do so, specify your search criteria:

    -   Registration ID
    -   Registration Version
    -   Repository ID
    -   Event Scenario
    -   Busi Object Name

    1.  Click *Search*.

        A list of existing producers \(P\) and consumers \(C\), matching your search criteria, is displayed.

        > ### Note:  
        > If you do not specify your search criteria and click *Search*, all existing producers and consumers are displayed.

    2.  Choose one producer or consumer.

    3.  Click *Create*.

        For the chosen consumer or producer, the following sections are displayed:


        <table>
        <tr>
        <td valign="top">
        
        *Attributes*
        
        </td>
        <td valign="top">
        
        -   *Application/Software Component* that is assigned to a consumer or producer
        -   Description for the *Application/Software Component*


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *Administrative Information*
        
        </td>
        <td valign="top">
        
        -   *Technical Data*
        -   *Created*
        -   *Changed*


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *Log Groups*
        
        </td>
        <td valign="top">
        
        Log groups are groups of fields that are displayed in one log entry in the read access log.

        To add a log group, do the following:

        -   Click the button with the tooltip *Create Log Group*.
        -   In the *Create Log Group* dialog box, do the following:
            -   Define the *Purpose*.
            -   Define the *Description*.

        -   Click *Create*.

        > ### Note:  
        > Keep in mind to drag and drop *Channel Fields* and/or *System Fields* from the *Field list* to the *Fields* section of the log group.

        > ### Tip:  
        > You can create log groups without adding conditions. If you want to add conditions, uncheck the *Without Condition* flag.


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *Conditions*
        
        </td>
        <td valign="top">
        
        To add a condition, do the following:

        -   Click the button with the tooltip *Create Condition*.
        -   In the *Create Condition* dialog box, do the following:
            -   Define the *Condition*.
            -   Define the *Description*.

        -   Click *Create*.


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *Field list*
        
        </td>
        <td valign="top">
        
         
        
        </td>
        </tr>
        </table>
        
    4.  Click *Save as Active* to activate your configuration.



**Related Information**  


[Defining Conditions for Configurations](defining-conditions-for-configurations-52c115a.md "")

