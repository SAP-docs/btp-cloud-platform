<!-- loio80a8d52279ef428d96dadcca9a8dd752 -->

# Pulling Git Repositories to an ABAP Environment System



<a name="loio80a8d52279ef428d96dadcca9a8dd752__prereq_e3z_wdw_ljb"/>

## Prerequisites

-   You have an ABAP environment system.
-   You’ve created a *Communication User* as described in [How to Create Communication Users](../50-administration-and-ops/How_to_Create_Communication_Users_0377ade.md).
-   You’ve created a *Communication System* as described in [How to Create Communication Systems](../50-administration-and-ops/How_to_Create_Communication_Systems_c2234ac.md)
-   You’ve created a *Communication Arrangement* as described in [How to Create a Communication Arrangement](../50-administration-and-ops/How_to_Create_a_Communication_Arrangement_a0771f6.md).
-   You have selected the communication scenario **SAP\_COM\_0510** for your communication arrangement and have mapped it to your communication system.
-   You have cloned the Git repository to the ABAP Environment system. See [Cloning Git Repositories to an ABAP Environment System](Cloning_Git_Repositories_to_an_ABAP_Environment_System_0552763.md).



## Context

You can use the communication scenario *SAP\_COM\_0510* to pull Git repositories to an ABAP environment system.

> ### Note:  
> In ABAP environment, Git repositories are wrapped in *Software Components*. These are currently managed in the App *Manage Software Components*. The parameter passed to this API needs to be the name of the Git repository on the ABAP environment system – the name of the Software Component.



## Procedure

1.  **\(Authentication on the Server\)**The first step serves the authentication on the server. The response header contains an x-csrf-token, which is used as authentication for the POST request following in *step 2*.

    **Request**

    ```
    GET/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY HTTP/1.1
    Host: host.com
    Authentication: basicAuthentication
    X-csrf-token: fetch
    
    ```

    **Response**

    ```
    HTTP/1.1 200 OK
    X-csrf-token: xCsrfToken
    
    ```

2.  **\(Pull a Git Repository\)** To trigger the pull of a Git repository, you have to insert the *x-csrf-token* that was retrieved in the first request in the header parameters. The Git repository you want to pull is passed in the body of the request.

    **Request**

    ```
    POST/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Pull HTTP/1.1
    Host: host.com
    Authentication: basicAuthentication
    X-csrf-token: xCsrfToken
    Content-Type: application/json
    Accept: application/json
    
    {
    	“sc_name” : “/DMO/GIT_REPOSITORY”
    }
    
    ```

    **Response**

    ```
    HTTP/1.1 200 OK
    Content-Type: application/json
    
    ```

    ```
    {
        "d": {
            "__metadata": {
                "id": "https://host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Pull(guid’UUID’)", "uri": "https://host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Pull(guid’UUID’)", "type": "cds_sd_a4c_a2g_gha_sc_web_api.PullType"
            }
            ,
            "uuid": "UUID ",
            "sc_name": "/DMO/GIT_REPOSITORY ",
            "namespace": "",
            "status": "R",
            "status_descr": "Running",
            "start_time": "/Date(1571227437000+0000)/",
            "change_time": "/Date(1571227472000+0000)/",
            "criticality": 2,
            "user_name": "CC0000000001",
            "to_Execution_log": {
                "__deferred": {
                    "uri": "https://host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Pull(guid’UUID’)/to_Execution_log"
                }
            }
            ,
            "to_Transport_log": {
                "__deferred": {
                    "uri": "https://host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Pull(guid’UUID’)/to_Transport_log"
                }
            }
        }
    }
    ```

3.  **\(Tracking the Status of the Pull\)** To track the status of the pull, you can make a GET request using the uuid contained in the response. You can also read the URI directly from the “\_\_metadata” of the response.

    **Request**

    ```
    GET/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Pull(guid’UUID’) HTTP/1.1
    Host: host.com
    Authentication: basicAuthentication
    Accept: application/json
    
    ```

    The response contains the same entity as the second request. The Pull is successful, when the “status” in the response body has the value **S**. The status description “status\_descr” will then return **Successful**. In case of an error “status” will have the value **E** and “status\_descr” the value **Error**.

4.  **\(Retrieving Logs\)** To get the Execution Log and the Transport Log after the Pull is finished, you can use the following requests. Alternatively, you can use the URIs from the response of the POST request. You can also check both logs in the *Manage Software Components* app for better readability.

    **For the Execution Log**:

    **Request**

    ```
    GET /sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Pull(guid’UUID’)/to_Execution_log HTTP/1.1
    Host: host.com
    Authentication: basicAuthentication
    Accept: application/json
    
    ```

    **Response**

    ```
    HTTP/1.1 200 OK
    Content-Type: application/json
    
    ```

    ```
    {
        "d": {
            "results": [ {
                "__metadata": {
                    "id": "host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/ExecutionLogs(index_no=1m,uuid=guid'UUID')", "uri": "host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/ExecutionLogs(index_no=1m,uuid=guid'UUID')", "type": "cds_sd_a4c_a2g_gha_sc_web_api.ExecutionLogsType"
                }
                ,
                "index_no": "1",
                "uuid": "UUID",
                "type": "Information",
                "descr": "Step X: MESSAGE",
                "timestamp": "/Date(1571227438000+0000)/",
                "criticality": 0,
            }
            ]
        }
    }
    
    
     
    
    ```

    **For the Transport Log**:

    **Request**

    ```
    GET /sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Pull(guid’UUID’)/to_Transport_log HTTP/1.1
    Host: host.com
    Authentication: basicAuthentication
    Accept: application/json
    
    ```

    **Response**

    ```
    HTTP/1.1 200 OK
    Content-Type: application/json
    
    ```

    ```
    {
        "d": {
            "results": [ {
                "__metadata": {
                    "id": "host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/ExecutionLogs(index_no=1m,uuid=guid'UUID')", "uri": "host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/ExecutionLogs(index_no=1m,uuid=guid'UUID')", "type": "cds_sd_a4c_a2g_gha_sc_web_api.ExecutionLogsType"
                }
                ,
                "index_no": "1",
                "uuid": "UUID",
                "type": "Information",
                "descr": "Step X: Message",
                "timestamp": "/Date(1571227438000+0000)/",
                "criticality": 0,
            }
            ]
        }
    }
    
    
     
    
    ```


