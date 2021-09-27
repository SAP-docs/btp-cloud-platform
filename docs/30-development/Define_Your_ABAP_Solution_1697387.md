<!-- loio1697387c02e74e66a55cf21a05678167 -->

# Define Your ABAP Solution

Follow these steps to define your ABAP Solution.



1.  Create a configuration JSON file. The configuration JSON file needs to have the following format:

    ```lang-json
    {
        "name": "abap-solution",
        "sap_system_name": "H01",
        "addon_product_name": "/NAMESPC/PRODUCTX",
        "addon_product_version": "1.2.0",
        "consumer_tenant_limit": 10	
        "size_of_runtime": 1,
        "size_of_persistence": 4,
        "tenant_mode": "multi",
        "consumer_id_pattern": "([^-]*).*",
        "provider_admin_email": " provider-admin@example.com",
        "xs-security": {
            "xsappname": "abap-saas-app"
        },
    	"usage": "test"
    }
    
    ```

    <a name="loio1697387c02e74e66a55cf21a05678167__table_n42_ypv_qmb"/>Specify the following parameters:


    <table>
    <tr>
    <th>

    Name


    
    </th>
    <th>

    Data Type


    
    </th>
    <th>

    Description


    
    </th>
    <th>

    Purpose


    
    </th>
    <th>

    Updateable


    
    </th>
    </tr>
    <tr>
    <td>

    name


    
    </td>
    <td>

    string


    
    </td>
    <td>

    Name of the solution as defined by the provider. Must be unique in the scope of the Global Account \(or globally if this information is not available\)


    
    </td>
    <td>

    Used to identify the solution and will be passed through to ABAP System \(saas\_oem plan\)


    
    </td>
    <td>

    No


    
    </td>
    </tr>
    <tr>
    <td>

    sap\_system\_name

    \(optional\)


    
    </td>
    <td>

    string


    
    </td>
    <td>

    Name of the system as defined by the provider.​ If a value is supplied, the new system\(s\) will be created with this parameter.


    
    </td>
    <td>

    Passed through ABAP System


    
    </td>
    <td>

    Yes


    
    </td>
    </tr>
    <tr>
    <td>

    addon\_product\_name

    \(optional\)


    
    </td>
    <td>

    string


    
    </td>
    <td>

    Registered name of the add-on product


    
    </td>
    <td>

    Passed through ABAP System \(saas\_oem plan\)


    
    </td>
    <td>

    No


    
    </td>
    </tr>
    <tr>
    <td>

    addon\_product\_version

    \(optional\)


    
    </td>
    <td>

    string


    
    </td>
    <td>

    Version of the add-on product to be installed


    
    </td>
    <td>

    Passed through ABAP System \(saas\_oem plan\)


    
    </td>
    <td>

    Yes \(updated value applies for new systems only\)


    
    </td>
    </tr>
    <tr>
    <td>

    consumer\_tenant\_limit

    \(optional\)


    
    </td>
    <td>

    int


    
    </td>
    <td>

    Maximum number of tenants in the multitenant ABAP system​. If the consumer tenant limit is exceeded, a new multitenant system will be created. ​

    **Note**: A recently deleted tenant will be counted towards the limit, in case it is restored during the grace period . After the 30-day grace period is up, it will no longer be considered for the limit. See [Consumer Offboarding](Consumer_Offboarding_c882a2a.md).


    
    </td>
    <td>

    Passed through ABAP System \(saas\_oem plan\)​


    
    </td>
    <td>

    Yes


    
    </td>
    </tr>
    <tr>
    <td>

    size\_of\_runtime


    
    </td>
    <td>

    int


    
    </td>
    <td>

    Default sizing for solution


    
    </td>
    <td>

    Passed through to ABAP System


    
    </td>
    <td>

    Yes \(updated value applies for new systems only\)


    
    </td>
    </tr>
    <tr>
    <td>

    size\_of\_persistence


    
    </td>
    <td>

    int


    
    </td>
    <td>

    Default sizing for solution


    
    </td>
    <td>

    Passed through to ABAP System


    
    </td>
    <td>

    Yes \(updated value applies for new systems only\)


    
    </td>
    </tr>
    <tr>
    <td>

    tenant\_mode


    
    </td>
    <td>

    enum \(string\):

    - single

    - multi


    
    </td>
    <td>

    Tenant Mode of the solution


    
    </td>
    <td>

    Decides whether a customer will have a tenant in

    - a dedicated system \(single\)

    - a shared system \(multi\)

    **single**: will trigger a system creation and a tenant onboarding

    **multi**: will trigger a system creation \(only if necessary\) and a tenant onboarding

    The parameter will be passed through to ABAP System \(saas\_oem plan\).


    
    </td>
    <td>

    No


    
    </td>
    </tr>
    <tr>
    <td>

    consumer\_id\_pattern


    
    </td>
    <td>

    string \(regex\)


    
    </td>
    <td>

    String containing a regular expression with a capturing group. The **subdomain of the consumer** is matched against this regular expression. The value of the first capturing group is used as consumer id.


    
    </td>
    <td>

    To allow the provider to group his consumer subaccounts based on an self choosen consumer identifier.

    This becomes relevant, when the provider creates the consumer subaccounts in his own provider global account and he has multiple subaccounts for one consumer \(e.g. Test & Prod\).


    
    </td>
    <td>

    No


    
    </td>
    </tr>
    <tr>
    <td>

    provider\_admin\_email


    
    </td>
    <td>

    email


    
    </td>
    <td>

    Email address of initial provider user


    
    </td>
    <td>

    Passed through to ABAP System \(saas\_oem plan\).


    
    </td>
    <td>

    Yes


    
    </td>
    </tr>
    <tr>
    <td>

    xs-security/xsappname

    \(optional\)


    
    </td>
    <td>

    string


    
    </td>
    <td>

    xsappname used for the OAuth clone during instance creation. Will be visible in the security section of SAP BTP Cockpit when assigning the initial onboarder role. Will be the "Application Name" shown in the Roles UI.

    **Default**: Service Instance GUID

    **Recommendation**: Provide the same value as defined in the xs-security.json of the XSUAA Instance of your application


    
    </td>
    <td>

    Allows providing a meaningful application name to assign the onboarding roles.


    
    </td>
    <td>

    No


    
    </td>
    </tr>
    <tr>
    <td>

    usage


    
    </td>
    <td>

    enum \(string\):

    - test

    - prod


    
    </td>
    <td>

    Specifies whether it is a test or production solution.


    
    </td>
    <td>

    Will be passed on to the Landscape Portal during the onboarding request and is used to determine the right tenant role code


    
    </td>
    <td>

    No


    
    </td>
    </tr>
    </table>
    
