<!-- loio711286a6629c4f209ff42e5e1383ab88 -->

# Create a Communication Arrangement for the Communication Scenario bound to an Event Consumption Model



## Context

To be able to receive events from the *SAP Event Mesh* service instance, you must configure the inbound communication from the *SAP Event Mesh* to the consuming `Event Consumption Model`.

For general information about how to create communication arrangements, see [How to Create a Communication Arrangement](how-to-create-a-communication-arrangement-a0771f6.md).



## Procedure

1.  Open the *Communication Arrangements* app and click on *New*.

2.  Select the communication scenario that was created for the respective `Event Consumption Model`..

    You can recognize the scenario by its `Inbound Service`. An `Inbound Service` is created for each `Event Consumption Model` and later on assigned to the respective communication scenario.

3.  Choose an Arrangement Name and click on *Create*.

4.  Create a communication system as described in .

    1.  On the*General* tab under *Technical Data*, pull the switch for `Event Mesh` to *ON*.

        Note that communication arrangements created for an `Event Consumption Model` only support inbound communication. That's why the *Inbound Only* flag is activated when switching *Event Mesh* on.

    2.  Select the *Event Channel* In the *Event Mesh* section, that you've configured as described in [Communication Management](communication-management-56cf82e.md).

        The *Event Channel* name you see in the value help is the name that was assigned in the property *Channel Name* of the respective SAP\_COM\_0092 communication arrangement.

    3.  Add a new user in the *Users for Inbound Communication* tab as described in [How to Create Communication Users](how-to-create-communication-users-0377ade.md).

        This inbound user is used later for the event processing. This user has authorizations maintained in the `Authorization Default Values` as described in [Adjusting the Generated Artifacts](https://help.sap.com/docs/SAP_S4HANA_CLOUD/25cf71e63940453397a32dc2b7676947/090230c1c26346518c5b82687ab2cd6f.html).


    In general, you can assign multiple `Event Consumption Models` via the corresponding communication scenarios to the same `SAP_COM_0092` communication arrangement.




<a name="loio711286a6629c4f209ff42e5e1383ab88__result_knv_5mz_xtb"/>

## Results

You've created an inbound communication arrangement for your `Event Consumption Model`.

