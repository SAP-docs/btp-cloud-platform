<!-- loiocade5df722f141dc9673fe031a31d77e -->

# Pulling Software Components to an ABAP Environment System

-   You have an ABAP environment system.

-   You’ve created a communication user as described in [How to Create Communication Users](https://help.sap.com/docs/btp/sap-business-technology-platform/how-to-create-communication-users?version=Cloud).

-   You’ve created a communication system as described in [How to Create Communication Systems](https://help.sap.com/docs/btp/sap-business-technology-platform/how-to-create-communication-systems?version=Cloud&q=how%20to%20create%20communication%20systems).

-   You’ve created a communication arrangement as described in [How to Create a Communication Arrangement](https://help.sap.com/docs/btp/sap-business-technology-platform/how-to-create-communication-arrangement?version=Cloud&q=how%20to%20create%20a%20communication%20arrangement).

-   You have selected the communication scenario SAP\_COM\_0948 for your communication arrangement and have mapped it to your communication system.

-   You have cloned the software component to the ABAP Environment system. See Cloning Software Components to an ABAP Environment System.


You can use the communication scenario SAP\_COM\_0948 to pull software components to an ABAP environment system.

1.  *Authentication to the server*

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

2.  *Pull a Software Component*

    To trigger the pull of a software component, you need to insert the `x-csrf-token` that was retrieved in the first request in the header parameters. The software component you want to pull is passed in path of the request URL.

    > ### Sample Code:  
    > ```
    > Request
    >     POST /sap/opu/odata4/sap/a4c_mswc_api/srvd_a2x/sap/manage_software_components/0001/SoftwareComponents/%2FDMO%2FCOMPONENT/SAP__self.pull HTTP/1.1
    >     Accept: application/json
    >     X-Csrf-Token: {{xcsrfToken}}
    >     Host: host.abapcp.int.sap
    >     Content-Length: 39
    > 
    >     {
    >     "commit_id": "",
    >     "tag_name": ""
    >     }
    > 
    > Response
    >  HTTP/1.1 200 OK
    >  Content-Type: application/json
    >     {
    >     "@odata.context": "../$metadata#Actions/$entity",
    >     "@odata.metadataEtag": "W/\"20240111143934\"",
    >     "uuid": "763eca2a-340b-1eee-ad8e-c864d7a77c38",
    >     "sc_name": "/DMO/COMPONENT",
    >     "import_type": "Pull",
    >     "branch_name": "master",
    >     "namespace": "",
    >     "status": "Q",
    >     "status_descr": "Scheduled",
    >     "criticality": 0,
    >     "user_name": "WebAPI - CC0000000009",
    >     "commit_id": "",
    >     "tag_name": "",
    >     "relative_date_change_time": "",
    >     "change_time": "2024-01-16T13:50:54Z",
    >     "start_time": "2024-01-16T13:50:54Z",
    >     "execution_mode": "",
    >     "import_mode": "",
    >     "SAP__Messages": []
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


