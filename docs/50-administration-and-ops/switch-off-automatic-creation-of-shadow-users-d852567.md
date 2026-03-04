<!-- loiod8525671e8b14147b96ef497e1e1af80 -->

# Switch Off Automatic Creation of Shadow Users

To switch off the creation of shadow users in the trust configuration of custom identity providers, administrators must explicitly allow users to log on. Administrators then have full control over who is allowed to log on.



## Context

Whenever a user authenticates at an application in your subaccount using any identity provider, the User Account and Authentication service always stores user-related data provided by the identity provider in the form of shadow users. The UAA uses details of the shadow users to issue tokens that refer to a certain user.

By default, the UAA allows any user of any connected identity provider to authenticate to applications in the subaccount. When there’s no corresponding shadow user, it automatically creates one based on the information received from the identity provider.

> ### Note:  
> With new subaccounts created after 24 September 2020, automatic creation of shadow users is switched off by default for the default identity provider, SAP ID service.

Usually, you want your administrators to be fully aware of which users they allow to log on. If you’ve switched off automatic creation of shadow users for a certain identity provider, you enforce that only those users can log on where shadow users have been created explicitly. You can create them in the SAP BTP cockpit, typically when you assign the first role collection to them. For more information, see [Create Users](create-users-a3bc7e8.md).

To switch off creation of shadow users during logon, proceed as follows:



## Procedure

1.  In the SAP BTP cockpit, go to your subaccount\(see [Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md)\) and choose *Security* \> *Trust Configuration*.

2.  Choose your custom trust configuration.

3.  Choose *Edit*.

4.  Go to *Create Shadow Users on User Logon* and remove the checkmark.

5.  Save your changes.

    From now on, the User Account and Authentication service doesn’t automatically create shadow users for a certain identity provider during logon.


**Related Information**  


[Deletion](../60-security/deletion-25e3cc6.md "The processing of personal data is subject to applicable laws related to the deletion of this data when the specified, explicit, and legitimate purpose for processing this personal data has expired. If there is no longer a legitimate purpose that requires the retention and use of personal data, it must be deleted.")

[Delete Users](delete-users-51000c2.md "As an administrator, you can delete users from your subaccount. When you delete a user, you also delete the user's role collection assignments.")

[Delete Shadow Users for Data Protection and Privacy Using APIs](../60-security/delete-shadow-users-for-data-protection-and-privacy-using-apis-eb70f16.md "Data privacy regulations or policies may require you to delete this data, for example, when the user has left your organization. To delete shadow users using APIs, set up access to the API and then use the SCIM REST APIs to retrieve and delete the users.")

