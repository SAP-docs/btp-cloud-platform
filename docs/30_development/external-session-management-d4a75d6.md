<!-- loiod4a75d6e970844cb94fcdd1d0747b568 -->

# External Session Management

The application router supports the backup of user sessions in an external session store. This enables a session recovery if the application router instance that stores a session crashes and another application router instance needs to continue handling the running user session.

To enable this capability the you must bind a service instance of a service that supports a fast persistence store such as Redis. When such a service is bound, the application router backs up the in memory session information into the external persistency store. If, in subsequent requests, the session information is not found in the in memory session store, the application router tries to rebuild the in memory session store session information from external persistency store.

The sessions are stored encrypted and compressed. For capacity planning, you can assume 50 Kb per session storage in fast persistence store.



<a name="loiod4a75d6e970844cb94fcdd1d0747b568__section_ztg_cgt_qpb"/>

## Configuration of External Session Management

To use external session management, you have to the `EXT_SESSION_MGT` environment variable. The variable value is defined in JSON format, providing the following properties:

-   `instanceName` \(mandatory\): the name of the service instance of the storage service

-   `storageType` \(mandatory\): the type of the storage, for example - "redis".

    Note that if no custom storage driver is used, only `redis` is allowed.

-   `sessionSecret` \(mandatory\): Since the application router stores encrypted sessions in a persistence store, a shared secret shall be provided. Please generate a unique string with at least 64 characters.


For example:

> ### Sample Code:  
> ```
> {
>     "instanceName": "approuter-redis",
>     "storageType": "redis",
>     "sessionSecret": "someuniquesessionsecret"
> }
> 
> ```

> ### Note:  
> Currently, the application router supports only a Redis store.



<a name="loiod4a75d6e970844cb94fcdd1d0747b568__section_unp_cgt_qpb"/>

## Configuration of a Custom Storage Driver

You can use your own driver. In order to do that, the user injects its own implementation of a store.

The class has to implement the following interface:

> ### Sample Code:  
> ```
> interface UserCustomStore {
> 
>   // delete all sessions
>   clear(): Promise<void>;
> 
>   // remove <sessionId> session
>   destroy(sessionId : string): Promise<void>; 
> 
>   // retrieve <sessionId> session
>   get(sessionId : string): Promise<object | null>;
> 
>   // number of sessions
>   length(): Promise<number>;
> 
>   // get <sessionId> expiration
>   ttl(sessionId : string): Promise<number>;
> 
>   // set <sessionId> data to <session> with <timeout> expiration
>   set(sessionId: string, session: object, timeout: number): Promise<void>;
> 
>   // check if session <sessionId> exists
>   exists(sessionId: string): boolean; 
> 
>   // update existing session <sessionId> expiration to <timeout>
>   resetTimer(sessionId: string, timeout: number); 
> }  
> 
> ```

In addition, the file must include a method to get an instance of the store, for example:

> ### Sample Code:  
> ```
> let store;
> module.exports.getStore = () => {
>   if (!store) {
>     store = new UserCustomStore();
>   }
>   return store;
> };
> 
> ```

In order for application router to use it, user has to set the `externalStoreFilePath` property in the `EXT_SESSION_MGT` environment variable with the path to the storage. The application router uses this path to require your storage For example:

> ### Sample Code:  
> ```
> {
>     "instanceName": "approuter-redis",
>     "storageType": "redis",
>     "sessionSecret": "someuniquesessionsecret",
>     "externalStoreFilePath": "./src/storage/my-special-storage"
> }
> 
> 
> ```

**Related Information**  


[Environment Variables](environment-variables-ba52705.md "A list of environment variables that can be used to configure the application router.")

