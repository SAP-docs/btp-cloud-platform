<!-- loioa69e99c457a54ff881adcff843eea950 -->

# Set Up an RFC Destination

Set up RFC connectivity for the ABAP environment by configuring a destination of type RFC.

To configure an RFC destination in the SAP BTP cockpit, perform the following steps:

1.  Navigate to the relevant destination service instance.

    > ### Note:  
    > Instead of creating a destination from your own Destination service instance, you can configure destinations directly on subaccount level, in the subaccount in which the ABAP instance resides \(recommended\). See also [Integrating On-Premise Systems](Integrating_On-Premise_Systems_c95327f.md).

2.  In the menu, navigate to *Destinations*.
3.  Create a destination by selecting *New Destination*.
4.  Enter a destination *<Name\>*.
5.  For *<Type\>*, select ***RFC*** from the value help.
6.  \(Optional\) Enter a description for the destination.
7.  Specify the destination *<URL\>*.
8.  For *<Proxy Type\>*, select ***Internet*** or ***OnPremise*** from the value help.
9.  For *<Authentication\>*, select one of these authentication methods for your proxy type:
    -    **Internet**:
        -   ***BasicAuthentication***

        -   ***ClientCertificateAuthentication*** 

            > ### Note:  
            > For client certificate authentication, you must upload the X.509 client certificate in P12 format on the client side, using the *Maintain Client Certificates* application. For more information, see [Maintain Client Certificates](../50-administration-and-ops/Maintain_Client_Certificates_7f6a8fb.md). Uploading the client certificate via the Destination service is not supported.

    -   **OnPremise**:
        -   ***BasicAuthentication***

        -   ***PrincipalPropagation***

            > ### Note:  
            > The use of authentication type `PrincipalPropagation` for a destination is not supported in the ADT class runner.

10. If you use basic authentication, set a user name and credentials for the destination.
11. If you are using more than one Cloud Connector for on-premise connectivity in your subaccount, you must enter the *<Location ID\>* of the target Cloud Connector. See also [Managing Subaccounts](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/f16df12fab9f4fe1b8a4122f0fd54b6e.html) \(section **Procedure**, step 4\).
12. Depending on the proxy type of your RFC destination, specify at least the following JCo properties in section *Additional Properties*.
    1.  In the *Additional Properties* panel, choose *New Property*.
    2.  Add each required property from the dropdown menu and specify its value:


        <table>
        <tr>
        <th>

        Proxy Type


        
        </th>
        <th>

        Property


        
        </th>
        <th>

        Description


        
        </th>
        </tr>
        <tr>
        <td rowspan="9">

        **OnPremise**


        
        </td>
        <td colspan="2">

        **Load Balancing Connections**


        
        </td>
        </tr>
        <tr>
        <td>

        `jco.client.r3name`


        
        </td>
        <td>

        Three-letter system ID of your backend system \(as configured in the Cloud Connector\).


        
        </td>
        </tr>
        <tr>
        <td>

        `jco.client.mshost`


        
        </td>
        <td>

        Message server host \(as configured in the Cloud Connector\).


        
        </td>
        </tr>
        <tr>
        <td>

        `jco.client.group`


        
        </td>
        <td>

        \(Optional\) The group of application servers that is used \(logon group\). If not specified, the group `PUBLIC` is used.


        
        </td>
        </tr>
        <tr>
        <td>

        `jco.client.client`


        
        </td>
        <td>

        Three-digit ABAP client number \(defines the client of your backend ABAP system\).


        
        </td>
        </tr>
        <tr>
        <td colspan="2">

        **Direct Connections** 


        
        </td>
        </tr>
        <tr>
        <td>

        `jco.client.ashost`


        
        </td>
        <td>

        Application server name of your backend system \(as configured in the Cloud Connector\).


        
        </td>
        </tr>
        <tr>
        <td>

        `jco.client.sysnr`


        
        </td>
        <td>

        Instance number of the application server \(as configured in the Cloud Connector\).


        
        </td>
        </tr>
        <tr>
        <td>

        `jco.client.client`


        
        </td>
        <td>

        Three-digit ABAP client number \(defines the client of your backend ABAP system\).


        
        </td>
        </tr>
        <tr>
        <td rowspan="4">

        **Internet**


        
        </td>
        <td>

        `jco.client.wshost`


        
        </td>
        <td>

        WebSocket RFC server host on which the target ABAP system is running. The system must be exposed to the Internet.


        
        </td>
        </tr>
        <tr>
        <td>

        `jco.client.wsport`


        
        </td>
        <td>

        WebSocket RFC server port on which the target ABAP system is listening.


        
        </td>
        </tr>
        <tr>
        <td>

        `jco.client.client`


        
        </td>
        <td>

        Three-digit ABAP client number \(defines the client of the target ABAP system\).


        
        </td>
        </tr>
        <tr>
        <td>

        `jco.client.tls_client_certificate_logon`


        
        </td>
        <td>

        Enables client certificate authentication if set to ***1***.


        
        </td>
        </tr>
        </table>
        
        For a detailed description of RFC-specific properties \(JCo properties\), see [RFC Destinations](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/238d027c154541f597201a0002713c86.html).

13. Press *Save*.



<a name="loioa69e99c457a54ff881adcff843eea950__section_hgj_1sk_4jb"/>

## Next Step \(Optional\): Call a Remote Function Module

1.  Open Eclipse, and create and execute a runnable class.
2.  Execute a remote function module. See [Enable RFC Communication in Your ABAP Code](Enable_RFC_Communication_in_Your_ABAP_Code_bbbd142.md).

    > ### Note:  
    > When using on-premise connectivity, make sure the called remote function module is exposed in Cloud Connector. See [Configure Access Control \(RFC\)](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/ca5868997e48468395cf0ca4882f5783.html).




## Related Information

[RFC Destinations](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/238d027c154541f597201a0002713c86.html)

