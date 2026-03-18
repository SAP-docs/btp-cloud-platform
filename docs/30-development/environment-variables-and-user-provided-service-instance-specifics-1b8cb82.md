<!-- loio1b8cb822797d4007b956a3f70fb30798 -->

# Environment Variables and User-Provided Service Instance Specifics

Naming conventions and other specifics regarding the environment variables and user-provided service instances used for sensitive data handling during MTA deployment.



## Environment Variables

Sensitive values that need to be passed during deployment must be declared as local environment variables before the deployment is initialized. Their names must contain a specific prefix depending on the data type. The supported types are strings, numbers, JSON objects, and Base64-encoded certificates.


<table>
<tr>
<th valign="top">

Naming

</th>
<th valign="top">

Used For

</th>
</tr>
<tr>
<td valign="top">

`__MTA___<NAME>`

</td>
<td valign="top">

Strings

> ### Example:  
> `__MTA___secret="plainStringSecret"`



</td>
</tr>
<tr>
<td valign="top">

`__MTA_JSON___<NAME>`

</td>
<td valign="top">

-   JSON objects

    > ### Example:  
    > `__MTA_JSON___secretObj='{"secretKey":"secretValue"}'`

-   Numbers

    > ### Example:  
    > `__MTA_JSON___secretNumber=675`




</td>
</tr>
<tr>
<td valign="top">

`_MTA_CERT___<NAME>`

</td>
<td valign="top">

Certificates

</td>
</tr>
</table>

> ### Note:  
> Limitations regarding the configuration of these specialized environment variables depend on the specific shell or client environment being used. Users should check the documentation for their respective command-line interpreters to determine the correct syntax, capabilities, and limitations for setting environment variables.



## User-Provided Service Instance



### Persistent User-Provided Service Instance

When using the persistent user-provided service instance approach, you must adhere to the following format for the name of the user-provided service instance:

-   `__mta-secure-<mtaId>`
-   `__mta-secure-<mtaId>-<namespace>` \(if you are using [Namespaces](namespaces-b28fd77.md)\)

You must also insert an encryption key in the user-provided service instance that will be used to encrypt and decrypt your data. The key must be 32 characters long and can contain only alphanumeric characters, hyphens, and underscores.

> ### Example:  
> ```
>  
> cf cups __mta-secure-<mtaId> -p '{"encryptionKey": "abdfgtresghytiothewqprtimgnhdrwp"}'
> ```

For more information, see [Using a Persistent User-Provided Service Instance](using-a-persistent-user-provided-service-instance-33b5047.md).



### Disposable User-Provided Service Instance

When using the disposable user-provided service instance approach, a user-provided service instance is automatically created on your behalf. The following format is used for its name:

-   `__mta-secure-<mtaId>-<random suffix>`
-   `__mta-secure-<mtaId>-<namespace>-<random suffix>` \(if you are using [Namespaces](namespaces-b28fd77.md)\)

For more information, see [Using a Disposable User-Provided Service Instance](using-a-disposable-user-provided-service-instance-2e50c4e.md).

**Related Information**  


[Sensitive Data Handling During MTA Deployment](sensitive-data-handling-during-mta-deployment-4c40fda.md "Securely manage credentials and other sensitive values during MTA deployment.")

[Using a Persistent User-Provided Service Instance](using-a-persistent-user-provided-service-instance-33b5047.md "Pass sensitive values during MTA deployment by creating or using a persistent user-provided service instance.")

[Using a Disposable User-Provided Service Instance](using-a-disposable-user-provided-service-instance-2e50c4e.md "Pass sensitive values during MTA deployment by using a disposable user-provided service instance.")

