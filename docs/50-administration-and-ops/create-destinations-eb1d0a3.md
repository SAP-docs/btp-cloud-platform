<!-- loioeb1d0a34b7c1411ba18401c07203020a -->

# Create Destinations

In the SAP BTP cockpit, you need to create destinations to enable the communication to the ABAP environment. In addition, the destination must be enabled for use in SAP Build.



## Procedure

1.  In the SAP BTP cockpit, navigate to your subaccount. See [Navigate to Orgs and Spaces](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/5bf87353bf994819b8803e5910d8450f.html).

2.  Choose *Connectivity* \> *Destinations.*.

3.  Choose *New Destination* \> *Blank Template*, and enter the following data:

    **Process Visibility Capability**


    <table>
    <tr>
    <th valign="top">

    Field
    
    </th>
    <th valign="top">

    Value
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Name
    
    </td>
    <td valign="top">
    
    Enter the destination name.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Type
    
    </td>
    <td valign="top">
    
    Select *HTTP*.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Description
    
    </td>
    <td valign="top">
    
    Enter a description.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    URL
    
    </td>
    <td valign="top">
    
    API-URL of the ABAP environment. The format is: https://\*\*\*\*\*.ondemand.com/.

    Set the destination URL to the API endpoint URL found in the service key that was created for the service instance of SAP Build Process Automation and which was used creating the communication arrangement. Access the communication arrangement and copy the API URL displayed under *Common Data* \> *API-URL*.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Proxy Type
    
    </td>
    <td valign="top">
    
    *Internet* 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Authentication
    
    </td>
    <td valign="top">
    
    Select *BasicAuthentication*.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    User
    
    </td>
    <td valign="top">
    
    \(Inbound\) communication user used in the communication arrangement
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Password
    
    </td>
    <td valign="top">
    
    Set the password to the secret. Password of the \(inbound\) communication user used in the communication arrangement.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Additional Properties
    
    </td>
    <td valign="top">
    
    Add the following properties:

    -   “sap.applicationdevelopment.actions.enabled” → true

    -   “sap.processautomation.enabled ” → true



    
    </td>
    </tr>
    </table>
    
4.  Save your entries.

5.  Open the Settings of SAP Build on your subaccount.

6.  Choose *Destinations* \> *New Destination*.

7.  Select the destination that you have created in the SAP BTP cockpit and click *Add*.




<a name="loioeb1d0a34b7c1411ba18401c07203020a__result_a5r_2qd_syb"/>

## Results

You have created a destination in your SAP BTP subaccount that can be used for the callback to the SAP BTP ABAP environment. The callback indicates the completion of a process on SAP Build Process Automation.

**Related Information**  


[Configure SAP Build Process Automation Destinations](https://help.sap.com/docs/build-process-automation/sap-build-process-automation/configure-sap-build-process-automation-destinations)