2.  Create an ABAP Solution instance:

    > ### Note:  
    > You need to have the space developer role assigned to you, see [Creating New Space Members and Assigning Space Developer Roles to Them](../20-getting-started/Creating_New_Space_Members_and_Assigning_Space_Developer_Roles_to_Them_967fc4e.md).

    1.  Log into your subaccount in the SAP BTP cockpit, then go into your space by navigating to *Cloud Foundry* \> *Spaces* and selecting your space.
    2.  Navigate to *Services* \> *Service Marketplace* and click on the tile *ABAP Solution*.
    3.  Go to *Instances* and click *New Instance*. Specify your parameters in JSON format and save your changes.



> ### Note:  
> **ABAP System \(saas\_oem plan\)**: This service plan is like the standard service plan of the ABAP service \(see [Create an ABAP System](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/f0163565eb554f009f990652ca41d1c6.html) \), but it is used as "backing service" for a partner-provided SaaS solution. In comparison to a standard service plan of the ABAP service, there is one main differences: An add-on product \(see [The Add-on Product](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentAddons/#the-add-on-product)\) which is installed during system provisioning can be specified.
> 
> -   Parameter: `addon_product_name`
> 
>     \(specifies which ABAP add-on to install during provisioning\)
> 
> -   Parameter: `addon_product_version`
> 
>     \(if - for testing purpose - another add-on version instead of the most recent released version shall be installed\)
> 
> 
> ABAP systems of service plan saas\_oem are provisioned by the ABAP Solution service using the destination for cloud controller access \(see [Create a Destination for the Cloud Foundry Cloud Controller Access](Create_a_Destination_for_the_Cloud_Foundry_Cloud_Controller_Access_35b5acb.md)\).

