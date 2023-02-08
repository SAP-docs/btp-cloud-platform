<!-- loio980bd73175d44007b65e67b07eccb730 -->

# Creating Communication Arrangements



## Prerequisites

-   The Event Mesh kernel service is provided in the SAP Business Technology Platform.

-   The destination URL of the Event Mesh kernel service instance is available. The destination URL is given in the corresponding service key of the SAP Event Mesh service instance.

-   The key user must have the business role `SAP_BR_ADMINISTRATOR` \(Administrator\) that contains the business catalog `SAP_CORE_BC_COM` \(Communication Management\).




## Context



## Procedure

1.  Log on to the SAP Fiori launchpad in the SAP S/4HANA Cloud system.

2.  Create a communication arrangement
3.  In the *Communication Management* app, select the *Communication Arrangements* artifact.

4.  Choose *New*.

5.  Enter or select the *Scenario* `SAP_COM_0892` \(communication scenario ID\) for *SAP Event Mesh 2.0 Integration*.

6.  Adapt the *Arrangement Name*.

7.  Choose *Create*.

8.  Create a communication system
9.  In the *Common Data* section, press *New* to create a *Communication System*.

10. In the *New Communication System* dialog box, proceed as follows:

    1.  Enter the *System ID*.

    2.  Enter the *System Name*.

    3.  Choose *Create*.


11. In the *General* tab, enter the destination URL of the Event Mesh kernel service instance in the *Host Name* field.

12. In the *Users for Inbound Communication* tab, press *\+*.

13. In the *New Inbound Communication User* dialog box, proceed as follows:

    1.  Choose the *Authentication Method* *User Name and Password*.

    2.  Enter a *User Name / Client ID*. Proceed as follows:

        -   Choose a *User Name / Client ID* from the value help.
        -   Create a *New User* by choosing *New User*.
            -   Enter the *User Name*.
            -   Enter a *Description*.
            -   Press the *Propose Password* button.
            -   Choose *Create*.


        > ### Note:  
        > This user is used to run the background process that keeps the connection up and running.

    3.  Choose *OK*.


14. In the *Users for Outbound Communication* tab, press *\+*.

15. In the *New Outbound User* dialog box, proceed as follows:

    1.  Choose the *Authentication Method* *SSL Client Certificate*.

    2.  Choose the *Client Default* for the *Client Certificate* from the value help.

    3.  Choose *Create*.


16. Choose *Save* to save the communication system.

17. Finalize the communication arrangement
18. In the *Additional Properties* section, enter the *Channel* name.

    If the *Channel* name is not specified, the *Channel* name equals the *Arrangement Name*. The channel name is used as key in all enterprise event enablement SAP Fiori applications.

19. In the *Outbound Services* section, enter `/protocols/amqp10ws` as *Path*.

20. Choose *Save*.




## Results

You have created a communication arrangement.

