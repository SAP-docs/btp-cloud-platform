<!-- loio40ecb5c8bd054808805863e4814d6b6d -->

# Usage of the Destination Service

You can use the destination service to establish a connection for outbound communication.



 **Developer tasks**

1.  Providing information in the code
    1.  If the credentials are maintained via a destination in the subaccount, enter the following:

        > ### Sample Code:  
        > **Destination via subaccount**
        > 
        > ```
        > DATA(lo_destination) = cl_http_destination_provider=>create_by_cloud_destination(
        > i_name               = 'Destination Name' ).
        > 
        > ```

    2.  If the credentials are maintained via a destination service instance, enter the following:

        > ### Sample Code:  
        > **Destination via destination service instance**
        > 
        > ```
        > DATA(lo_destination) = cl_http_destination_provider=>create_by_cloud_destination(
        > i_name                       = 'Destination Name',
        > i_service_instance_name      = 'Service Instance Name' ).
        > ```

2.  Developing a configuration app to maintain the destination name or service instance name depending on the configuration of the administrator \(credentials via destination in the subaccount or credentials via a destination service instance\)

> ### Tip:  
> Instead of coding against destination names, add an additional configuration business object to define the destination name that shall be used. That way, the destination name can be different in the development, test, and production subaccount. For example:
> 
> > ### Sample Code:  
> > ```
> > SELECT SINGLE destination_name FROM destination_config INTO DATA @(lv_destination_name)
> > 
> >  DATA(lo_destination) = cl_http_destination_provider=>create_by_cloud_destination(
> >     i_name            = lv_destination_name ).
> > 
> > ```

**Administrator tasks**

-   Option 1: Maintaining the credentials via a destination in the subaccount
-   Option 2: Maintaining the credentials via a destination service instance. For this option, a communication arrangement for scenario `SAP_COM_0276` needs to be maintained to enable communication with the destination service instance. See [Create a Destination](Create_a_Destination_3fa7934.md).

> ### Recommendation:  
> We recommend using the `create_by_comm_arrangement` method for outbound communication.

