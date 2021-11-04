<!-- loio2133e15cbf8747dbad81dff41a14e139 -->

# SOAP Communication via Communication Arrangements

To set up SOAP communication via communication arrangement, proceed as follows:

1.  Create a Service Consumption model of the type Web service as described in [Creating Service Consumption Model](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/96132822b3554016b653d3601bb9ff1a.html).
2.  Create a corresponding outbound service of type `SOAP` and include it in a communication scenario. See [Communication Scenario](Communication_Scenario_7ea7276.md).
3.  Create a communication arrangement as described in [How to Create a Communication Arrangement](../50-administration-and-ops/How_to_Create_a_Communication_Arrangement_a0771f6.md).
4.  Call the Web service as described in the sample code below.

> ### Note:  
> The parameters `SERVICE_ID` and `COMM_SYSTEM_ID` are optional and only need to be specified if unique identification of the communication arrangement is not possible without them.

> ### Sample Code:  
> ```
> TRY.
>     DATA(soap_destination) = cl_soap_destination_provider=>create_by_comm_arrangement(
>                                comm_scenario  = '<test scenario>'
>                                service_id     = '<service id>'
>                                comm_system    = '<comm system>' ).
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
> For the approach via communication arrangement, you can't set the properties programmatically by using setter methods. See [Communication Arrangement](Communication_Arrangement_201de48.md) for more information.

**Related Information**  


[Enable SOAP Communication in Your ABAP Code](Enable_SOAP_Communication_in_Your_ABAP_Code_6ab460e.md "SOAP-based Web service outbound communication within the ABAP environment is enabled by using SOAP destination objects.")

[Overview of Communication Management](Overview_of_Communication_Management_5b8ff39.md "")

[Communication Arrangement](Communication_Arrangement_201de48.md "A communication arrangement is a runtime description of a specific communication scenario. It describes which communication partners communicate with each other in the scenario and how they communicate.")

[Developing External Service Consumption \(Outbound Communication\)](Developing_External_Service_Consumption_(Outbound_Communication)_f871712.md "Get more information about consuming external services.")

