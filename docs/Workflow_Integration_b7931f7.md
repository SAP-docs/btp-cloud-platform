<!-- loiob7931f7b42d5433987b9d3f30e2445fd -->

# Workflow Integration

You can enable the communication between the ABAP environment and the workflow capability within the SAP Workflow Management service.

This scenario enables the ABAP environment applications to extend their business processes by using the workflow capability in the Cloud Foundry environment. It allows the provisioning of an API in the ABAP environment to start and control workflow instances running on workflow capability.

You set up the scenario using the following tasks:

1.  [Create a Communication Arrangement Using a Service Key](Create_a_Communication_Arrangement_Using_a_Service_Key_e66e844.md) \(recommended\)

2.  [Create a Destination](Create_a_Destination_da60b99.md)

3.  [Set Scopes for the Service Instance Using the Command Line Interface](Set_Scopes_for_the_Service_Instance_Using_the_Command_Line_Interface_2c19449.md)

4.  [Maintain Business Roles and Business Users](Maintain_Business_Roles_and_Business_Users_cb058dc.md)


-   **[Create a Communication Arrangement Using a Service Key](Create_a_Communication_Arrangement_Using_a_Service_Key_e66e844.md "To connect the ABAP environment and the SAP BTP cockpit, you need a communication arrangement.")**  
To connect the ABAP environment and the SAP BTP cockpit, you need a communication arrangement.
-   **[Create a Destination](Create_a_Destination_da60b99.md "In the  SAP BTP cockpit, you need to create a destination to enable the communication to the ABAP environment.")**  
In the SAP BTP cockpit, you need to create a destination to enable the communication to the ABAP environment.
-   **[Set Scopes for the Service Instance Using the Command Line Interface](Set_Scopes_for_the_Service_Instance_Using_the_Command_Line_Interface_2c19449.md "To set the necessary scopes of a service instance, you need to install a new service
		interface with all scopes needed or you update an already existing service
		interface.")**  
To set the necessary scopes of a service instance, you need to install a new service interface with all scopes needed or you update an already existing service interface.
-   **[Model Service Task to Complete the Workflow in the ABAP Environment](Model_Service_Task_to_Complete_the_Workflow_in_the_ABAP_Environment_35f7822.md "As the workflow capability doesn’t support the enterprise messaging service, you must model an additional service task right before each
		end event for each workflow definition, that was started from the ABAP environment.")**  
As the workflow capability doesn’t support the enterprise messaging service, you must model an additional service task right before each end event for each workflow definition, that was started from the ABAP environment.

