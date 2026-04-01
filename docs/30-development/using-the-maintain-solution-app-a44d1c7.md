<!-- loioa44d1c7dcbf7460e9f4d4ac964dc841f -->

# Using the Maintain Solution App



<a name="loioa44d1c7dcbf7460e9f4d4ac964dc841f__section_ocz_zyt_4zb"/>

## Configure the solution

As a Landscape Portal administrator, you can implement the multitenant application using the*Maintain Solution*app in the Landscape Portal. Create a new solution using:

-   the previously registered product,

-   the product version that shall be installed initially \(“latest” will always install the newest available product version\),

-   the usage mode “prod”, unless you do not intend to deploy a productive application at the end,

-   the consumer tenant limit and system sizing values that you have decided on.


For more information regarding solutions, see[Create Solution](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/4441a90bb6644a02a44b2f9e25b80cc5.html).



<a name="loioa44d1c7dcbf7460e9f4d4ac964dc841f__section_jzz_jzt_4zb"/>

## Deploy the solution for test purposes

After creating the solution, it is recommended to perform a test deployment to validate the subscription process. Use the *Maintain Solution* app to create a deployment configuration for your solution:

-   Target the Provide space in the 05 Provide subaccount in your global account for development. You need to specify the corresponding CF API Endpoint, CF Organization Name and CF Space Name.

-   Choose the domain type “shared”. Since this is not a productive deployment, it is sufficient to use one of the available app domains provided by SAP.

-   Since you are deploying to a shared app domain, a unique route prefix is needed to uniquely identify your application endpoint.

-   Maintain the subdomain of the subaccount where you intend to test the subscription process.


For more information regarding deployment configurations, see[Create Deployment Configuration](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/146b71650f254d57b403ec982eea82ff.html).



<a name="loioa44d1c7dcbf7460e9f4d4ac964dc841f__section_lxb_rzt_4zb"/>

## Test the solution

You can test the multitenant application by subscribing from a consumer subaccount created in the global account for development. See [Subscribe to Multitenant Applications Using the Cockpit](https://help.sap.com/docs/btp/sap-business-technology-platform/subscribe-to-multitenant-applications-using-cockpit?version=Cloud).

Once the subscription is successful, you may also want to test the initial user onboarding process. First, assign the onboarding role collection, which includes the SolutionAdmin role, to your user. Afterwards, access the application via the consumer subaccount and trigger the user onboarding. For more details, please see the section on the productive tenant onboarding.



<a name="loioa44d1c7dcbf7460e9f4d4ac964dc841f__section_fm1_zzt_4zb"/>

## Deploy the solution for production purposes

After successfully testing the subscription process you can proceed to a productive deployment of your solution. Use the *Maintain Solution* app to create a second deployment configuration for your solution:

-   Target the Provide space in the 05 Provide subaccount in the global account for production. You need to specify the corresponding CF API Endpoint, CF Organization Name and CF Space Name.

-   Choose the domain type “custom”. It is recommended to use a custom domain for your productive application, such that consumers can access it via a recognizable URL.

-   It is recommended to use a wildcard route in conjunction with custom domains. This will route all requests towards that domain to your application.


To set up a custom domain, please follow the steps outlined in [Configuring Custom Domains](https://help.sap.com/docs/custom-domain/custom-domain-manager/configuring-custom-domains?version=Cloud) or [Get Started with the Custom Domain Manager](https://developers.sap.com/tutorials/btp-custom-domain-manager-getting-started.html). After registering the custom domain in your provider subaccount, it becomes available as a private domain \(see [Private domains](https://docs.cloudfoundry.org/devguide/deploy-apps/routes-domains.html#private-domains)\) for route creation in any of the Cloud Foundry spaces of the subaccount. Once you have created the production deployment configuration, you can trigger it using the *Deploy* action, see[Deploy Solution](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/aea1dfd5093c4a2bb107f6d20b8dfc83.html). Once deployed, your solution should appear in the service marketplace on SAP BTP Cockpit for subaccounts within your global account for production.

