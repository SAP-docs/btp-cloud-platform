<!-- loiob7931f7b42d5433987b9d3f30e2445fd -->

# Workflow Integration

You can enable the communication between the ABAP environment and the workflow capability within the SAP Workflow Management service.

This scenario enables the ABAP environment applications to extend their business processes by using the workflow capability in the Cloud Foundry environment. It allows the provisioning of an API in the ABAP environment to start and control workflow instances running on workflow capability.

You set up the scenario using the following tasks:

1.  [Create a Communication Arrangement Using a Service Key](Create_a_Communication_Arrangement_Using_a_Service_Key_e66e844.md) \(recommended\)

2.  [Create a Destination](Create_a_Destination_da60b99.md)

3.  

4.  [Maintain Business Roles and Business Users](Maintain_Business_Roles_and_Business_Users_cb058dc.md)


-   **[Create a Communication Arrangement Using a Service Key](Create_a_Communication_Arrangement_Using_a_Service_Key_e66e844.md "To connect the ABAP environment and the SAP BTP cockpit, you need a communication arrangement.")**  
To connect the ABAP environment and the SAP BTP cockpit, you need a communication arrangement.
-   **[Create a Destination](Create_a_Destination_da60b99.md "In the  SAP BTP cockpit, you need to create a destination to enable the communication to the ABAP environment.")**  
In the SAP BTP cockpit, you need to create a destination to enable the communication to the ABAP environment.
-   **[Model Service Task to Complete the Workflow in the ABAP Environment](Model_Service_Task_to_Complete_the_Workflow_in_the_ABAP_Environment_35f7822.md "As the workflow capability doesn’t support the enterprise messaging service, you must model an additional service task right before each
		end event for each workflow definition, that was started from the ABAP environment.")**  
As the workflow capability doesn’t support the enterprise messaging service, you must model an additional service task right before each end event for each workflow definition, that was started from the ABAP environment.
-   **[AIF Monitoring](AIF_Monitoring_95b6a4f.md "AIF (Application Interface Framework) enables you to monitor inbound and outbound messages in the ABAP environment.")**  
AIF \(Application Interface Framework\) enables you to monitor inbound and outbound messages in the ABAP environment.

