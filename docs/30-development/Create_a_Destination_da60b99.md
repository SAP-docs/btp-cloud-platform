<!-- loioda60b993f6e145d78c82cd00f755c114 -->

# Create a Destination

In the SAP BTP cockpit, you need to create a destination to enable the communication to the ABAP environment.



## Procedure

1.  In the SAP BTP cockpit, navigate to your subaccount. See [Navigate to Orgs and Spaces](https://help.sap.com/viewer/e275296cbb1e4d5886fa38a2a2c78c06/Cloud/en-US/5bf87353bf994819b8803e5910d8450f.html).

2.  Choose *Connectivity* \> *Destinations.*.

3.  Choose *New Destination*, and enter the following data:


    <table>
    <tr>
    <th>

    Field


    
    </th>
    <th>

    Value


    
    </th>
    </tr>
    <tr>
    <td>

    Name


    
    </td>
    <td>

    Enter the destination name. This name is also used in the SAP Web IDE as the destination name in the service task properties.


    
    </td>
    </tr>
    <tr>
    <td>

    Type


    
    </td>
    <td>

    Select *HTTP*.


    
    </td>
    </tr>
    <tr>
    <td>

    Description


    
    </td>
    <td>

    Enter a description.


    
    </td>
    </tr>
    <tr>
    <td>

    URL


    
    </td>
    <td>

    URL for the ABAP environment. The format is: `https://*****.ondemand.com/`.

    Set the destination URL to the authorization endpoint URL found in the service key that was created for the workflow capability when creating the communication arrangement. Access the communication arrangement and copy the root URL under *Inbound Services* \> *Service URL/Service Interface*.


    
    </td>
    </tr>
    <tr>
    <td>

    Proxy Type


    
    </td>
    <td>

     *Internet* 


    
    </td>
    </tr>
    <tr>
    <td>

    Authentication


    
    </td>
    <td>

    Select *BasicAuthentication*.


    
    </td>
    </tr>
    <tr>
    <td>

    User


    
    </td>
    <td>

    Set the user to the client ID as specified for the inbound communication.


    
    </td>
    </tr>
    <tr>
    <td>

    Password


    
    </td>
    <td>

    Set the password to the secret.


    
    </td>
    </tr>
    </table>
    
4.  Save your entries.


