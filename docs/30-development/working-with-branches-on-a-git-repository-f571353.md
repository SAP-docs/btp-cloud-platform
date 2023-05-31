<!-- loiof571353ba0c24f37bd77c8b4b8ff5530 -->

# Working with Branches on a Git Repository



<a name="loiof571353ba0c24f37bd77c8b4b8ff5530__prereq_ign_rdy_clb"/>

## Prerequisites

-   You have an ABAP environment system.

-   You’ve created a *Communication User* as described in [How to Create Communication Users](../50-administration-and-ops/how-to-create-communication-users-0377ade.md).

-   You’ve created a *Communication System* as described in [How to Create Communication Systems](https://help.sap.com/docs/btp/sap-business-technology-platform/how-to-create-communication-systems?version=Cloud).
-   You’ve created a *Communication Arrangement* as described in [How to Create a Communication Arrangement](../50-administration-and-ops/how-to-create-a-communication-arrangement-a0771f6.md).

-   You have selected the communication scenario **SAP\_COM\_0510** for your communication arrangement and have mapped it to your communication system.
-   You have a Git repository/ software component with a main branch. A main branch is created when you push content to the repository for the first time, i.e. you release a transport request for the repository/ software component.



<a name="loiof571353ba0c24f37bd77c8b4b8ff5530__context_app_2gy_clb"/>

## Context

You can use the communication scenario `SAP_COM_0510` to work with Git repositories on an SAP BTP, ABAP environment system.

> ### Note:  
> In ABAP Environment, Git repositories are wrapped in software components. These are currently managed in the *Manage Software Components* app. The technical parameter `sc_name` used in this API needs to be the name of the Git repository on the ABAP Environment system – the name of the software component.



<a name="loiof571353ba0c24f37bd77c8b4b8ff5530__steps_bgs_k42_dlb"/>

## Procedure

1.  **\(Authentication on the Server\)** The first step serves the authentication on the server. The response header contains an x-csrf-token, which is used as authentication for the `POST` request following in *step 2*.

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

2.  **\(Clone a Git Repository\)** If a software component is not yet in your system, you first need to clone it once to import it into your system. For more information on how to do this, see [Cloning Git Repositories to an ABAP Environment System](cloning-git-repositories-to-an-abap-environment-system-0552763.md).

3.  **\(Pull a Git Repository\)** In order to work with branches, the Git repository needs to be pulled to the system. For more information on how to do this, see [Pulling Git Repositories to an ABAP Environment System](pulling-git-repositories-to-an-abap-environment-system-80a8d52.md).

4.  **\(Create a Branch\)** To create a branch, you perform a `POST` request on the `Branches` entity. In the header parameters, you should include the x-csrf-token that was retrieved in the first request. Fill in the following data in your request body:

    1.  "sc\_name": the name of your Git repository
    2.  "branch\_name": the name of your new branch
    3.  "derived\_from": the branch that your new branch should derive from

    **Request**

    ```
    POST/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Branches HTTP/1.1
    Host: host.com
    Authentication: basicAuthentication
    X-csrf-token: xCsrfToken
    Content-Type: application/json
    Accept: application/json
    	{
    "sc_name" : "/DMO/GIT_REPOSITORY",
    "derived_from" : "main",
    "branch_name" : "newBranch"
    	}
    ```

    **Response**

    ```
    HTTP/1.1 200 OK
    Content-Type: application/json
    
    {
    	"d": {
    		"__metadata": {
    			"id": "https://host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Branches(branch_name='newBranch',sc_name='/DMO/GIT_REPOSITORY')",
    			"uri": "https://host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Branches(branch_name='newBranch',sc_name='/DMO/GIT_REPOSITORY')",
    			"type": "cds_sd_a4c_a2g_gha_sc_web_api.BranchesType"
    		},
    		"branch_name": "newBranch",
    		"sc_name": "/DMO/GIT_REPOSITORY",
    		"is_active": false,
    		"criticality": 0,
    		"derived_from": "main",
    		"created_by": "CC0000000001",
    		"created_on": "/Date(1584967657000+0000)/",
    		"last_commit_on": "/Date(1584634658000+0000)/"
    	}
    }
    ```

5.  **\(GET the Branch\)** To read the branch entity, you can use the following request:

    **Request**

    ```
    GET /sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Branches(branch_name=’newBranch’,sc_name=’/DMO/GIT_REPOSITORY’ HTTP/1.1
    
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
    		"__metadata": {
    			"id": "https://host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Branches(branch_name='newBranch',sc_name='/DMO/GIT_REPOSITORY')",
    			"uri": "https://host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Branches(branch_name='newBranch',sc_name='/DMO/GIT_REPOSITORY')",
    			"type": "cds_sd_a4c_a2g_gha_sc_web_api.BranchesType"
    		},
    		"branch_name": "newBranch",
    		"sc_name": "/DMO/GIT_REPOSITORY",
    		"is_active": false,
    		"criticality": 0,
    		"derived_from": "main",
    		"created_by": "CC0000000001",
    		"created_on": "/Date(1584967657000+0000)/",
    		"last_commit_on": "/Date(1584634658000+0000)/"
    	}
    }
    ```

6.  > ### Note:  
    > Please note that the newly created branch is not yet active.

7.  **\(Checkout a Branch\)** Simply creating a branch did not change the state of the system. In order to work with the newly created branch, you need to import the branch to the system. This action is called "checkout branch". You need to pass the Git repository and the name of the branch as query parameters.

    **Request**

    ```
    POST/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/checkout_branch?branch_name='newBranch'&sc_name="'/DMO/GIT_REPOSITORY' HTTP/1.1
    
    Host: host.com
    Authentication: basicAuthentication
    X-csrf-token: xCsrfToken
    Content-Type: application/json
    Accept: application/json
    ```

    **Response**

    ```
    HTTP/1.1 200 OK
    
    Content-Type: application/json
    
    {
    
    	"d": {
    		"__metadata": {
    			"id": "https://host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Pull(guid’UUID’)", 
    			"uri": "https://host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Pull(guid’UUID’)", 
    			"type": "cds_sd_a4c_a2g_gha_sc_web_api.PullType"
    		},
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
    		},
    
    		"to_Transport_log": {
    			"__deferred": {
    				"uri": "https://host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Pull(guid’UUID’)/to_Transport_log"
    			}
    		}
    	}
    }
    ```

    Behind the scenes, a `Pull` entity is created. It can be used to track the status of the checkout \(see steps 3 and 4 in [Pulling Git Repositories to an ABAP Environment System](pulling-git-repositories-to-an-abap-environment-system-80a8d52.md)\). This entity is specified in the `__metadata` of the response body.

8.  **\(Delete a Branch\)** You can delete existing branches. Keep in mind, however, that neither the current active branch nor the main branch can be deleted. Both parameters are mandatory.

    **Request**

    ```
    DELETE /sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Branches(branch_name='my-to-be-deleted-branch',sc_name='/DMO/GIT_REPOSITORY') HTTP/1.1
    Host: host.com
    Authentication: basicAuthentication
    Accept: application/json
    
    ```

    **Response**

    Since you're using a DELETE request, an HTTP 204 code is returned as confirmation that your branch has successfully been deleted.

    ```
    HTTP/1.1 204 No Content
    ```


