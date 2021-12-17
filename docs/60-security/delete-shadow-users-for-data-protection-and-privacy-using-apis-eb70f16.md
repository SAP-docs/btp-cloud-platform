<!-- loioeb70f16b420447b6b33dedc3ebcf91cc -->

# Delete Shadow Users for Data Protection and Privacy Using APIs

Data privacy regulations or policies may require you to delete this data, for example, when the user has left your organization. To delete shadow users using APIs, set up access to the API and then use the SCIM REST APIs to retrieve and delete the users.



<a name="loioeb70f16b420447b6b33dedc3ebcf91cc__prereq_sg2_kqr_ddb"/>

## Prerequisites

The security administrator must have the following scopes:

-   `xs_user.read`

-   `xs_user.write`




## Context

> ### Note:  
> When handling personal data, consider the legislation in the various countries and regions where your organization operates. After the data has passed the end of purpose, regulations might require you to delete the data. For more information on data protection and privacy, see the related link.

The User Account and Authentication service stores user-related data records in the form of shadow users. The UAA uses the information of the shadow users to issue tokens that refer to the specific user. If automatic shadow user creation is enabled, the UAA creates the shadow users when the user authenticates. Otherwise, the UAA creates the shadow user as soon as you assign the user a role collection. These conditions apply to platform users and business users. For more information about shadow users, see the Cloud Foundry documentation.

> ### Note:  
> Administrators can also delete users using the SAP BTP cockpit. For more information, see [Delete Users](../50-administration-and-ops/delete-users-51000c2.md).



## Procedure

1.  Enable API access to your subaccount.

    For more information, see [Access UAA Admin APIs](../50-administration-and-ops/access-uaa-admin-apis-ebc9113.md).

2.  Use the *GET* method for the User Management \(SCIM\) API of the SAP Authorization and Trust Management service to get a list of users.

    For more information about the User Management \(SCIM\) API, see [https://api.sap.com/package/authtrustmgmnt](https://api.sap.com/package/authtrustmgmnt) on *SAP API Business Hub*.

    The API returns the list of users in JSON format.

3.  Use your own tools to sort and identify the users in the JSON response to delete.

    > ### Recommendation:  
    > Users, who have left your organization, haven't logged on recently. Use the `lastLogonTime` parameter to find users who haven't logged on in the last 180 days. The `lastLogonTime` parameter is in UNIX time.
    > 
    > The last logon time you filter for varies from situation to situation. The filter value must meet the following requirements:
    > 
    > -   Be long enough that the filter doesn't catch users who are simply on vacation or don't work regularly in the system.
    > 
    > -   Not be so long that the filter no longer meets your data protection and privacy requirements.
    > 
    > 
    > Account for users on parental leave or on a longer leave of absence, too.

    > ### Caution:  
    > You can't undo the deletion of a user. When you delete a user, you delete any direct assignments of role collections to that user. You also potentially invalidate any application referencing that user.
    > 
    > For example, an application saves some data relating to a user. When you delete the user, that data points to an ID that no longer exists. You can recreate the user, but the new user has a different ID, even though other attributes, such as e-mail, first name, and last name, are identical.

4.  Use the *DELETE* method and the list of user IDs to delete the shadow users one at a time.

    For each user, call the `Users` endpoint with the delete method and include the user ID in the path. For example:

    ```
    curl --location --request DELETE 'https://api.authentication.eu20.hana.ondemand.com/Users/a0a67e6f-c4b5-41e5-b871-6fa181d46599' \
    --header 'Content-Type: application/x-www-form-urlencoded' \
    --header 'Accept: application/json' \
    --header 'Authorization: bearer eyJqdGkiOiJmZmZl…'
    ```

    For more information about the User Management \(SCIM\) API, see [https://api.sap.com/package/authtrustmgmnt](https://api.sap.com/package/authtrustmgmnt) on *SAP API Business Hub*.


**Related Information**  


[Data Protection and Privacy](data-protection-and-privacy-7e513d3.md "Data protection is associated with numerous legal requirements and privacy concerns. In addition to compliance with general data protection and privacy acts, it is necessary to consider compliance with industry-specific legislation in different countries.")

[https://docs.cloudfoundry.org/uaa/uaa-concepts.html\#%23shadow](https://docs.cloudfoundry.org/uaa/uaa-concepts.html#%23shadow)

[Switch Off Automatic Creation of Shadow Users](../50-administration-and-ops/switch-off-automatic-creation-of-shadow-users-d852567.md "To switch off the creation of shadow users in the trust configuration of custom identity providers, administrators must explicitly allow users to log on. Administrators then have full control over who is allowed to log on.")

[Delete Shadow Users for Data Protection and Privacy Using the Cockpit](delete-shadow-users-for-data-protection-and-privacy-using-the-cockpit-893c5ac.md "Data privacy regulations or policies may require you to delete this data, for example, when the user has left your organization. SAP BTP cockpit offers an application to select and delete shadow users.")

