<!-- loio657285a09f7148d894c27bb8e17827cf -->

# Reading and Deploying ATC Configurations



<a name="loio657285a09f7148d894c27bb8e17827cf__prereq_ign_rdy_clb"/>

## Prerequisites

-   You have an SAP BTP ABAP environment system.

-   You’ve created a *Communication User* and generated a **password** as described in [How to Create Communication Users](../50-administration-and-ops/how-to-create-communication-users-0377ade.md).

-   You’ve created a *Communication System* as described in [How to Create Communication Systems](https://help.sap.com/docs/btp/sap-business-technology-platform/how-to-create-communication-systems?version=Cloud).
-   You’ve created a *Communication Arrangement* as described in [How to Create a Communication Arrangement](../50-administration-and-ops/how-to-create-a-communication-arrangement-a0771f6.md).

    > ### Note:  
    > The URL displayed for the inbound service of the communication arrangement will be needed for the GET requests described below.

-   You have selected the communication scenario **SAP\_COM\_0763** for your communication arrangement and have mapped it to your communication system.



## Context

The communication scenario **SAP\_COM\_0763** offers an OData V4 API for maintenance of ABAP Test Cockpit \(ATC\) configurations on the business objects `SATC_CI_CF_RT_E`, `SATC_CI_CF_E`, and `SATC_CI_CF_P_V`. Therefore, you have to create a valid communication arrangement as described in the prerequisites before performing the actual test steps.



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
    
2.  **Read ATC configurations:** To read ATC configurations, prepare a GET request using the following parameters:

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
    
    -   All configurations:

        **GET** <URL\_from\_Communication\_Arrangement\>/configuration

    -   By name:

        **GET** <URL\_from\_Communication\_Arrangement\>/configuration?$filter=conf\_name eq '<CONFNAME\>'

    -   Default configuration:

        **GET** <URL\_from\_Communication\_Arrangement/configuration?$filter=is\_default eq true


    If you want to look deeper into configuration data \(e.g. the priorities of the configuration\), you can use expands by adding:

    -   to all priorities: &$expand=\_priorities
    -   filtered only on priorities changed from default\_priority: &$expand=\_priorities\($filter=priority ne default\_priority\)

3.  **Deploy ATC configurations:** To deploy an ATC configuration, prepare a POST request and use the body to provide a json \(or XML\) representing the configuration you want to deploy.

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
    
    content-type


    
    </td>
    <td valign="top">
    
    application/json


    
    </td>
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
    
    **POST**<URL\_from\_Communication\_Arrangement\>/configuration

    -   Flat Insert of changed priorities:

        When you pass the json from the `get_configuration` with no expand by creating a valid configuration, the default priorities will also be created.

    -   Deep Insert of changed priorities:

        You can pass the json from the `get_configuration` with expand to filtered priorities and potentially change the `confname` if desired.



