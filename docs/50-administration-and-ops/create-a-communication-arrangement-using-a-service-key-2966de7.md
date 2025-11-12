<!-- loio2966de7262194fd8bd03681204e67583 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Create a Communication Arrangement Using a Service Key

To connect the ABAP environment and SAP Build Process Automation, you need a communication arrangement.



<a name="loio2966de7262194fd8bd03681204e67583__prereq_r5q_3wc_pgc"/>

## Prerequisites

You have already created a communication user, or you know how to create a new one through the Maintain Communication Users app on the SAP S/4HANA.



## Procedure

1.  Get the service key.

    1.  In the SAP BTP cockpit, navigate to your space. See [Navigate to Orgs and Spaces](https://help.sap.com/docs/btp/sap-business-technology-platform/navigate-to-orgs-and-spaces).

    2.  From the navigation pane, choose *Services* \> *Instances and Subscriptions*.

    3.  Click the name of your SAP Build Process Automation instance and choose the side arrow <span class="SAP-icons-V5"></span>.

    4.  From the navigation pane, choose *Service Keys*.

    5.  Select one entry, and copy the service key.


2.  In your SAP S/4HANA Cloud system, go to *Administration* \> *Communication Management*. Open the *Communication Arrangements* app.

3.  Choose *New* to create a communication arrangement.

4.  In the *New Communication Arrangement* window, in the *Scenario* field enter *SAP\_COM\_0863*.

5.  In the *Arrangement Name* field, enter a name for the arrangement.

6.  Choose *Additional Properties* and in the following fields enter:


    <table>
    <tr>
    <th valign="top">

    Property Name
    
    </th>
    <th valign="top">

    Action
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    SAP Process Visibility Service Tenant ID
    
    </td>
    <td valign="top">
    
    -   If you do not require integration with the process visibility capability, leave this field **blank**.
    -   If integration is needed, enter the Tenant ID of the SAP BTP sub-account.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Consumer Type \(Workflow\)
    
    </td>
    <td valign="top">
    
    Choose *Default*.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Consumer Type \(Visibility\)
    
    </td>
    <td valign="top">
    
    -   Select the customer type corresponding to the scenarios for which you would like to create an extension workflow.
    -   The consumer type is used to identify the communication arrangement. Ensure that you assign the customer type to exactly one communication arrangement. You can assign multiple consumer types to one communication arrangement.
    -   Based on how the extension workflow is integrated, the customer type may vary. If the intergration method is:
        -   Flexible Workflow Extension of Business Workflow: Use the scenario identifier as the consumer type. For example, WS12345678.
        -   Directly integrated through API: Choose the consumer type provided and documented by the SAP S/4HANA Cloud application.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    API \(Optional\)
    
    </td>
    <td valign="top">
    
    -   Provide an SAP Build Process Automation API Key if API Triggers are used in relevant SAP Build Process Automation processes.
    -   API keys are created in the Control Tower of SAP Build Process Automation. Ensure that the API keys have the scopes *trigger\_read* and *trigger\_execute*.
    -   If the API key is already stored in the service instance, you do not need to provide it again in the communication arrangement.

    > ### Note:  
    > If you want to add an API key, you cannot do it on the initial Communication Arrangement window. You can do it on the next Communication Arrangement page.


    
    </td>
    </tr>
    </table>
    
7.  Select a communication user \(of which you know the password\) or create a new one to use for inbound communication \(from SAP BTP to your ABAP environment\).

8.  Paste the service key into the corresponding field, and choose *Create*.

    To set up the destination configuration in SAP BTP, you need the inbound username, password, and the host URL \(with port\) of the inbound services.




<a name="loio2966de7262194fd8bd03681204e67583__result_ipp_pd1_qjb"/>

## Results

You’ve created the communication arrangement, the communication system, and an inbound user.

