<!-- loio13ce7bb497dc4ce3b92048e6149ae4c5 -->

# Access Is Denied or Forbidden



## Symptom

After sending a request to a web application in the SAP BTP, Cloud Foundry environment, you get a response containing a nested error element with the value access\_denied and an error\_description element.

The system responds with Access is denied.

The system might also respond with the single word Forbidden.

> ### Output Code:  
> ```
> <oauth>
>   <error_description>Access is denied</error_description>
>   <error>Access denied</error>
> </oauth>
> ```



## Reason and Prerequisites

A business user has tried to access the URL endpoint of a web application but is not authorized to do this. The authorizations \(scopes\) required for the URL endpoint must be assigned to this business user. Scopes \(functional authorizations\) allow the business user to perform operations provided by the web application. Attributes \(instance-based authorizations\) specify the data, for example, company code or cost center, which the business user is authorized to use. In this way, business users can perform the operations they are authorized for.



## Solution

A role collection with the role that contains the required authorizations must be available. Assign this role collection to the business user.

If there are neither instance-based authorizations nor roles containing the required attribute values, create a role based on the corresponding role template. Maintain the attribute values of the new role to define the required data authorizations.

> ### Note:  
> -   Role templates are predefined and deployed together with the web application. Role templates specify the scopes \(functional operations\) that the web application supports. You cannot change existing role templates or create new ones.
> -   After a role collection has been assigned, you might need to clear the cache and cookies and log on to the application again for the changes to take effect.

For more information about roles and role collections, see [Building Roles and Role Collections for Applications](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/eaa6a26291914b348e875a00b6beb729.html?version=Cloud).

