<!-- loiod8cec788fc104ff9ad9c3757b4dd13d4 -->

# Executing ABAP Test Cockpit \(ATC\) Check Runs



<a name="loiod8cec788fc104ff9ad9c3757b4dd13d4__prereq_ign_rdy_clb"/>

## Prerequisites

-   You have an SAP BTP, ABAP environment system.

-   You’ve created a *Communication User* as described in [How to Create Communication Users](../50-administration-and-ops/How_to_Create_Communication_Users_0377ade.md).

-   You’ve created a *Communication System* as described in [How to Create Communication Systems](../50-administration-and-ops/How_to_Create_Communication_Systems_c2234ac.md)
-   You’ve created a *Communication Arrangement* as described in [How to Create a Communication Arrangement](../50-administration-and-ops/How_to_Create_a_Communication_Arrangement_a0771f6.md).

-   You have selected the communication scenario **SAP\_COM\_0510** for your communication arrangement and have mapped it to your communication system.
-   You have defined a business user in the additional properties in the communication arrangement. To do so, click the *Additional Properties* link for ATC Check Run in the *Inbound Services* section. Specify a business user \(CB\) or select a user from the value help. ATC runs started via the service will be scheduled and executed with the specified business user.

    > ### Note:  
    > The assigned business user needs development authorization for ADT, which is contained in the business catalog`SAP_A4C_BC_DEV_PC` or in the business role template `SAP_BR_DEVELOPER`. In case the ATC is used to execute ABAP Unit Tests, further specific authorizations might be required.




<a name="loiod8cec788fc104ff9ad9c3757b4dd13d4__context_app_2gy_clb"/>

## Context

The ABAP Test Cockpit \(ATC\) is the standard tool for checking the quality of ABAP development objects using static checks and ABAP unit tests. In this help topic you will learn how to trigger an ATC Check Run via REST Service.

