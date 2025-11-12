<!-- loio9fa6bcfc1ca74e3c8ba5cdb8130f9805 -->

# Reading ATC Results



## Prerequisites

-   You have an SAP BTP ABAP environment system.

-   You’ve created a *Communication User* and generated a **password** as described in [How to Create Communication Users](../50-administration-and-ops/how-to-create-communication-users-0377ade.md).

-   You’ve created a *Communication System* as described in [How to Create Communication Systems](https://help.sap.com/docs/btp/sap-business-technology-platform/how-to-create-communication-systems?version=Cloud).
-   You’ve created a *Communication Arrangement* as described in [How to Create a Communication Arrangement](../50-administration-and-ops/how-to-create-a-communication-arrangement-a0771f6.md).

    > ### Note:  
    > The URL displayed for the inbound service of the communication arrangement will be needed for the GET requests described below.

-   You have selected the communication scenario **SAP\_COM\_0A59** for your communication arrangement and have mapped it to your communication system.



## Context

The communication scenario `SAP_COM_0A59` provides an OData V4 API for reading ABAP Test Cockpit \(ATC\) results, including their findings, potential run failures, and descriptions. It also offers navigation information for findings.



## Procedure

1.  **Get CSRF token:** The first step serves for the authentication on the server. Use the URL you've obtained from the *Communication Arrangement*'s inbound service for the **GET** request. The response header contains an CSRF token, which is used as authentication for the GET request following in step 2.

    **Request**

    **Authentication Type**: Basic Authentication. Enter the name of your *Communication User* \(not the technical user ID\) and the generated password.

    **GET** <URL\_from\_Communication\_Arrangement\>

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
    </table>
    
2.  **Read ATC results:** To read ATC results, prepare a GET request using the following parameters:

    **Request**

    **Header**


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
    </table>
    
    -   ATC Findings:

        **GET** <URL\_from\_Communication\_Arrangement\>/SATC\_API\_FINDINGS\_C

    -   ATC Item Description Data:

        **GET** <URL\_from\_Communication\_Arrangement\>/SATC\_API\_RAW\_DESCR\_C

    -   ATC Item Navigation Data:

        **GET** <URL\_from\_Communication\_Arrangement\>/SATC\_API\_RAW\_NAV\_C

    -   ATC Result Headers:

        **GET** <URL\_from\_Communication\_Arrangement\>/SATC\_API\_RESULT\_HEADERS\_C

    -   ATC Run Failures:

        **GET** <URL\_from\_Communication\_Arrangement\>/SATC\_API\_RUN\_FAILURES\_C



