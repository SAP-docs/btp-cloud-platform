<!-- loio4a9c5011922847ac91db165c78656149 -->

# Initial User Onboarding

In order to be able to start using the solution, your customer needs to receive an initial administrator user in their consumer tenant. This is done automatically via the initial tenant onboarding of your solution.

To trigger this onboarding process, you as the provider need to be assigned to the SolutionAdmin role collection in the consumer subaccount:

1.  Log on to the consumer subaccount and navigate to Security Role Collections.

2.  Select the role collection SolutionAdmin, choose Edit, scroll down to Users, and select +. Enter the email address of your user, select SAP ID Service as your identity provider or use your preferred custom identity provider, and save your changes.


Now you are ready to access the solution’s new tenant, where you will see the initial onboarding screen. In the confirmation dialog, you must confirm details such as email, subdomain, and subaccount ID to onboard an initial user for the customer:

1.  Open the URL your provider has sent you to get access to their SaaS application.

2.  On the initial administrator onboarding screen, your email address, subdomain, and subaccount ID are displayed. Select Onboard User to start the onboarding process. This might take a few minutes. Once the process is finished, you are redirected to the system. This onboarding process only needs to be performed once.


You can also monitor the tenant user provisioning using the Systems Overview and Operations Dashboard apps in the Landscape Portal. Ongoing tenant user provisionings are displayed in the Requests section of the Systems Overview app. See [Systems Overview](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/4f812863a1bf4eff928951a9e14eb01b.html?locale=en-US).

