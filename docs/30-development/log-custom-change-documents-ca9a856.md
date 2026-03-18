<!-- loioca9a856a93ce41ec893a305df2b3fbf3 -->

# Log Custom Change Documents

Change documents defined in custom RAP business objects are automatically logged as business events when the corresponding business is activated for logging in the Activate Business Event Logging configuration.

For information on defining change documents for a managed RAP business object as a customer, see [Enabling Change Documents Integration](https://help.sap.com/docs/abap-cloud/abap-rap/enabling-rap-change-documents-integration).

> ### Note:  
> For partners who implement the same scenario under a partner namespace, change documents can be logged as business events only if the event binding version is C2 released.



## Reset Shared Memory

Any new RAP object or changed object will be considered for logging only when the shared memory \(metadata buffer\) is reset. Business Event Logging resets the memory once everyday to ensure that the new or changed objects are considered for logging within the framework.

