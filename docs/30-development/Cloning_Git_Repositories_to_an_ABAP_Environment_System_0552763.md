<!-- loio0552763b6c184281893e808391ea5380 -->

# Cloning Git Repositories to an ABAP Environment System



<a name="loio0552763b6c184281893e808391ea5380__prereq_ksl_h54_qmb"/>

## Prerequisites

-   You have an ABAP environment system.

-   You’ve created a *Communication User* as described in [How to Create Communication Users](../50-administration-and-ops/How_to_Create_Communication_Users_0377ade.md).

-   You’ve created a *Communication System* as described in [How to Create Communication Systems](../50-administration-and-ops/How_to_Create_Communication_Systems_c2234ac.md)
-   You’ve created a *Communication Arrangement* as described in [How to Create a Communication Arrangement](../50-administration-and-ops/How_to_Create_a_Communication_Arrangement_a0771f6.md).

-   You have selected the communication scenario **SAP\_COM\_0510** for your communication arrangement and have mapped it to your communication system.



<a name="loio0552763b6c184281893e808391ea5380__context_anl_d54_qmb"/>

## Context

If a software component is not in your system yet, you will first need to clone it once to import it into your system.

> ### Note:  
> In ABAP environment, Git repositories are wrapped in software components. These are currently managed in the *Manage Software Components* app. The parameter `sc_name` passed to this API needs to be the name of the Git repository on the ABAP environment system – the name of the software component.



<a name="loio0552763b6c184281893e808391ea5380__steps_cfw_s54_qmb"/>

## Procedure

1.  **\(Authentication on the server\)**The first step serves the authentication on the server. The response header contains an x-csrf-token, which is used as authentication for the POST request following in *step 2*.

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

2.  **\(Cloning a Git repository\)**To trigger the clone, you need to insert the x-csrf-token that was retrieved in the first request in the header parameters. The Git repository and the branch you want to clone are passed in the body of the request. If you don’t enter a branch name, the main branch is automatically selected.

    **Request**

    ```
    POST/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Clones HTTP/1.1
    Host: host.com
    Authentication: basicAuthentication
    X-csrf-token: xCsrfToken
    Content-Type: application/json
    Accept: application/json
     
    {
            "sc_name" : "/DMO/GIT_REPOSITORY"
            "branch_name": "main"
    }
    
    ```

3.  **\(View all clones\)**To view all clones that have been made, you can make a GET request.

    **Request**

    ```
    GET /sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Clones HTTP/1.1
    Host: host.com
    Authentication: basicAuthentication
    Accept: application/json
    
    ```

    **Response**

    ```
    HTTP/1.1 200 OK
    Content-Type: application/json
    {
        "d": {
            "results": [
                {
                    "__metadata": {
                        "id": "host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Clones(uuid=guid'02ceab7d-ff04-1eda-b1ea-eb7fdbf28bc4',sc_name='ZHM_INITIAL_TEST',branch_name='')",
                        "uri": "host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Clones(uuid=guid'02ceab7d-ff04-1eda-b1ea-eb7fdbf28bc4',sc_name='ZHM_INITIAL_TEST',branch_name='')",
                        "type": "cds_sd_a4c_a2g_gha_sc_web_api.ClonesType"
                    },
                    "uuid": "02ceab7d-ff04-1eda-b1ea-eb7fdbf28bc4",
                    "sc_name": "/DMO/GIT_REPOSITORY",
                    "branch_name": "",
                    "import_type": "Clone",
                    "namespace": "",
                    "status": "S",
                    "status_descr": "Success",
                    "criticality": 3,
                    "user_name": "administrator@example.com",
                    "start_time": "/Date(1594898863000+0000)/",
                    "change_time": "/Date(1594898891000+0000)/"
                },
                   // all clones for this system instance will be listed here …
            ]
        }
    }
    
    ```


