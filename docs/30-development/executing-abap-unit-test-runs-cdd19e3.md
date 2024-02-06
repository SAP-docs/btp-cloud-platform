<!-- loiocdd19e3a5c49458291ec65d8d86e2b9a -->

# Executing ABAP Unit Test Runs



<a name="loiocdd19e3a5c49458291ec65d8d86e2b9a__prereq_ign_rdy_clb"/>

## Prerequisites

-   You have an SAP BTP ABAP environment system.

-   You’ve created a *Communication User* as described in [How to Create Communication Users](../50-administration-and-ops/how-to-create-communication-users-0377ade.md).

-   You’ve created a *Communication System* as described in [How to Create Communication Systems](https://help.sap.com/docs/btp/sap-business-technology-platform/how-to-create-communication-systems?version=Cloud).
-   You’ve created a *Communication Arrangement* as described in [How to Create a Communication Arrangement](../50-administration-and-ops/how-to-create-a-communication-arrangement-a0771f6.md).

-   You've selected the communication scenario **SAP\_COM\_0735** for your communication arrangement and have mapped it to your communication system.



<a name="loiocdd19e3a5c49458291ec65d8d86e2b9a__context_app_2gy_clb"/>

## Context

ABAP Unit is the standard tool for executing unit tests. In this help topic, you'll learn how to trigger an ABAP Unit Test Run via REST Service.

For more information about ABAP Unit, see [Ensuring Quality of ABAP Code](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide/ensuring-quality-of-abap-code?version=sap_btp).



<a name="loiocdd19e3a5c49458291ec65d8d86e2b9a__steps_vqt_dgz_klb"/>

## Procedure

1.  **Get CSRF token:** The first step serves for the authentication on the server. The response header contains a CSRF token, which is used as authentication for the POST request following in step 2.

    **Request**

    **Authentication Type**: Basic Authentication

    **GET** https://<host.com\>:<port\>/sap/bc/adt/api/abapunit/runs/00000000000000000000000000000000

    **Headers**


    <table>
    <tr>
    <th valign="top">

    KEY
    
    </th>
    <th valign="top">

    VALUE
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    accept
    
    </td>
    <td valign="top">
    
    application/vnd.sap.adt.api.abapunit.run-status.v1+xml
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    x-csrf-token
    
    </td>
    <td valign="top">
    
    fetch
    
    </td>
    </tr>
    </table>
    
    **Response**

    **Headers**


    <table>
    <tr>
    <th valign="top">

    KEY
    
    </th>
    <th valign="top">

    VALUE
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    x-csrf-token
    
    </td>
    <td valign="top">
    
    <token\>
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    location
    
    </td>
    <td valign="top">
    
    /sap/bc/adt/api/abapunit/runs/00000000000000000000000000000000
    
    </td>
    </tr>
    </table>
    
2.  **Trigger an ABAP Unit Run:** To trigger an ABAP Unit run, insert the**CSRF token** that was retrieved in the first request in the header parameters.

    **Request**

    **POST** https://<host.com\>:<port\>/sap/bc/adt/api/abapunit/runs

    **Headers**


    <table>
    <tr>
    <th valign="top">

    KEY
    
    </th>
    <th valign="top">

    VALUE
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    x-csrf-token
    
    </td>
    <td valign="top">
    
    <token\>
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    content type
    
    </td>
    <td valign="top">
    
    application/vnd.sap.adt.api.abapunit.run.v1+xml
    
    </td>
    </tr>
    </table>
    
    **Body**

    You can specify arbitrary object sets. See also [Object Sets](https://help.sap.com/docs/btp/sap-abap-development-user-guide/objects-sets) and [XML Representations of Object Sets](https://help.sap.com/docs/btp/sap-abap-development-user-guide/xml-representations-of-object-sets) for more details.

    You can provide additional parameters to control the selection of tests. You can restrict the amount of tests to certain risk level and durations. Furthermore, you can decide to execute foreign tests, which are connected via test relations.

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <aunit:run title="My Run" context="AIE Integration Test" xmlns:aunit="http://www.sap.com/adt/api/aunit">
      <aunit:options>
        <aunit:measurements type="none"/>
        <aunit:scope ownTests="true" foreignTests="true"/>
        <aunit:riskLevel harmless="true" dangerous="true" critical="true"/>
        <aunit:duration short="true" medium="true" long="true"/>
      </aunit:options>
      <osl:objectSet xsi:type="unionSet" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:osl="http://www.sap.com/api/osl">
       <osl:set xsi:type="osl:packageSet">
         <osl:package includeSubpackages="true" name="PACKAGE_ONE"/>
       </osl:set>
       <osl:set xsi:type="osl:flatObjectSet">
         <osl:object name="ZCL_TEST_ONE" type="CLAS"/>
         <osl:object name="ZIF_TEST_TWO" type="INTF"/>
       </osl:set>
      </osl:objectSet>
    </aunit:run>
    ```

    **Response**

    **Headers**


    <table>
    <tr>
    <th valign="top">

    KEY
    
    </th>
    <th valign="top">

    VALUE
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    location
    
    </td>
    <td valign="top">
    
    /sap/bc/adt/api/abapunit/runs/\{runId\}
    
    </td>
    </tr>
    </table>
    
3.  **Tracking the Status of the Test Run:**To track the status of the test run, you can make a GET request using the URI contained in the location header.

    **Request**

    **GET** https://<host.com\>:<port\>/sap/bc/adt/api/abapunit/runs/\{runId\}

    **Headers**


    <table>
    <tr>
    <th valign="top">

    KEY
    
    </th>
    <th valign="top">

    VALUE
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    accept
    
    </td>
    <td valign="top">
    
    application/vnd.sap.adt.api.abapunit.run-status.v1+xml
    
    </td>
    </tr>
    </table>
    
    **Response**

    While the tests are still running, the returned status will be ”In Process”.

    If all tests have been executed, the status “Completed” is returned. You'll find the link /sap/bc/adt/api/atc/results/<UUID\> at the bottom of the body. Use this link to retrieve the ABAP Unit test results in the next step.

    **Body**

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <aunit:run xmlns:aunit="http://www.sap.com/adt/api/aunit" title="MyTitle" context="MyContext">
      <aunit:progress status="FINISHED" percentage="100" />
      <aunit:executedBy user="JOHNDOE" />
      <aunit:time started="2021-02-12T17:09:19Z" ended="2021-02-12T17:09:22Z" />
      <atom:link xmlns:atom="http://www.w3.org/2005/Atom" href="/sap/bc/adt/api/abapunit/results/0123821392189313" rel="http://www.sap.com/adt/relations/api/abapunit/run-result" type="application/vnd.sap.adt.api.junit.run-result.v1+xml"/>
    </aunit:run>
    ```

4.  **Retrieve Results:** To get the ABAP Unit results, use the following request.

    **Request**

    **GET**https://<host.com\>:<port\>/sap/bc/adt/api/abapunit/results/\{resultId\}

    **Headers**


    <table>
    <tr>
    <th valign="top">

    KEY
    
    </th>
    <th valign="top">

    VALUE
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Accept
    
    </td>
    <td valign="top">
    
    application/vnd.sap.adt.api.junit.run-result.v1+xml
    
    </td>
    </tr>
    </table>
    
    **Response**

    The results are submitted in the JUnit format.

    **Body**

    As an example, the result may look like this:

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <testsuites tests="3" asserts="2" skipped="1" errors="0" failures="1" timestamp="2021-01-22T19:17:30Z" time="0.36" executedBy="JOHNDOE" client="000" system="UIA">
        <testsuite tests="2" asserts="2" skipped="1" errors="0" failures="1" timestamp="2021-01-22T19:17:30Z" time="0.28 " hostname="ldai3uia" package="test_cars" name="">
            <testcase asserts="1" time="0.01 " name="order" classname="fugr:zmg_cars.ltc_finder">
                <failure type="Assert Failure" message="Critical Assertion Error: 'Cds_View: ASSERT_EQUALS'">
                Character string different as of position 4Expected [CL_AUNIT_TESTABLE_OBJECT======CP]Actual [CL_CAR========================CP] Test 'LTC_FINDER->ORDER' in Main Program 'SAPLZMG_CARS'
                Stack: Include: <LZMG_CARST99> Line: <38> (ORDER)
                </failure>
            </testcase>
            <testcase asserts="1" time="0.01 " name="preview" classname="fugr:zmg_cars.ltc_finder">
                <skipped message="Missing Prerequisites - Dummy: ABORT">
                Test execution skipped due to missing prerequisites Test 'LTC_FINDER->PREVIEW' in Main Program 'SAPLZMG_CARS'
                Stack: Include: <LZMG_CARST99> Line: <44> (PREVIEW)
                </skipped>
            </testcase>
            <testcase asserts="0" time="0.01 " name="drive" classname="fugr:zmg_cars.ltc_finder"/>
        </testsuite>
    </testsuites>
    ```