For more information about ABAP Test Cockpit, see [Checking Quality of ABAP Code with ATC](https://help.sap.com/viewer/c238d694b825421f940829321ffa326a/latest/en-US/4ec5711c6e391014adc9fffe4e204223.html).



<a name="loiod8cec788fc104ff9ad9c3757b4dd13d4__steps_vqt_dgz_klb"/>

## Procedure

1.  **\(Get CSRF token\)** The first step serves for the authentication on the server. The response header contains an CSRF token, which is used as authentication for the POST request following in step 2.

    **Request**

    **Authentication Type**: Basic Authentication

    **GET** https://<host.com\>:<port\>/sap/bc/adt/api/atc/runs/00000000000000000000000000000000

    **Headers**


    <table>
    <tr>
    <th>

    KEY


    
    </th>
    <th>

    VALUE


    
    </th>
    </tr>
    <tr>
    <td>

    accept


    
    </td>
    <td>

    application/vnd.sap.atc.run.v1+xml


    
    </td>
    </tr>
    <tr>
    <td>

    x-csrf-token


    
    </td>
    <td>

    fetch


    
    </td>
    </tr>
    </table>
    
    **Response**

    **Body**

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <atc:run status="Not Created" xmlns:atc="http://www.sap.com/adt/atc">
        <atc:progress description="No run was created, no objects had to be checked"/>
        <atc:phases/>
    </atc:run>
    
    ```

    **Headers**


    <table>
    <tr>
    <th>

    KEY


    
    </th>
    <th>

    VALUE


    
    </th>
    </tr>
    <tr>
    <td>

    x-csrf-token


    
    </td>
    <td>

    <token\>


    
    </td>
    </tr>
    <tr>
    <td>

    location


    
    </td>
    <td>

    /sap/bc/adt/atc/runs/00000000000000000000000000000000


    
    </td>
    </tr>
    </table>
    
2.  **\(Trigger an ATC Check Run\)** To trigger an ATC check run, insert the**CSRF token** that was retrieved in the first request in the header parameters.

    **Request**

    **POST** https://<host.com\>:<port\>/sap/bc/adt/api/atc/runs?clientWait=false

    **Headers**


    <table>
    <tr>
    <th>

    KEY


    
    </th>
    <th>

    VALUE


    
    </th>
    </tr>
    <tr>
    <td>

    x-csrf-token


    
    </td>
    <td>

    <token\>


    
    </td>
    </tr>
    <tr>
    <td>

    content type


    
    </td>
    <td>

    application/vnd.sap.atc.run.parameters.v1+xml


    
    </td>
    </tr>
    </table>
    
    **Body**

    You can specify components, packages or both. If you specify both components and packages, only those objects will be checked that are assigned to packages which belong to the specified software components.

    For the package value, enter the name of the package you want to have checked.

    To include subpackages, you need to state `includeSubpackages=”true”`.

    You can provide an ATC configuration as additional parameter which is used instead of the default configuration of your system.

    You can also provide an ATC check variant as additional parameter. This is used instead of the default check variant of your ATC configuration, regardless of whether an ATC configuration was explicitly provided via parameter or not.

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <atc:runparameters xmlns:atc="http://www.sap.com/adt/atc"
             xmlns:obj="http://www.sap.com/adt/objectset"
             checkVariant="CHECKVARIANT_NAME"
             configuration="CONFIGURATION_NAME">
      <obj:objectSet>
          <obj:softwarecomponents>       
            <obj:softwarecomponent value="SAP_BASIS"/>
          </obj:softwarecomponents>
          <obj:packages>
            <obj:package value="Z_MY_PACKAGE" includeSubpackages="true"/>
          </obj:packages>
       </obj:objectSet>
    </atc:runparameters>
    
    
    ```

    **Response**

    **Headers**


    <table>
    <tr>
    <th>

    KEY


    
    </th>
    <th>

    VALUE


    
    </th>
    </tr>
    <tr>
    <td>

    location


    
    </td>
    <td>

    /sap/bc/adt/api/atc/runs/<UUID\>


    
    </td>
    </tr>
    </table>
    
3.  **\(Tracking the Status of the Check Run\)**To track the status of the check run, you can make a GET request using the URI contained in the location header.

    **Request**

    **GET** https://<host.com\>:<port\>/sap/bc/adt/api/atc/runs/<UUID\>

    **Headers**


    <table>
    <tr>
    <th>

    KEY


    
    </th>
    <th>

    VALUE


    
    </th>
    </tr>
    <tr>
    <td>

    accept


    
    </td>
    <td>

    application/vnd.sap.atc.run.v1+xml


    
    </td>
    </tr>
    </table>
    
    **Response**

    While the check is still running, the ATC phases will show the status ”In Process” or “Undefined” in the body.

    The check run is finished when all ATC phases show the status “Completed”. You will find the link /sap/bc/adt/api/atc/results/<UUID\> at the bottom of the body. Use this link to retrieve the ATC check run results in the next step.

    **Body**

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <atc:run status="Completed" xmlns:atc="http://www.sap.com/adt/atc">
        <atc:progress description="Run Completed"/>
        <atc:phases>
            <atc:phase title="Determine Object Keys" status="Completed" number="1"/>
            ...
        </atc:phases>
        <atom:link href="/sap/bc/adt/api/atc/results/<UUID>" rel="http://www.sap.com/abap/checks/atc/relations/results/displayid" type="application/xml" title="Result" xmlns:atom="http://www.w3.org/2005/Atom"/>
    </atc:run>
    
    ```

4.  **\(Retrieve Results\)** To get the ATC results, use the following request.

    **Request**

    **GET** /sap/bc/adt/api/atc/results/<UUID\>

    **Headers**


    <table>
    <tr>
    <th>

    KEY


    
    </th>
    <th>

    VALUE


    
    </th>
    </tr>
    <tr>
    <td>

    Accept


    
    </td>
    <td>

    application/vnd.sap.atc.checkstyle.v1+xml


    
    </td>
    </tr>
    </table>
    
    **Response**

    The results are submitted in the checkstyle format. You can find the checkstyle XSD here: [https://github.com/linkedin/pygradle/blob/master/pygradle-plugin/src/test/resources/checkstyle/checkstyle.xsd](https://github.com/linkedin/pygradle/blob/master/pygradle-plugin/src/test/resources/checkstyle/checkstyle.xsd).

    **Body**

    As an example, the result may look like this:

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <checkstyle version="1.0">
        <file name="PACKAGE/OBJECT_NAME.OBJECT_TYPE">
        <error message="Hard-coded user name (@User's formatted name)" source="CL_CI_TEST_EXTENDED_CHECK_SEC#0821" line="2" severity="error"/>
    </checkstyle>
    
    ```

    In this example, the error message shows a hard-coded username. Ideally, the formatted user name corresponds to the developer that edited the object for the last time. In case "last changed by" should not be available for the object, the author is used instead. In case the formatted user name cannot be determined, the business user id is displayed as fallback.

    > ### Note:  
    > In the output, the namespace slashes will be replaced by dashes. That means `/NAMESPACE/OBJECT_NAME` will be output as `-NAMESPACE-OBJECT_NAME`.


