<!-- loiobcd3cc9839dc405aa29337702ab0a320 -->

# Enable Technical Authentication

Access the workflow capability with a technical user.



## Context

The authorities of a technical authentication refer to the scopes of the respective endpoints.



<a name="loiobcd3cc9839dc405aa29337702ab0a320__steps_ivf_hqs_zhb"/>

## Procedure

1.  Prepare a JSON object that specifies the list of authorizations you want to grant to the OAuth2 client that is provided through the service instance.

    The following example grants to the service instance all available authorities:

    > ### Sample Code:  
    > ```lang-json
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
    >         "WORKFLOW_INSTANCE_UPDATE_CONTEXT",
    >         "WORKFLOW_INSTANCE_GET_EXECUTION_LOGS",
    >         "MESSAGE_SEND",
    >         "TASK_GET",
    >     ]
    > }
    > 
    > ```

2.  Create or update a service instance and provide the JSON object as described in [Enable Technical Authentication](https://help.sap.com/viewer/e157c391253b4ecd93647bf232d18a83/Cloud/en-US/c74f5ff9065b4baeb700d033602ef1d9.html).


