<!-- loiof51ced4de19d41fe91f6d07c1d2a1db1 -->

# Cloud Foundry Audit Events for Service Instances

The following steps can help you get information about who started a service instance. These steps are valid only for Cloud Foundry subaccounts.

To get the instance information, you can use the [Cloud Foundry API](https://v3-apidocs.cloudfoundry.org/version/3.134.0/), which is available for all CF subaccounts. The following steps describe a path of API calls. Combining all information from the three steps, you can have a list of all services created by a specific user at a specific time.

1.  Get list of all audit events from type “audit.service\_instance.create”.

    ![](images/Get_list_of_all_audit_events_from_type_audit_service_instance_create_5f9752b.png)

2.  Follow service plan navigation.

    ![](images/Service_Plan_Navigation_2c6b269.png)

3.  Follow service offering to get the name, documentation URL and other parameters of the service.

    ![](images/Service_Offering_d8ae322.png)


