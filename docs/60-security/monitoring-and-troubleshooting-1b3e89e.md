<!-- loio1b3e89e915b349c1aa3896ac8c6becd6 -->

# Monitoring and Troubleshooting

This section provides information on troubleshooting-related activities for the SAP Authorization and Trust Management service in the Cloud Foundry environment.



> ### Tip:  
> We also recommend that you regularly check the SAP Notes and Knowledge Base for component `BC-CP-CF-SEC-IAM` in the [SAP Support Portal](https://support.sap.com/home.html). These contain information about program corrections and provide additional information.
> 
> To help you troubleshoot your issue, we also recommend increasing the log verbosity of your application and application router. We provide a [script](https://github.com/SAP/cloud-security-xsuaa-integration/tree/master/troubleshooting/logcollector) to help you. If for some reason you can't use this script, increase the log verbosity manually, see related link.

Our troubleshooting information can be found in our Guided Answers [Troubleshooting for the SAP Authorization and Trust Management service in the Cloud Foundry environment](https://ga.support.sap.com/dtp/viewer/index.html#/tree/2212/actions/28290). Guided Answers are a specialized format to guide you step by step through troubleshooting topics. Check the individual troubleshooting topics for your error message. If you can't find your problem, create an incident in the component `BC-CP-CF-SEC-IAM`. For more information, see the related link.

-   [The Security Tab Is Missing in the Subaccount](https://ga.support.sap.com/dtp/viewer/index.html#/tree/2212/actions/28290:34793)

-   [Access Is Denied or Forbidden](https://ga.support.sap.com/dtp/viewer/index.html#/tree/2212/actions/28290:28291)

-   [Identity Provider Could Not Process Authentication Request](https://ga.support.sap.com/dtp/viewer/index.html#/tree/2212/actions/28290:28292)

-   [Logon Screen Shows "SAP HANA XS Advanced"](https://ga.support.sap.com/dtp/viewer/index.html#/tree/2212/actions/28290:28293)

-   [Requested Route Does Not Exist](https://ga.support.sap.com/dtp/viewer/index.html#/tree/2212/actions/28290:34795)

-   [Subdomain Does Not Map to a Valid Identity Zone](https://ga.support.sap.com/dtp/viewer/index.html#/tree/2212/actions/28290:34797)

-   [No Client with Requested ID](https://ga.support.sap.com/dtp/viewer/index.html#/tree/2212/actions/28290:34801)

-   [Login Issues](https://ga.support.sap.com/dtp/viewer/index.html#/tree/2212/actions/28290:35340)

-   [Cannot Add Role Templates to Predefined Role Collections](https://ga.support.sap.com/dtp/viewer/index.html#/tree/2212/actions/28290:35574)

-   [502 Error: Call to /oauth/token Was Not Successful](https://ga.support.sap.com/dtp/viewer/index.html#/tree/2212/actions/28290:40211)

-   [Unexpected AuthnResponse : Existing authentication - <User\>](https://ga.support.sap.com/dtp/viewer/index.html#/tree/2212/actions/28290:48205)

-   [AuthnRequest expired - ID: <RequestId\> Destination: <IdPDestination\>](https://ga.support.sap.com/dtp/viewer/index.html#/tree/2212/actions/28290:48362)

-   [InResponseToField of Response doesn‘t correspond to the sent message](https://ga.support.sap.com/dtp/viewer/index.html#/tree/2212/actions/28290:48369)

-   [Response issue time is either too old or with date in the future. Sync IdP to match skew <skew\>](https://ga.support.sap.com/dtp/viewer/index.html#/tree/2212/actions/28290:48396)

-   [Trust establishment issues](https://ga.support.sap.com/dtp/viewer/index.html#/tree/2212/actions/28290:52538)

-   [Token retrieval fails with status code 401](https://ga.support.sap.com/dtp/viewer/index.html#/tree/2212/actions/28290:52819)

-   [Cockpit displays HTTP status 500 error on logon with custom IdP user](https://ga.support.sap.com/dtp/viewer/index.html#/tree/2212/actions/28290:53448)

-   [IAS application reference isn't created in your IAS tenant](https://ga.support.sap.com/dtp/viewer/index.html#/tree/2212/actions/28290:53486)

-   [User base doesn't appear in existing Neo subaccounts](https://ga.support.sap.com/dtp/viewer/index.html#/tree/2212/actions/28290:53495)

-   [User from corporate IdP can't log on to Neo subaccount](https://ga.support.sap.com/dtp/viewer/index.html#/tree/2212/actions/28290:53598)


**Related Information**  


[Getting Support](../70-getting-support/getting-support-5dd7398.md "Use SAP Community, get guided answers, or explore SAP Support Portal.")

[Enable and Provide Application Logs](enable-and-provide-application-logs-f22d510.md "If there are authentication problems in your application, enable logging for the container security library in question, reproduce the problem, and attach the application logs. To obtain more details, set the environment variables for the application.")

[Auditing and Logging Information for SAP Authorization and Trust Management Service](auditing-and-logging-information-for-sap-authorization-and-trust-management-service-d8f4b7c.md "Here you can find a list of the security events that are logged by SAP Authorization and Trust Management service (XSUAA). These events are provided in addition to the events of the Cloud Foundry User Account and Authentication service (UAA).")

[Authorization and Access Control Cookbook](https://cap.cloud.sap/docs/guides/authorization)

