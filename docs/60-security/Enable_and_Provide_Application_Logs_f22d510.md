<!-- loiof22d5100b3a243af88e3edf5311754fc -->

# Enable and Provide Application Logs

If there are authentication problems in your application, enable logging for the container security library in question, reproduce the problem, and attach the application logs. To obtain more details, set the environment variables for the application.



<a name="loiof22d5100b3a243af88e3edf5311754fc__context_agt_xwy_4mb"/>

## Context

> ### Tip:  
> We also provide a [log collector script](https://github.com/SAP/cloud-security-xsuaa-integration/tree/master/troubleshooting/logcollector), that helps you to increase the log verbosity of your application and application router.



## Procedure

1.  Open a command prompt.

2.  Log on to your Cloud Foundry environment using the Cloud Foundry command line interface \(CLI\). For more information, see [Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface](../50-administration-and-ops/Log_On_to_the_Cloud_Foundry_Environment_Using_the_Cloud_Foundry_Command_Line_Interface_7a37d66.md).

3.  Choose your organization.

    > ### Note:  
    > The Cloud Foundry command line interface prompts you to choose an org. To find the org of your subaccount, use the SAP BTP cockpit to go to your subaccount. You find the org in the Cloud Foundry tile under *Organization* \(see [Navigate to Orgs and Spaces](../50-administration-and-ops/Navigate_to_Orgs_and_Spaces_5bf8735.md)\).

4.  Choose the space where the application is located.

5.  To route the log messages to the standard output, use the following command:

    ***cf set-env <application\_name\> SAP\_EXT\_TRC stdout***

    > ### Example:  
    > ***cf set-env your-app SAP\_EXT\_TRC stdout***

6.  To set the log level, use the following command:

    ***cf set-env <application\_name\> SAP\_EXT\_TRL 3***

    > ### Example:  
    > ***cf set-env your-app SAP\_EXT\_TRL 3***

7.  \(For Node.js\) To set detailed logs of the Security API for Node.js, use the following command:

    ***cf set-env <application\_name\> DEBUG xssec\****

    > ### Example:  
    > ***cf set-env your-app DEBUG xssec\****

8.  Restage your application using the following command:

    ***cf restage <application\>***

    > ### Example:  
    > ***cf restage your-app***

    Restaging the application enables the display of the logs.

9.  We recommend piping the output to a log file. Use the following command to do this:

    ***cf logs <application\> \> <log\_file\_name\>***

    > ### Example:  
    > ***cf logs your-app \> your-app-log.txt***

10. Reproduce the problem in your application. The events that occur in your application are logged in your local log file.

    > ### Note:  
    > You can stop the recording of the log messages using [CTRL+C\]. You can revert the environment variables using the following command:
    > 
    > ***cf unset-env <application\> SAP\_EXT\_TRC***
    > 
    > > ### Example:  
    > > ***cf unset-env your-app SAP\_EXT\_TRC***
    > 
    > Restage your application using the following command:
    > 
    > ***cf restage <application\>***
    > 
    > > ### Example:  
    > > ***cf restage your-app***

11. Running on the cloud management tools feature set B: Create an incident for your local supportRunning on the cloud management tools feature set A: Create an incident using the component `BC-CP-CF-SEC-IAM`. Use the [SAP Support Portal](https://support.sap.com/home.html). For more information, see [Monitoring and Troubleshooting](Monitoring_and_Troubleshooting_1b3e89e.md).

12. Attach the log files to the incident.

    To obtain more details about the token validation, set the following environment variables of the container security library and Node.js \(if applicable\):

    <a name="loiof22d5100b3a243af88e3edf5311754fc__table_ncv_lfl_gdb"/>`SAPSSOEXT` Environment Variables


    <table>
    <tr>
    <th>

    Environment Variables


    
    </th>
    <th>

    Description


    
    </th>
    </tr>
    <tr>
    <td>

     ***SAP\_EXT\_TRC*** 


    
    </td>
    <td>

    Enablement of logs


    
    </td>
    </tr>
    <tr>
    <td>

     ***SAP\_EXT\_TRL*** 


    
    </td>
    <td>

    Log level ranging from off to high

    Values \(integer\):

    -   ***0*** \(off\)

    -   ***1*** \(default\)

    -   ***2*** \(medium\)

    -   ***3*** \(high\)


    
    </td>
    </tr>
    </table>
    
    <a name="loiof22d5100b3a243af88e3edf5311754fc__table_erj_lqn_hdb"/>`Node.js` Environment Variables


    <table>
    <tr>
    <th>

    Environment Variables


    
    </th>
    <th>

    Description


    
    </th>
    </tr>
    <tr>
    <td>

     ***DEBUG*** 


    
    </td>
    <td>

    Detailed logs of the security API for Node.js

    Value \(string\): ***xssec\****


    
    </td>
    </tr>
    </table>
    

