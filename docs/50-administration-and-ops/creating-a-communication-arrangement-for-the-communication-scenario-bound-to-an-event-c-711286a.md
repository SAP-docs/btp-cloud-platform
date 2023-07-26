<!-- loio711286a6629c4f209ff42e5e1383ab88 -->

# Creating a Communication Arrangement for the Communication Scenario bound to an Event Consumption Model

To be able to receive events from the SAP Event Mesh service instance, you must configure the inbound communication from the SAP Event Mesh to the consuming event consumption model.



## Prerequisites

-   You've set up a communication arrangement for `SAP_COM_0092` as described in [Communication Management](communication-management-56cf82e.md).

-   You've created an event consumption model and a *Communication Scenario* as described in [Event Consumption](event-consumption-a2c4285.md).




## Context

Following the procedure, you create an inbound communication arrangement.



## Procedure

1.  Log on to the SAP Fiori launchpad in the SAP S/4HANA Cloud system.

2.  In the *Communication Management* app, select the *Communication Arrangements* artifact.

3.  Choose *New*.

4.  Select the *Communication Scenario* that was created for the respective event consumption model.

    You can recognize the scenario by its `Inbound Service`. An `Inbound Service` is created for each event consumption model and later on assigned to the respective communication scenario.

5.  Choose an *Arrangement Name* and click on *Create*.

6.  To assign a communication system, proceed as follows:

    -   Assign an existing communication system by selecting a *Communication System*. You can ignore the substeps.
    -   Create a communication system as described in [How to Create Communication Systems](https://help.sap.com/docs/SAP_S4HANA_CLOUD/0f69f8fb28ac4bf48d2b57b9637e81fa/1bfe32ae08074b7186e375ab425fb114.html).

    1.  In the *General* tab under *Technical Data*, pull the switch for *Event Mesh* to *ON*.

        Note that communication arrangements created for an event consumption model only support inbound communication. That's why the *Inbound Only* flag is activated when switching *Event Mesh* on.

    2.  In the *General* tab under *Technical Data*, select the *Event Channel* that you've configured as described in [Communication Management](communication-management-56cf82e.md).

        The *Event Channel* name you see in the value help is the name that was assigned in the property *Channel* of the respective `SAP_COM_0092` communication arrangement.

    3.  In the *Users for Inbound Communication* tab, add an inbound user.

        > ### Note:  
        > The *User for Inbound Communication* \(inbound user\) and the *Communication User* must be maintained as two different users. Make sure to create a dedicated inbound user, apart from your communication user. To create a new inbound user, follow the steps described in [How to Create Communication Users](how-to-create-communication-users-0377ade.md)
        > 
        > The inbound user is used later for event processing. This user has authorizations maintained in the `Authorization Default Values` as described in [Adjusting the Generated Artifacts](https://help.sap.com/docs/SAP_S4HANA_CLOUD/25cf71e63940453397a32dc2b7676947/090230c1c26346518c5b82687ab2cd6f.html).

    4.  Choose *Save*.


    In general, you can assign multiple event consumption models via the corresponding communication scenarios to the same `SAP_COM_0092` communication arrangement.




<a name="loio711286a6629c4f209ff42e5e1383ab88__result_knv_5mz_xtb"/>

## Results

You've created an inbound communication arrangement for your event consumption model.

**Related Information**  


[How to Create a Communication Arrangement](how-to-create-a-communication-arrangement-a0771f6.md "General information about creating communication arrangements")

