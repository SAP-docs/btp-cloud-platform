<!-- loio2c19449ebaeb4e4c8fe1c110a2a2b876 -->

# Set Scopes for the Service Instance Using the Command Line Interface

To set the necessary scopes of a service instance, you need to install a new service interface with all scopes needed or you update an already existing service interface.



<a name="loio2c19449ebaeb4e4c8fe1c110a2a2b876__steps_jqs_s3r_s5b"/>

## Procedure

1.  To update the workflow capability instance with the necessary scopes, save the following JSON file that specifies all necessary scopes:

    ```json
    
    {  
        "authorities": [
            "WORKFLOW_INSTANCE_START",
            "WORKFLOW_DEFINITION_GET",
            "WORKFLOW_INSTANCE_GET",
            "WORKFLOW_INSTANCES_UPDATE",
            "WORKFLOW_INSTANCE_CANCEL",
            "WORKFLOW_INSTANCE_GET_ERROR_MESSAGES",
            "WORKFLOW_INSTANCE_GET_CONTEXT",
            "WORKFLOW_INSTANCE_GET_EXECUTION_LOGS",
            "MESSAGE_SEND",
            "TASK_GET"
        ]
    }
    ```

    To set these scopes, see *Update an existing service instance* in [Enable Technical Authentication](https://help.sap.com/docs/WORKFLOW/e157c391253b4ecd93647bf232d18a83/c74f5ff9065b4baeb700d033602ef1d9.html?version=Cloud).

2.  Model the workflow as described in [Developing Applications with Workflow Capability](https://help.sap.com/docs/WORKFLOW/e157c391253b4ecd93647bf232d18a83/60ae81179050478caa4212fad4ba50f2.html).


