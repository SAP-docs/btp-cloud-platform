<!-- loio1f8e2542308e4eb0b2a5bf91462fb4dc -->

# Features Related to SAP Alert Notificaton service for SAP BTP

Deploy and update the SAP Alert Notification service for SAP BTP using the multitarget application concept, or get notified by the service about multitarget application operation status.



<a name="loio1f8e2542308e4eb0b2a5bf91462fb4dc__section_afx_xl2_wkb"/>

## Deploying and Updating the service

As an alternative to the manual procedure, you can use a deployment descriptor to automate the initial deployment of SAP Alert Notification service. You can use the same procedure to update the service parameters. See the procedure described in [Updating for the Cloud Foundry Environment](https://help.sap.com/viewer/5967a369d4b74f7a9c2b91f5df8e6ab6/Cloud/en-US/8e65bf3b94d945918440b01646d8d473.html), section *Update using a Multi-Target Application deployment descriptor*.



## Using the SAP Alert Notification service for BTP for alerts during deployment and undeployment of multitarget applications



### 

You can set SAP Alert Notification service for SAP BTP to dispatch alerts to a communication channel of your choice, so that you are informed about the status of MTA deployment and undeployment operations. For example, if setup to do so, upon a successful deployment t can send you an e-mail or a Slack message. You can also get notified for problems in MTA operations, as you can also receive alerts if the deployment has encountered issues.

The integration between the services is out-of-the-box, that is, no special steps are required for its activation. If you have a service instance in the space where the MTA deployment takes place, it would automatically receive alerts from the MTA deployments in that space.

See how you can match events using about multitarget operations as described in [Multitarget Application Events](https://help.sap.com/viewer/5967a369d4b74f7a9c2b91f5df8e6ab6/Cloud/en-US/b512e2d7ae174291baded5ce5ffa601a.html).

To see additional details, see [Receive instant notifications...with the SAP Cloud Deployment service](https://blogs.sap.com/2020/02/24/receive-instant-notifications-for-your-sap-cloud-platform-cloud-foundry-deployments-and-dynamically-change-your-alerting-policy-with-mta-deployment-service/).

