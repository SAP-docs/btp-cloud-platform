<!-- loio1f8e2542308e4eb0b2a5bf91462fb4dc -->

# Features Related to SAP Alert Notificaton service for SAP BTP

Deploy and update SAP Alert Notification service for SAP BTP using the multitarget application concept, or get notified by the service about the status of multitarget application operations.



<a name="loio1f8e2542308e4eb0b2a5bf91462fb4dc__section_afx_xl2_wkb"/>

## Deploying and Updating the Service

As an alternative to the manual procedure, you can use a deployment descriptor to automate the initial deployment of SAP Alert Notification service. You can use the same procedure to update the service parameters. See the procedure described in [Configuration Management Using Multitarget Application Descriptors](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/configuration-management-using-multitarget-application-descriptors?version=Cloud).



## Receive Alerts During Deployment and Undeployment of MTAs



### 

You can set SAP Alert Notification service for SAP BTP to dispatch alerts to a communication channel of your choice, so that you are informed about the status of MTA deployment and undeployment operations. For example, if setup to do so, upon a successful deployment it can send you an e-mail or a Slack message. You can also get notified for problems in MTA operations, as you can also receive alerts if the deployment has encountered issues.

The integration between the services is out-of-the-box, that is, no special steps are required for its activation. If you have a service instance in the space where the MTA deployment takes place, it would automatically receive alerts from the MTA deployments in that space.

See how you can match events using multitarget operations as described in [Multitarget Application Events](https://help.sap.com/viewer/5967a369d4b74f7a9c2b91f5df8e6ab6/Cloud/en-US/b512e2d7ae174291baded5ce5ffa601a.html).

To see additional details, see [Receive instant notifications...with the SAP Cloud Deployment service](https://blogs.sap.com/2020/02/24/receive-instant-notifications-for-your-sap-cloud-platform-cloud-foundry-deployments-and-dynamically-change-your-alerting-policy-with-mta-deployment-service/).

