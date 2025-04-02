<!-- loio7d529e1545c34e8aa4f8f22b511520c5 -->

# Working with Branches on a Software Component

-   You have an ABAP environment system.

-   You’ve created a communication user as described in [How to Create Communication Users](https://help.sap.com/docs/btp/sap-business-technology-platform/how-to-create-communication-users?version=Cloud).

-   You’ve created a communication system as described in [How to Create Communication Systems](https://help.sap.com/docs/btp/sap-business-technology-platform/how-to-create-communication-systems?version=Cloud&q=how%20to%20create%20communication%20systems).

-   You’ve created a communication arrangement as described in [How to Create a Communication Arrangement](https://help.sap.com/docs/btp/sap-business-technology-platform/how-to-create-communication-arrangement?version=Cloud&q=how%20to%20create%20a%20communication%20arrangement).

-   You have selected the communication scenario `SAP_COM_0948` for your communication arrangement and have mapped it to your communication system.

-   You have cloned the software component to the ABAP environment system. See [Cloning Software Components to an ABAP Environment System](cloning-software-components-to-an-abap-environment-system-383ce2f.md).


You can use the communication scenario `SAP_COM_0948` to work with software components on a SAP BTP ABAP environment system.

1.  *Authentification on the server*

    The first step serves the authentication on the server. The response header contains an `x-csrf-token`, which is used as authentication for the POST request following in step 2 and 3.

    > ### Sample Code:  
    > ```
    > Request
    >     GET /sap/opu/odata4/sap/a4c_mswc_api/srvd_a2x/sap/manage_software_components/0001 HTTP/1.1
    >     Accept: application/json
    >     X-Csrf-Token: fetch
    >     Host: host.sap
    > 
    > Response
    >     HTTP/1.1 200 OK
    >     X-csrf-token: xCsrfToken
    > 
    > ```

2.  *Create a Branch*

    To create a branch, you perform a `POST` request on the `Branches` entity. In the header parameters, you should include the `x-csrf-token` that was retrieved in the first request. Fill in the following data in your request body:

    1.  `sc_name`: the name of your software component

    2.  `branch_name`: the name of your new branch
    3.  `derived_from`: the branch that your new branch should derive from


    > ### Sample Code:  
    > ```
    > Request
    >     POST /sap/opu/odata4/sap/a4c_mswc_api/srvd_a2x/sap/manage_software_components/0001/Branches HTTP/1.1
    >     Accept: application/json
    >     X-Csrf-Token: {{xcsrfToken}}
    >     Host: host.abapcp.int.sap
    >     Content-Length: 103
    > 
    >     {
    >         "sc_name" : "/DMO/COMPONENT",
    >         "branch_name" : "feature",
    >         "derived_from" : "main"
    >     }
    > 
    > Response
    >     HTTP/1.1 201 Created
    >     Content-Type: application/json
    >     {
    >         "@odata.context": "$metadata#Branches/$entity",
    >         "@odata.metadataEtag": "W/\"20240111143934\"",
    >         "sc_name": "/DMO/COMPONENT",
    >         "branch_name": "feature",
    >         "is_active": false,
    >         "criticality": 0,
    >         "delta": "Please checkout first",
    >         "delta_criticality": 0,
    >         "derived_from": "main",
    >         "name_of_new_branch": "",
    >         "commit_id": "",
    >         "commit_message": "",
    >         "last_commit_by": "",
    >         "relative_date_last_rem_commit": "",
    >         "last_commit_on": null,
    >         "commit_id_on_system": "-",
    >         "created_by": "CC0000000009",
    >         "created_on": "2024-01-16T14:00:00Z",
    >         "execution_mode": "",
    >         "import_mode": "",
    >         "SAP__Messages": []
    >     }
    > 
    > ```

3.  *Check Out a Branch*

    Simply creating a branch did not change the state of the system. In order to work with the newly created branch, you need to import the branch to the system. This action is called *checkout branch*. You need to include the software component and the name of the branch in the path of the request URL.

    > ### Sample Code:  
    > ```
    > Request
    >       POST /sap/opu/odata4/sap/a4c_mswc_api/srvd_a2x/sap/manage_software_components/0001/Branches/%2FDMO%2FCOMPONENT/main/SAP__self.checkout_branch HTTP/1.1
    >         Accept: application/json
    >         X-Csrf-Token: {{xcsrfToken}}
    >         Host: host.abapcp.int.sap
    >         Content-Length: 44
    >         {
    >             "import_mode" : "",
    >             "execution_mode": ""
    >         }
    > 
    > Response
    >       HTTP/1.1 200 OK
    >       Content-Type: application/json
    >       {
    >         "@odata.context": "../$metadata#com.sap.gateway.srvd_a2x.a4c_a2g_mswc_api.v0001.ActionsType",
    >         "@odata.metadataEtag": "W/\"20240111143934\"",
    >         "uuid": "96bbf3e1-5202-1ede-ad8f-001e560df4e6",
    >         "sc_name": "/DMO/FCOMPONENT",
    >         "import_type": "Checkout",
    >         "branch_name": "main",
    >         "namespace": "",
    >         "status": "Q",
    >         "status_descr": "Scheduled",
    >         "criticality": 0,
    >         "user_name": "WebAPI - CC0000000009",
    >         "commit_id": "",
    >         "tag_name": "",
    >         "relative_date_change_time": "",
    >         "change_time": "2024-01-16T14:03:22Z",
    >         "start_time": "2024-01-16T14:03:21Z",
    >         "execution_mode": "",
    >         "import_mode": "",
    >         "SAP__Messages": []
    >       }
    > 
    > ```

4.  *Tracking the Status of the Action*

    To track the status of the action, you can do a `GET` request using the UUID contained in the response.

    > ### Sample Code:  
    > ```
    > Request
    >     GET /sap/opu/odata4/sap/a4c_mswc_api/srvd_a2x/sap/manage_software_components/0001/Actions/96bbf3e1-5202-1ede-ad8e-b46db5437410 HTTP/1.1
    >     Accept: application/json
    >     Host: host.abapcp.int.sap
    > 
    > ```

    The response contains the same entity as the second request. The action is successful, when the *status* in the response body has the value *S*. The status description *status\_descr* will then return *Successful* . In case of an error *status* will have the value *E* and *status\_descr* the value *Error*.


