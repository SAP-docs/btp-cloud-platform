<!-- loio383ce2f9e2eb40f1b8ad538ddf79e656 -->

# Cloning Software Components to an ABAP Environment System

-   You have an ABAP environment system.

-   You have created a communication user as described in [How to Create Communication Users](https://help.sap.com/docs/btp/sap-business-technology-platform/how-to-create-communication-users?version=Cloud).

-   You’ve created a communication system as described in [How to Create Communication Systems](https://help.sap.com/docs/btp/sap-business-technology-platform/how-to-create-communication-systems?version=Cloud&q=how%20to%20create%20communication%20systems).

-   You’ve created a communication arrangement as described in [How to Create a Communication Arrangement](https://help.sap.com/docs/btp/sap-business-technology-platform/how-to-create-communication-arrangement?version=Cloud&q=how%20to%20create%20a%20communication%20arrangement).

-   You have selected the communication scenario SAP\_COM\_0948 for your communication arrangement and have mapped it to your communication system.


If a software component is not in your system yet, you will first need to clone it once to import it into your system. Please note that you can clone a software component only once into your system.

1.  *Authentication on the server*

    The first step serves the authentication on the server. The response header contains an `x-csrf-token`, which is used as authentication for the `POST` request following in step 2.

    > ### Sample Code:  
    > ```
    > Request
    > GET /sap/opu/odata4/sap/a4c_mswc_api/srvd_a2x/sap/manage_software_components/0001 HTTP/1.1
    > Accept: application/json
    > X-Csrf-Token: fetch
    > Host: host.sap
    > 
    > Response
    > HTTP/1.1 200 OK
    > X-csrf-token: xCsrfToken
    > ```

2.  *Cloning a Software Component*

    To trigger the clone, you need to insert the `x-csrf-token` that was retrieved in the first request in the header parameters. The software component is passed in the path of the request URL. The branch you want to clone is passed in the body of the request. If you don’t enter a branch name, the main branch is automatically selected. Alternatively, you can clone a specific tag or commit ID by entering the tag name or commit ID. Make sure that the tag or commit ID exists on the branch. If that's not the case, no clone action will be executed.

    > ### Sample Code:  
    > ```
    > Request
    >     POST /sap/opu/odata4/sap/a4c_mswc_api/srvd_a2x/sap/manage_software_components/0001/SoftwareComponents/%2FDMO%2FCOMPONENT/SAP__self.clone HTTP/1.1
    > Accept: application/json
    > X-Csrf-Token: {{xcsrfToken}}
    > Host: host.abapcp.int.sap
    > Content-Length: 122
    >     {
    >     "commit_id": "",
    >     "branch_name": "main",
    >     "tag_name": "",
    >     }
    > 
    > Response
    >     HTTP/1.1 200 OK
    >     Content-Type: application/json
    >     {
    >         "@odata.context": "../$metadata#Actions/$entity",
    >         "@odata.metadataEtag": "W/\"20240111143934\"",
    >         "uuid": "96bbf3e1-5202-1ede-ad8e-b46db5437410",
    >         "sc_name": "/DMO/COMPONENT",
    >         "import_type": "Clone",
    >         "branch_name": "main",
    >         "namespace": "",
    >         "status": "Q",
    >         "status_descr": "Scheduled",
    >         "criticality": 0,
    >         "user_name": "WebAPI - CC0000000009",
    >         "commit_id": "",
    >         "tag_name": "",
    >         "relative_date_change_time": "",
    >         "change_time": "2024-01-16T13:46:26Z",
    >         "start_time": "2024-01-16T13:46:26Z",
    >         "execution_mode": "",
    >         "import_mode": "",
    >         "SAP__Messages": []
    >     }
    > 
    > ```

3.  *Tracking the Status of the Action*

    To track the status of the action, you can do a GET request using the UUID contained in the response.

    > ### Sample Code:  
    > ```
    > Request
    >     GET /sap/opu/odata4/sap/a4c_mswc_api/srvd_a2x/sap/manage_software_components/0001/Actions/96bbf3e1-5202-1ede-ad8e-b46db5437410 HTTP/1.1
    >     Accept: application/json
    >     Host: host.abapcp.int.sap
    > 
    > ```

    The response contains the same entity as the second request. The action is successful, when the *status* in the response body has the value *S*. The status description *status\_descr* will then return *Successful* . In case of an error *status* will have the value *E* and *status\_descr* the value *Error*.


