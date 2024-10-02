<!-- loio2133e15cbf8747dbad81dff41a14e139 -->

# SOAP Communication via Communication Arrangements



<a name="loio2133e15cbf8747dbad81dff41a14e139__section_sjy_xsm_mtb"/>

## Prerequisites

-   You have created a communication scenario as described in [Defining a Communication Scenario Including Authorization Values](defining-a-communication-scenario-including-authorization-values-bba0fd2.md).
-   You have a service meta data file \(WSDL file\) for the service you want to consume.
-   You have created and activated a service consumption model \(SRVC\) of type `Web Service`. See [Generating Proxies for Remote Web Service](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide/generating-proxies-for-remote-web-service?version=sap_btp) for more information.

    > ### Restriction:  
    > When calling a SOAP service via communication arrangements, only SOAP 1.1 is supported.




## Procedure

1.  Create a corresponding outbound service of type `SOAP`.
    1.  In your ABAP project, select the relevant package node in the Project Explorer.
    2.  Open the context menu and choose *File* \> *New* \> *Other ABAP Repository Object* \> *Cloud Communication Management* \> *Outbound Service* \> *Next* to launch the creation wizard.
    3.  Enter the name of the outbound service.
    4.  Select *SOAP* in the *Service Type* dropdown list.
    5.  Choose *Next* and select a transport request.
    6.  In field *Service Interface*, enter the name of the relevant consumer proxy. You can choose the consumer proxy from the list of the value help.
    7.  Save the outbound service.

2.  Add the newly created outbound service to the communication scenario. See [Service Consumption via Communication Arrangements](service-consumption-via-communication-arrangements-86aece6.md) for more information.

    > ### Note:  
    > You can't use the `create_by_comm_arrangement` method for SAP-delivered scenarios.

3.  Publish the communication scenario. The administrator can then create the required communication management objects as described in [Test Your Outbound Call](soap-communication-via-communication-arrangements-2133e15.md#loio2133e15cbf8747dbad81dff41a14e139__section_rbb_dl5_mtb).
4.  Call the SOAP service as described in the example. Copy the code snippet from the *Overview* tab in your SRVC and add the `comm_system_id` and `service_id` parameters if necessary. Note the difference between synchronous and asynchronous services. According to your developed communication scenario, add the following:


    <table>
    <tr>
    <td valign="top">
    
    `comm_scenario`
    
    </td>
    <td valign="top">
    
    mandatory
    
    </td>
    <td valign="top">
    
    ID of the developed communication scenario
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `comm_system_id`
    
    </td>
    <td valign="top">
    
    optional
    
    </td>
    <td valign="top">
    
    ID of the configured communication system
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `service_id`
    
    </td>
    <td valign="top">
    
    optional
    
    </td>
    <td valign="top">
    
    ID of the developed outbound service
    
    </td>
    </tr>
    </table>
    



<a name="loio2133e15cbf8747dbad81dff41a14e139__section_vnl_x3l_mtb"/>

## Example



### Synchronous Services

> ### Sample Code:  
> ```abap
> TRY.
>     DATA(soap_destination) = cl_soap_destination_provider=>create_by_comm_arrangement(
>                                comm_scenario  = '<demo scenario>'
>                                service_id     = '<service id>'
>                                comm_system_id    = '<comm system>' ).
>  
>     DATA(proxy) = NEW zsc_co_epm_product_soap( destination = soap_destination ).
>  
>     DATA(request) = VALUE zsc_req_msg_type( req_msg_type-product = '<product name>' ).
>     proxy->get_price(
>       EXPORTING
>         input = request
>       IMPORTING
>         output = DATA(response) ).
>  
>     "handle response
>   CATCH cx_soap_destination_error.
>     "handle error
>   CATCH cx_ai_system_fault.
>     "handle error
>   CATCH zsc_cx_fault_msg_type.
>     "handle error
>  
> ENDTRY.
> ```

> ### Note:  
> We recommend to retrieve the correct destination reference based on the communication scenario and a customer-defined property as described in [Service Consumption via Communication Arrangements](service-consumption-via-communication-arrangements-86aece6.md).



### Asynchronous Services

For asynchronous services, follow the same procedure as for synchronous services. The only differences in the code are the following:

-   The `IMPORTING` parameter is missing since the service doesn't return any value.
-   A `COMMIT WORK` triggers the SOAP call.

> ### Sample Code:  
> ```abap
>  TRY.
>         DATA(destination) = cl_soap_destination_provider=>create_by_comm_arrangement(
>                               comm_scenario  = '<demo scenario>'
> *                             service_id     = '<service id>'
> *                             comm_system_id = '<comm system>'
>                             ).
>         DATA(proxy) = NEW zco_appointment_activity_reque(
>                         destination = destination
>                       ).
>         DATA(request) = VALUE zappointment_activity_request1( ).
>         proxy->appointment_activity_request_i(
>           EXPORTING
>             input = request
>         ).
>         COMMIT WORK. "to trigger async call
>       CATCH cx_soap_destination_error.
>         "handle error
>       CATCH cx_ai_system_fault.
>         "handle error
>     ENDTRY.
> ```



<a name="loio2133e15cbf8747dbad81dff41a14e139__section_rbb_dl5_mtb"/>

## Test Your Outbound Call

To test your outbound call, you have to provide a configuration for the outbound service you want to call in your code.

Create a communication system and communication arrangement for the communication scenario in the Communication Systems and Communication Arrangements apps and maintain the required data.

To check if an asynchronous call was successfully sent to the provider system, see [SOAP Monitoring](soap-monitoring-3cd5085.md).

These tasks are performed by the administrator. For more information, see [Set Up SOAP Communication](set-up-soap-communication-8b6723b.md) and [SOAP Monitoring](soap-monitoring-3cd5085.md).

**Related Information**  


[Enable SOAP Communication in Your ABAP Code](enable-soap-communication-in-your-abap-code-6ab460e.md "")

[Communication Management](communication-management-5b8ff39.md#loio5b8ff39ddb6741a29ddfcf587939e8f4 "Learn more about the basic principles of communication management when integrating your system or solution with other systems to enable data exchange in your ABAP environment.")

[Communication Arrangement](communication-management-5b8ff39.md#loio201de48e2f57404e9222181b019eff14 "A communication arrangement is a runtime description of a specific communication scenario. It describes which communication partners communicate with each other in the scenario, and how they communicate.")

[Developing External Service Consumption \(Outbound Communication\)](developing-external-service-consumption-outbound-communication-f871712.md "Get more information about consuming external services.")

