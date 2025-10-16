<!-- loio3530af7ff2b449fbbc591dd3e2c0d151 -->

# Troubleshooting

This topic contains information that is essential for troubleshooting issues when deploying multitarget applications in the Cloud Foundry environment.



Before you start investigating the problem, download the logs for the current deployment. The logs contain the following structure of files:

-   `OPERATION.LOG` - contains the whole deployment log

-   `<application-name>.log` – there is a separate file for each application. It holds the logs related to the application during staging and starting


> ### Note:  
> Note that the operation logs are kept for 3 days. Make sure that you download them before the retention period expires

To download the logs, execute the following command:

`cf dmol -i <process-id>`

> ### Example:  
> `cf dmol -i cbe58aeb-0c40-4a3e-972d-82a499815745`



### Troubleshooting an MTA Operation Failure

To troubleshoot issues, see the list of problems that may occur during the Multitarget Application deployment that is available in [MTA Operation Failure](mta-operation-failure-f3e97ff.md).



### Creating an Incident

If the list does not contain a solution for your issue, you can contact the service support team by reporting an incident through the [SAP Support Portal](https://support.sap.com/en/index.html). Here is a list of what to provide in an incident:

1.  Select the component *BC-CP-CF-DS* from the *Component* dropdown list.
2.  In the description field, provide as much information as possible about the Cloud Foundry region, Cloud Foundry organization and space names and/or Global Unique Identifiers.
3.  Provide information about scenario with the exact steps to be reproduced, expected result, actual result or the error that appears, relevant logs and screenshots. In all cases, the starting point for the investigation are the Multitarget Application operation logs.

