<!-- loio2c19449ebaeb4e4c8fe1c110a2a2b876 -->

# Set Scopes for the Service Instance Using the Command Line Interface

To set the necessary scopes of a service instance, you need to install a new service interface with all scopes needed or you update an already existing service interface.



## Procedure

1.  [Download and Install the Cloud Foundry Command Line Interface](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/4ef907afb1254e8286882a2bdef0edf4.html)

2.  [Create a Service Instance of the Workflow Capability Using the Command Line Interface](https://help.sap.com/viewer/e157c391253b4ecd93647bf232d18a83/Cloud/en-US/e8d88dd056f14c75af59e68d6b20345f.html)

3.  Add the new system environment variable *<CF\_HOME\>* that points to your CF path.

4.  Create a file named `scopes.json`, and paste the following JSON file:

    > ### Sample Code:  
    > ```
    > 
    > {  
    >     "authorities": [
    >         "WORKFLOW_INSTANCE_START",
    >         "WORKFLOW_DEFINITION_GET",
    >         "WORKFLOW_INSTANCE_GET",
    >         "WORKFLOW_INSTANCES_UPDATE",
    >         "WORKFLOW_INSTANCE_CANCEL",
    >         "WORKFLOW_INSTANCE_GET_ERROR_MESSAGES",
    >         "WORKFLOW_INSTANCE_GET_CONTEXT",
    >         "WORKFLOW_INSTANCE_GET_EXECUTION_LOGS",
    >         "MESSAGE_SEND"
    >         "TASK_GET"
    >     ]
    > }
    > ```

5.  Determine the API endpoint.

    1.  Navigate to your subaccount.

    2.  On the subaccount overview page under *Cloud Foundry*, there’s the API endpoint URL.


6.  Go to the command line.

    1.  Log in to your Cloud Foundry account:

        > ### Sample Code:  
        > ```
        > 
        > cf login
        > ```

    2.  Enter your credentials.

    3.  Choose the correct subaccount.

    4.  To update the service instance, enter the following command:

        > ### Sample Code:  
        > ```
        > 
        > cf update-service <SERVICE_INSTANCE_NAME> -c c:/temp/scopes.json
        > ```

        Use the name of the workflow capability instance from your subaccount.



