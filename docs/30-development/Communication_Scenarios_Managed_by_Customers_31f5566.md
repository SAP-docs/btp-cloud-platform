<!-- loio31f5566141f84b388ac7004fc415784d -->

# Communication Scenarios Managed by Customers

Other than the communication scenarios managed by SAP that are ready to use, you can create your own communication scenarios.



<a name="loio31f5566141f84b388ac7004fc415784d__section_ly4_t5n_wmb"/>

## Inbound Communication

You can create and expose services for external consumption to a communication partner. To create and expose services for external consumption, a developer creates a communication scenario and assigns the required services. An administrator then creates a communication system and user for the communication partner, maintains a communication arrangement for the scenario using the created communication system, and specifies the authentication method. The communication partner can use the credentials provided by the communication system and user to consume the services of the scenario.

![](images/Inbound_Communication_Managed_by_Customers_ddbf80e.png)



<a name="loio31f5566141f84b388ac7004fc415784d__section_kgc_cvn_wmb"/>

## Outbound Communication

To set up outbound communication between two communication partners, developers and administrators have to perform different tasks. In general, they have to do the following:

-   Developers implement the call of a service
-   Administrators specify the endpoint and credentials

**Developer tasks**

-   Creating an outbound service with an ID and assigning it to a communication scenario

-   Implementing the call of the service by providing the following information in the code:

    > ### Sample Code:  
    > ```
    > DATA(lo_destination) = cl_http_destination_provider=>create_by_comm_arrangement(
    > comm_scenario        = 'COMM_SCENARIO_EXAMPLE'
    > service_id           = 'SERVICE_ID_EXAMPLE' ).
    > ```


**Administrator tasks**

-   **Step 1, option 1**: Creating a communication system that represents the communication partner. See [How To Create Communication Systems](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/c2234acd55774ebcbedb66744199273e.html).
    -   Maintaining the host name and port of the communication partner and the user credentials via a communication user. See [How to Create Communication Users](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/0377adea0401467f939827242c1f4014.html).

-   **Step 1, option 2**: Creating a communication system that represents a destination. See [Using the Destinations Editor in the Cockpit](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/565fdb3dd19d4cda80864341dc5a0451.html).
    -   **Option a**: Maintaing the credentials in a destination of your subaccount by enabling the destination service in the technical data.
    -   **Option b**: Maintaining the credentials in a destination service instance. See [Create and Bind a Destination Service Instance](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/9fdad3cad92e4b63b73d5772014b380e.html) and [Create a Destination](Create_a_Destination_3fa7934.md).

-   **Step 2**: Creating a communication arrangement by enabling the destination service. See [How To Create Communication Arrangements](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/a0771f6765f54e1c8193ad8582a32edb.html) and [Service Consumption via Communication Arrangements](Service_Consumption_via_Communication_Arrangements_86aece6.md).

> ### Recommendation:  
> We recommend creating a communication system and maintaing the host name and port of the communication partner via a communication user.

   
  
<a name="loio31f5566141f84b388ac7004fc415784d__fig_hy4_hdy_cqb"/>Preferred Configuration for Outbound Communication

 ![](images/Outbound_Communication_ABAP_Environment_0483811.png "Preferred Configuration for Outbound Communication") 



Instead of using a communication arrangement for outbound communication, you can use the destination service to establish a connection. See [Usage of the Destination Service](Usage_of_the_Destination_Service_40ecb5c.md).

Alternatively, if you only want to call a remote web service, use the following method

```
DATA(lv_dest) = cl_http_destination_provider=>create_by_url( i_url = 'https://www.example.com' ).
```

> ### Recommendation:  
> We recommend using the `create_by_comm_arrangement` method for outbound communication.

**Related Information**  


[Developing External Service Consumption \(Outbound Communication\)](Developing_External_Service_Consumption_(Outbound_Communication)_f871712.md "Get more information about consuming external services.")

[Service Consumption Model](Service_Consumption_Model_beda304.md "")

