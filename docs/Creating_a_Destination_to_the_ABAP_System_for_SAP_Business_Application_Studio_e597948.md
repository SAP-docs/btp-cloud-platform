<!-- loioe597948462fe45c98c10269bbe3603d6 -->

# Creating a Destination to the ABAP System for SAP Business Application Studio



<a name="loioe597948462fe45c98c10269bbe3603d6__steps_fn5_mv2_mmb"/>

## Procedure

1.  Log on to the SAP BTP cockpit as administrator.

2.  From your global account, navigate to your Cloud Foundry subaccount.

3.  In the navigation area, choose *Destinations*.

4.  Choose *New Destination*.

5.  Enter the following data:


    <table>
    <tr>
    <th>

    Field


    
    </th>
    <th>

    User Input


    
    </th>
    </tr>
    <tr>
    <td>

    ***Name***


    
    </td>
    <td>

    Enter a name for the destination, for example, ***SAP\_Business\_Application\_Studio***.


    
    </td>
    </tr>
    <tr>
    <td>

    ** *Type* **


    
    </td>
    <td>

     *HTTP* 


    
    </td>
    </tr>
    <tr>
    <td>

    ***Description***


    
    </td>
    <td>

     


    
    </td>
    </tr>
    <tr>
    <td>

    ***URL***


    
    </td>
    <td>

    Enter the URL of the ABAP system that you copied from the `<url>` element in the service key \(see [Creating a Service Key for the ABAP System](Creating_a_Service_Key_for_the_ABAP_System_7af8259.md)\).


    
    </td>
    </tr>
    <tr>
    <td>

    ***Proxy Type***


    
    </td>
    <td>

    *Internet*


    
    </td>
    </tr>
    <tr>
    <td>

    ***Authentication***


    
    </td>
    <td>

    *OAuth2UserTokenExchange​*


    
    </td>
    </tr>
    <tr>
    <td>

    ***Client ID***


    
    </td>
    <td>

    Enter the content of the `<clientID>` element that you copied from the `uaa` section of the service key \(see [Creating a Service Key for the ABAP System](Creating_a_Service_Key_for_the_ABAP_System_7af8259.md)\).


    
    </td>
    </tr>
    <tr>
    <td>

    ***Client Secret***


    
    </td>
    <td>

    Enter the content of the `<clientsecret>` element that you copied from the `uaa` section of the service key \(see [Creating a Service Key for the ABAP System](Creating_a_Service_Key_for_the_ABAP_System_7af8259.md)\).


    
    </td>
    </tr>
    <tr>
    <td>

    ***Token Service URL Type***


    
    </td>
    <td>

    Choose *Dedicated*.


    
    </td>
    </tr>
    <tr>
    <td>

    ***Token Service URL***


    
    </td>
    <td>

    Enter `<uaa-url>/oauth/token`, where `<uaa-url>` is the content of the `<url>` element that you copied from the `uaa` section of the service key \(see [Creating a Service Key for the ABAP System](Creating_a_Service_Key_for_the_ABAP_System_7af8259.md)\).


    
    </td>
    </tr>
    </table>
    
6.  Choose *New Property* and add the following properties:


    <table>
    <tr>
    <th>

    Property


    
    </th>
    <th>

    Value


    
    </th>
    </tr>
    <tr>
    <td>

    ***HTML5.DynamicDestination***


    
    </td>
    <td>

    ***true***


    
    </td>
    </tr>
    <tr>
    <td>

    ***HTML5.Timeout*​**


    
    </td>
    <td>

    ***60000***


    
    </td>
    </tr>
    <tr>
    <td>

    ***WebIDEEnabled***


    
    </td>
    <td>

    ***true***


    
    </td>
    </tr>
    <tr>
    <td>

    ***WebIDEUsage***


    
    </td>
    <td>

    ***odata\_abap,dev\_abap,abap\_cloud***


    
    </td>
    </tr>
    </table>
    
7.  Make sure that the *Use default JDK truststore* checkbox is checked.

8.  Choose *Save*.


