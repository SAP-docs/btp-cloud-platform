<!-- loio4005b2f880604f43a88ca796b04620a7 -->

# Destroying Business Event Logging Objects Using BEL\_TIMESTAMP\_DESTRUCTION

You can use the `BEL_TIMESTAMP_DESTRUCTION` object to destroy Business Event Logging objects. This data destruction object is related to the `BEL_TIMESTAMP_DESTRUCTION` ILM object.



<a name="loio4005b2f880604f43a88ca796b04620a7__section_ftx_z52_yqb"/>

## Prerequisites

You need to fulfill these prerequisites if you want to destroy a Business Event Logging object:

-   You've authorization for the **Data Privacy Specialist** role. For instructions about creating a business role, refer to [How to Create a Business Role from a Template](how-to-create-a-business-role-from-a-template-ec310a8.md)
-   You've assigned the ILM object \(`BEL_TIMESTAMP_DESTRUCTION`\) assigned to a new or existing ILM audit area.
-   You've defined an ILM policy and the required retention rules for the ILM object.
-   You've made one or more policies with the policy status **Live** available for the ILM object.



<a name="loio4005b2f880604f43a88ca796b04620a7__section_qhb_hv2_yqb"/>

## ILM-Based Information for the Data Destruction Object

You create policies and rules for the `BEL_TIMESTAMP_DESTRUCTION` ILM object related to this data destruction object.

The following *Condition Fields* for the ILM object are defined in the ILM policy and are visible when creating or processing *ILM Policies*:

-   BO\_TYPE: Objects. For example, **ProductionOrder**.

Use **last event timestamp** as the **Time Ref** to determine the retention period. The timestamp of the last event in a business event sequence in the context of the object node is used to determine the retention period according to the ILM policies. If the last event is older than the date defined in the **last time-stamp**, then the sequence is destroyed. For example, you can set the value between 6 and 12 months.

We recommend that you create at least one rule that defines a retention period for all objects. This limits database consumption. To set the rule for all objects, leave the objects condition field empty.

For more information, see [Information Lifecylce Management](https://help.sap.com/docs/SAP_S4HANA_CLOUD/a630d57fc5004c6383e7a81efee7a8bb/3c9d33dde6154f71863f994262a584fd.html).

