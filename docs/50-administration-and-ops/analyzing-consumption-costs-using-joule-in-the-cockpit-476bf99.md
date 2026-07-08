<!-- loio476bf99eb3514ea78548781f0201a47a -->

# Analyzing Consumption Costs Using Joule in the Cockpit

Joule, SAP's generative AI copilot in SAP BTP cockpit, provides detailed information about the consumption costs in your global account. Use this information to compare periods, identify cost drivers, or find optimization opportunities.



## Important Information

> ### Note:  
> The cost data that Joule provides is for information purposes only. Your monthly balance statement contains legally binding information regarding your monthly costs.

> ### Note:  
> This feature is available only for global accounts that use consumption-based commercial models.
> 
> If your account uses both consumption-based and subscription-based commercial models, you see cost information only for usage data charged under the consumption-based model.
> 
> Joule doesn't provide cost details for usage covered by a subscription-based model.



## Available Cost Analysis Scenarios

You can ask Joule in the SAP BTP cockpit for information about costs in your global account. Joule provides a comprehensive overview of cost data at the global account level, including breakdowns by subaccounts and services. Joule does not support queries for cost data of individual subaccounts or services. You can ask Joule for the following information:

-   **Quarterly Cost Summaries**

    Joule provides the total costs for the requested quarter, the costs for the preceding quarter, and the costs for the same quarter in the previous year. It also lists the highest-cost service plans and subaccounts for the quarter you requested.

-   **Highest-Cost Subaccounts**

    Joule provides a graphic of the highest-cost subaccounts of the requested period. It also gives a ranked list of the highest-cost subaccounts for the period, with the costs per subaccount.

-   **Highest-Cost Service Plans**

    Joule provides similar information for services, including a graphic of the most expensive service plans and a list with details of the most expensive service plans.

-   **Service Plan Cost Spikes**

    Joule displays a graphic of the highest cost spikes for services in the requested period, along with the spike amounts. It also provides a ranked list of the top cost spikes for service plans.

-   **Subaccount Cost Spikes**

    Joule provides similar information for subaccounts, including a graphic of the highest-cost spikes and a ranked list of the top cost spikes for subaccounts.

-   **Prepaid Quota Consumption**

    Joule compares the actual usage of your services with their prepaid quota and helps to identify underutilized services.

    Use this scenario only if your global account uses consumption-based commercial models and subscription-based commercial models.




## Using Joule to Analyze Costs

Type your question in the Joule chat and include details such as the period you want to review. You can define any period for the cost data you need.

For quarterly cost summaries, provide the quarter and year. For all other scenarios, provide the start month and year for the period you want to review. You can also provide the month and year for the end of the period. If you don't provide an end month and year, Joule calculates costs up to the current month.

**Related Information**  


[Account Administration Using Joule in the Cockpit](account-administration-using-joule-in-the-cockpit-3d7626b.md "Learn about the administrative tasks that SAP's generative AI copilot, Joule, can assist you with SAP BTP cockpit.")

